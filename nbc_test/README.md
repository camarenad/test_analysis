# Summary

## Visits and Searches

- I implemented a decomposable time series model developed by facebook that is accurate and intuitive.
This model works well with time series because it allows control over various kinds of seasonality and trends in the data. 

- After modeling the data we can see that on October-15 we can expect to receive approximately 18-20k views on our website. 

#### Margin of error
![Margin of Error](images/error.png)

![Predictions](images/prediction1.png)

### Visits and Searches

- We observe some correlation between searches and web traffic

![pairplot](images/searches.png)

## Email Open Rate
- The data suggests that the first email has an open rate of 80% while the second email has a lower open rate of 45%.  The overall open rate for all emails is around 50%.  This means that email one performed above average while email two fell short.

![open_rate](images/open_rate_barh.png)

### All Emails
- When we average our data our combined open rate for emails A,B,C,D
is 25%. 

![open_rate_all](images/open_combined.png)

## SQL
- Find those customers who bought hats (value "Hat") in 2016. Also include total quantity of hats per customer:
```
 SELECT
 custid as cid, 
 custname as cname, 
 SUM(qty) AS total_hats
 FROM 
 OrderDetail
 WHERE 
 CAST(xdate AS DATE) BETWEEN  '2016/01/01' AND '2016/12/31'
 AND
 productname = 'Hat'
 GROUP BY(cid, cname)
 ```



- Find those customers who bought only hats (value "Hat") in 2016. Also include total quantity of hats per customer

 ```
 SELECT 
 custname
 FROM 
 OrderDetail
 WHERE 
 productname = 'Hat'
 EXCEPT
 SELECT
 custname 
 FROM 
 OrderDetail
 WHERE CAST(xdate AS DATE) BETWEEN '2016/01/01' AND '2016/12/31'
 AND productname <> 'Hat'
  
 ```


