# DataEngineering-Bootcamp
To follow up DE camp
Week 1's HomeWork
Answer 1. 
1.docker run -it --entrypoint bash python:3.12.8 //Run docker image in bash with python:3.12.8 version
2.pip --version  //to check pip version of that image =>24.3.1

Answer 2.For pgadmin to connect pg we can see at service db and port 5432.Becuase 5433 is port of local machine.

Answer 3.
SELECT
  COUNT(*) AS total_trips,
  SUM(CASE WHEN trip_distance <= 1 THEN 1 ELSE 0 END) AS up_to_1_mile,
  SUM(CASE WHEN trip_distance > 1 AND trip_distance <= 3 THEN 1 ELSE 0 END) AS between_1_and_3_miles,
  SUM(CASE WHEN trip_distance > 3 AND trip_distance <= 7 THEN 1 ELSE 0 END) AS between_3_and_7_miles,
  SUM(CASE WHEN trip_distance > 7 AND trip_distance <= 10 THEN 1 ELSE 0 END) AS between_7_and_10_miles,
  SUM(CASE WHEN trip_distance > 10 THEN 1 ELSE 0 END) AS over_10_miles
FROM
   green_tripdata
WHERE
  lpep_pickup_datetime >= '2019-10-01' AND lpep_pickup_datetime < '2019-11-01'
  AND lpep_dropoff_datetime >= '2019-10-01' AND lpep_dropoff_datetime < '2019-11-01';

Answer 4.
SELECT lpep_pickup_datetime,MAX(trip_distance)
FROM green_tripdata
GROUP BY lpep_pickup_datetime
ORDER BY MAX(trip_distance) DESC;

Answer 5.
SELECT "Zone" 
FROM zones as z
INNER JOIN green_tripdata as gt
on "LocationID" ="PULocationID"
WHERE lpep_pickup_datetime='2019-10-18' AND
total_amount > 13000
ORDER BY total_amount DESC
limit 3;

Anser 6.
SELECT
  "Zone"  AS dropoff_zone,
  MAX(t.tip_amount) AS largest_tip
FROM
  green_tripdata as t
INNER JOIN zones as z
on "DOLocationID" ="LocationID"
WHERE "Zone" IN (
SELECT "Zone" as pickup_zone
FROM zones
WHERE "Zone"='East Harlem North'
) AND lpep_pickup_datetime >= '2019-10-01' AND lpep_pickup_datetime <='2019-10-31'
GROUP BY "Zone"
LIMIT 1;

