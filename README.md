# Surfs Up Challenge
## Overview of the statistical analysis  
Client W. Avy has requested an analysis of temperature data for the months of June and December in Oahu.  This background data is critical to making informed decisions regarding the suitability of the surf and ice cream shop business proposal.  Data analyzed consisted of observations over the course of several years at various weather stations, limited to June and December records.

## Results
### June Stats  
![june](https://user-images.githubusercontent.com/88070999/136680870-31b23884-13fe-4694-8c75-bd9c217583bf.png)

### December Stats  
![december](https://user-images.githubusercontent.com/88070999/136680874-5edf65e4-111f-4d3b-820e-791000e43aea.png)

### Observations  
* Both months have quite a few temperature observations, making comparisons between the months much more accurate due to the large sample sizes.
* The mean temperatures between the two months are only four degrees difference (71 in Dec and 75 in June). This is not a significant difference between the two months.
* Temperatures vary slightly more in December with a standard deviation of 3.7 vs 3.3 in June. This means that the temperature is not quite as steady in December as in June.
* Though the maximum temperatures are very similar (83 in Dec vs. 85 in June), the minimum temperatures are quite a bit more different.  In December the lowest record is for 56 degrees, a full 8 degrees cooler than the coldest temperature in June.

## Summary

Overall, the two months are remarkably similar with similar high temperatures and somewhat similar means.  The average day in either month is over 70 degrees, which is warm enough to support an ice cream and surf shop, and both months have the potential to get significantly warmer (especially in December, though technically "winter").

There are other factors to consider as well, including precipitation.  In December:  
![dec-prcp](https://user-images.githubusercontent.com/88070999/136681446-d0cea873-0449-4360-9c68-e214366b22be.png)  
Code to generate:
```
decprcp = []
decprcp = session.query(Measurement.prcp).filter(extract('month', Measurement.date) == 12).all()
dec_prcp_df = pd.DataFrame(decprcp, columns=['December Precipitation'])
dec_prcp_df.describe()
```

In June:  
![jun-prcp](https://user-images.githubusercontent.com/88070999/136681434-e7ba1414-609d-4199-bc69-0c139aa27f73.png)  
Code to generate:  
```
junprcp = []
junprcp = session.query(Measurement.prcp).filter(extract('month', Measurement.date) == 6).all()
jun_prcp_df = pd.DataFrame(junprcp, columns=['June Precipitation'])
jun_prcp_df.describe()
```

The data above shows that there is more precipitation on average in December, though the 50th percentile of days barely registers any precipitation.  In other words, both months have quite a few days of no precipitation, further lending support to a decision to build a surf and ice cream shop.
