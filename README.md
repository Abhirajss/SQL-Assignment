1) Popular starting  and ending station
```SQL
SELECT start_station_name, COUNT(*) AS trip_count
FROM `bigquery-public-data.new_york_citibike.citibike_trips`
GROUP BY start_station_name
ORDER BY trip_count DESC
LIMIT 10;

SELECT end_station_name, COUNT(*) AS trip_count
            FROM `bigquery-public-data.new_york_citibike.citibike_trips`
            GROUP BY end_station_name
            ORDER BY trip_count DESC
             LIMIT 10;
   ```
![image](https://github.com/Abhirajss/SQL-Assignment/assets/154316712/80ec9c94-4cc9-403d-a35f-eae470ac1d3d)

2)	Classification based on gender, age and number of trips
```SQL
SELECT gender, EXTRACT(YEAR FROM starttime) - birth_year AS age_group, COUNT(*) AS trip_count
FROM `bigquery-public-data.new_york_citibike.citibike_trips`
WHERE gender IS NOT NULL AND birth_year IS NOT NULL
GROUP BY gender, age_group;
```
![image](https://github.com/Abhirajss/SQL-Assignment/assets/154316712/d6fc9b09-eb84-4269-8b61-34101b97a0b0)

3)	Total collisions by borough
```SQL
SELECT borough, COUNT(*) AS num_collisions
FROM `bigquery-public-data.new_york_mv_collisions.nypd_mv_collisions`
GROUP BY borough
ORDER BY num_collisions DESC
```
![image](https://github.com/Abhirajss/SQL-Assignment/assets/154316712/9602e99b-dd88-4447-8add-c6167e902db3)

4)	Collisions with fatalities or injuries
```SQL
SELECT COUNT(*) AS num_collisions
FROM `bigquery-public-data.new_york_mv_collisions.nypd_mv_collisions`
WHERE number_of_persons_injured > 0 OR number_of_persons_killed > 0
```
![image](https://github.com/Abhirajss/SQL-Assignment/assets/154316712/9168ec06-0cad-4802-bb19-b7611ed290af)

5)	Most Contributing factors for collision
```SQL
SELECT contributing_factor_vehicle_1, COUNT(*) AS num_collisions
FROM `bigquery-public-data.new_york_mv_collisions.nypd_mv_collisions`
GROUP BY contributing_factor_vehicle_1
ORDER BY num_collisions DESC
LIMIT 10
```
![image](https://github.com/Abhirajss/SQL-Assignment/assets/154316712/c662e2f0-7106-4b08-bb30-e5a1cd9bd7dd)

6)	Collisions based on type of vehicle
```SQL
SELECT vehicle_type_code1, COUNT(*) AS num_collisions
FROM `bigquery-public-data.new_york_mv_collisions.nypd_mv_collisions`
GROUP BY vehicle_type_code1
ORDER BY num_collisions DESC
```
![image](https://github.com/Abhirajss/SQL-Assignment/assets/154316712/e27091f0-304b-449a-882b-5d814cbcaae3)

7)	Collision hotspots
```SQL
SELECT latitude, longitude, COUNT(*) AS num_collisions
FROM `bigquery-public-data.new_york_mv_collisions.nypd_mv_collisions`
GROUP BY latitude, longitude
ORDER BY num_collisions DESC
LIMIT 10
```
![image](https://github.com/Abhirajss/SQL-Assignment/assets/154316712/63ec1217-f859-4526-9413-ba8477e661bf)

8)	Collisions with pedestrians
```SQL
SELECT COUNT(*) as num_pedestrian_collisions
FROM `bigquery-public-data.new_york_mv_collisions.nypd_mv_collisions`
WHERE number_of_pedestrians_injured > 0 OR number_of_pedestrians_killed > 0
```
![image](https://github.com/Abhirajss/SQL-Assignment/assets/154316712/814aad74-2242-4e12-a49b-422f67b4e2d6)

9)	Average fertility rate by country 
```SQL
SELECT cn.country_name, AVG(afr.total_fertility_rate) AS avg_fertility_rate
FROM `bigquery-public-data.census_bureau_international.age_specific_fertility_rates` afr
JOIN `bigquery-public-data.census_bureau_international.country_names_area` cn
ON afr.country_code = cn.country_code
GROUP BY cn.country_name;
```
![image](https://github.com/Abhirajss/SQL-Assignment/assets/154316712/58a63c07-bfb6-469e-a1c6-2e1c4601524c)

10)	Changes in Bank branch offices with Time
```SQL
SELECT
locations.institution_name
locations,
locations.state_name,
established_date,
end_effective_date,
FROM
`bigquery-public-data.fdic_banks.locations` AS locations
JOIN
`bigquery-public-data.fdic_banks.institutions` AS institutions
ON
 locations.fdic_certificate_number = institutions.fdic_certificate_number
 WHERE
 established_date IS NOT null
 ORDER BY
 institutions.institution_name,
 established_date DESC;
```
![image](https://github.com/Abhirajss/SQL-Assignment/assets/154316712/7566f9b0-5c15-4ce6-a0d2-d7fdbf239f17)





