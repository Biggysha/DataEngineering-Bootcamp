# DataEngineering-Bootcamp
To follow up DE camp
Week 1's HomeWork
Answer 1. 
1.docker run -it --entrypoint bash python:3.12.8 //Run docker image in bash with python:3.12.8 version
2.pip --version  //to check pip version of that image =>24.3.1

Answer 2.For pgadmin to connect pg we can see at service db and port 5432.Becuase 5433 is port of local machine.

Answer 3.

Answer 4.It shows 2019-10-31
SELECT lpep_pickup_datetime,MAX(trip_distance)
FROM green_tripdata
GROUP BY lpep_pickup_datetime
ORDER BY MAX(trip_distance) DESC;

