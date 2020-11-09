# Query across the data with Athena

## Amazon Athena query visualization

* Return to Amazon Athena on the AWS Console
* On the Query editor:
 * Data source: **AwsDataCatalog**
 * Database: **nycitytaxianalysis**
 * Try this query:
 
```SQL 
SELECT min(trip_distance) as minDistance,
         max(trip_distance) as maxDistance,
         min(total_amount) as minTotal,
         max(total_amount) as maxTotal
FROM "nycitytaxianalysis"."canonicaldata01"
```

 * You can see some outliers in the total amount and distances that are = 0.  In the next query, don’t include those when calculating things like average cost per mile:

```SQL
SELECT type,
         avg(trip_distance) AS avgDist,
         avg(total_amount/trip_distance) AS avgCostPerMile
FROM "nycitytaxianalysis"."canonicaldata01"
WHERE trip_distance > 0
        AND total_amount > 0
GROUP BY  type
```

 * Interesting note: you aren’t seeing FHV broken out yet, because that dataset didn’t have a mapping to these fields. Here’s a query that’s a little more complicated, to calculate a 99th percentile:

```SQL
SELECT TYPE, 
       avg(trip_distance) avgDistance, 
       avg(total_amount/trip_distance) avgCostPerMile, 
       avg(total_amount) avgCost,
       approx_percentile(total_amount, .99) percentile99
FROM "nycitytaxianalysis"."canonicaldata01"
WHERE trip_distance > 0 and total_amount > 0
GROUP BY TYPE
```

 * Now lets move and see more data thru Amazon QuickSight














