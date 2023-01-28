## Question 1:  Knowing docker tags  ( Multiple choice)
Which tag has the following text? - Write the image ID to the file

**Answer**: 
> docker build --help | grep "Write the image"

## Question 2:  Understanding docker first run  (Multiple choice)
How many python packages/modules are installed?

**Answer**:
> pip list

## Question 3: Count records  (Multiple choice)
How many taxi trips were totally made on January 15?

**Answer**:
```sql
SELECT count(*) 
FROM green_taxi_trips 
WHERE lpep_pickup_datetime BETWEEN '2019-01-15 00:00:00' AND '2019-01-15 23:59:59' AND lpep_dropoff_datetime BETWEEN '2019-01-15 00:00:00' AND '2019-01-15 23:59:59'
```

## Question 4: Largest trip for each day (Multiple choice)
Which was the day with the largest trip distance?

**Answer**:
```sql
SELECT lpep_pickup_datetime 
FROM green_taxi_trips 
ORDER BY trip_distance DESC
LIMIT 1
```
## Question 5: The number of passengers  (Multiple choice)
In 2019-01-01 how many trips had 2 and 3 passengers?

**Answer**:
```sql
SELECT passenger_count, count(*) FROM green_taxi_trips 
WHERE lpep_pickup_datetime BETWEEN '2019-01-01 00:00:00' AND '2019-01-01 23:59:59'
AND passenger_count IN (2,3)
GROUP BY passenger_count
```

## Question 6: Largest tip (Multiple choice)
For the passengers picked up in the Astoria Zone which was the drop up zone that had the largest tip?

**Answer**:
```sql
SELECT d.Zone 
FROM green_taxi_trips AS t
INNER JOIN 
	zone_lookup AS pu ON pu.LocationID = t.PULocationID 
		AND pu.zone = 'Astoria'
INNER JOIN zone_lookup AS d ON d.LocationID = t.DOLocationID
ORDER BY t.tip_amount DESC
LIMIT 1
```
