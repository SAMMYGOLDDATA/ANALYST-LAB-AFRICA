SELECT *
FROM [netflix_titles yh]

SELECT COUNT(*) AS total_rows
FROM [netflix_titles yh]

SELECT COUNT(*)
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME = 'netflix_titles';

SELECT COLUMN_NAME,
       DATA_TYPE
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME = 'netflix_titles';

SELECT COLUMN_NAME
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME='netflix_titles'
AND DATA_TYPE IN ('int','bigint','decimal','numeric','float','double');

SELECT COLUMN_NAME
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME='netflix_titles'
AND DATA_TYPE IN ('varchar','text','char');

SELECT show_id,
COUNT(*) AS occurrences
FROM netflix_titles
GROUP BY show_id
HAVING COUNT(*)>1;

SELECT
SUM(CASE WHEN show_id IS NULL THEN 1 ELSE 0 END) AS show_id,
SUM(CASE WHEN Type IS NULL THEN 1 ELSE 0 END) AS type,
SUM(CASE WHEN title IS NULL THEN 1 ELSE 0 END) AS title,
SUM(CASE WHEN director IS NULL THEN 1 ELSE 0 END) AS director,
SUM(CASE WHEN country IS NULL THEN 1 ELSE 0 END) AS country,
SUM(CASE WHEN date_added IS NULL THEN 1 ELSE 0 END) AS date_added,
SUM(CASE WHEN release_year IS NULL THEN 1 ELSE 0 END) AS release_year,
SUM(CASE WHEN rating IS NULL THEN 1 ELSE 0 END) AS rating,
SUM(CASE WHEN duration IS NULL THEN 1 ELSE 0 END) AS duration,
SUM(CASE WHEN listed_in IS NULL THEN 1 ELSE 0 END) AS listed_in,
SUM(CASE WHEN Description IS NULL THEN 1 ELSE 0 END) AS description
FROM [netflix_titles yh]

UPDATE netflix_titles
SET director='Unknown'
WHERE director IS NULL;

UPDATE netflix_titles
SET country='Unknown'
WHERE country IS NULL;

UPDATE netflix_titles
SET rating='Not Rated'
WHERE rating IS NULL;

DELETE FROM netflix_titles
WHERE date_added IS NULL;

SELECT *,
COUNT(*) AS duplicate_count
FROM [netflix_titles yh]
GROUP BY show_id
HAVING COUNT(*)>1;

SELECT COUNT(*)-COUNT(DISTINCT show_id)
AS duplicates
FROM [netflix_titles yh]

UPDATE [netflix_titles yh]
SET title = TRIM(title);

UPDATE [netflix_titles yh]
SET director=TRIM(director),
country=TRIM(country),
rating=TRIM(rating);


SELECT *
FROM [netflix_titles yh]
WHERE duration IS NULL;

SELECT *
FROM [netflix_titles yh]
WHERE release_year>YEAR(GETDATE());

SELECT DISTINCT rating
FROM [netflix_titles yh]

SELECT
AVG(release_year) AS average_year,
MIN(release_year) AS minimum,
MAX(release_year) AS maximum,
STDEV(release_year) AS std_dev
FROM [netflix_titles yh]

SELECT AVG(release_year) AS median
FROM (
SELECT release_year,
ROW_NUMBER() OVER(ORDER BY release_year) rn,
COUNT(*) OVER() total
FROM [netflix_titles yh]
)t
WHERE rn IN ((total+1)/2,(total+2)/2);

SELECT type,
COUNT(*) AS total
FROM [netflix_titles yh]
GROUP BY type;

SELECT TOP 10 country,
COUNT(*) AS total_titles
FROM [netflix_titles yh]
GROUP BY country
ORDER BY total_titles DESC

SELECT YEAR(date_added) AS year_added,
COUNT(*) AS total
FROM [netflix_titles yh]
GROUP BY YEAR(date_added)
ORDER BY year_added;

SELECT rating,
COUNT(*) AS total
FROM [netflix_titles yh]
GROUP BY rating
ORDER BY total DESC;

SELECT TOP 10 listed_in,
COUNT(*) AS total
FROM [netflix_titles yh]
GROUP BY listed_in
ORDER BY total DESC

SELECT TOP 10 title,
release_year
FROM [netflix_titles yh]
ORDER BY release_year

SELECT TOP 10 title,
release_year
FROM [netflix_titles yh]
ORDER BY release_year DESC

SELECT TOP 10 director,
COUNT(*) AS total_titles
FROM [netflix_titles yh]
WHERE director<>'Unknown'
GROUP BY director
ORDER BY total_titles DESC

SELECT release_year,
COUNT(*) AS total_movies
FROM [netflix_titles yh]
WHERE type='Movie'
GROUP BY release_year
ORDER BY release_year;

SELECT release_year,
COUNT(*) AS total_shows
FROM [netflix_titles yh]
WHERE type='TV Show'
GROUP BY release_year
ORDER BY release_year;

SELECT country,
COUNT(*) AS total_titles,
RANK() OVER(ORDER BY COUNT(*) DESC) AS ranking
FROM [netflix_titles yh]
GROUP BY country;

SELECT
    YEAR(date_added) AS Year_Added,
    COUNT(*) AS Total_Content
FROM [netflix_titles yh]
WHERE date_added IS NOT NULL
GROUP BY YEAR(date_added)
ORDER BY Year_Added;

SELECT TOP 10
    country,
    COUNT(*) AS Total_Content
FROM [netflix_titles yh]
WHERE country IS NOT NULL
GROUP BY country
ORDER BY Total_Content DESC;

SELECT
    rating,
    COUNT(*) AS Total_Content
FROM [netflix_titles yh]
GROUP BY rating
ORDER BY Total_Content DESC;

SELECT TOP 10
    listed_in,
    COUNT(*) AS Total_Content
FROM [netflix_titles yh]
GROUP BY listed_in
ORDER BY Total_Content DESC;
