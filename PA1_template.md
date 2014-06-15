# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data


```r
activity <-read.csv("activity.csv", colClasses=c("integer", "Date", "integer"))

#activity <- activity[!is.na(activity$steps),]
```


## What is mean total number of steps taken per day?

The following figure shows the total number of steps per day

```r
totalStepsPerDay <- aggregate(steps ~ date, data = activity,
          FUN = sum) 

barplot(totalStepsPerDay$steps, ylab="Total number of steps per day", xlab="date", space=1)

text(seq(1.5,2*length(totalStepsPerDay$date),by=2), par("usr")[3], 
     srt = 60, adj= 1, xpd = TRUE,
     labels = totalStepsPerDay$date, cex=0.7)
```

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2.png) 

The average number of steps per day is:

```r
averageStepsPerDay <- aggregate(steps ~ date, data = activity,
          FUN = mean) 

kable(averageStepsPerDay, format = "html", table.attr = "width=\"200\"")
```

<table width="200">
 <thead>
  <tr>
   <th align="left"> date </th>
   <th align="right"> steps </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td align="left"> 2012-10-02 </td>
   <td align="right"> 0.4375 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-03 </td>
   <td align="right"> 39.4167 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-04 </td>
   <td align="right"> 42.0694 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-05 </td>
   <td align="right"> 46.1597 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-06 </td>
   <td align="right"> 53.5417 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-07 </td>
   <td align="right"> 38.2465 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-09 </td>
   <td align="right"> 44.4826 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-10 </td>
   <td align="right"> 34.3750 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-11 </td>
   <td align="right"> 35.7778 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-12 </td>
   <td align="right"> 60.3542 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-13 </td>
   <td align="right"> 43.1458 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-14 </td>
   <td align="right"> 52.4236 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-15 </td>
   <td align="right"> 35.2049 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-16 </td>
   <td align="right"> 52.3750 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-17 </td>
   <td align="right"> 46.7083 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-18 </td>
   <td align="right"> 34.9167 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-19 </td>
   <td align="right"> 41.0729 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-20 </td>
   <td align="right"> 36.0938 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-21 </td>
   <td align="right"> 30.6285 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-22 </td>
   <td align="right"> 46.7361 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-23 </td>
   <td align="right"> 30.9653 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-24 </td>
   <td align="right"> 29.0104 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-25 </td>
   <td align="right"> 8.6528 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-26 </td>
   <td align="right"> 23.5347 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-27 </td>
   <td align="right"> 35.1354 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-28 </td>
   <td align="right"> 39.7847 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-29 </td>
   <td align="right"> 17.4236 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-30 </td>
   <td align="right"> 34.0938 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-31 </td>
   <td align="right"> 53.5208 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-02 </td>
   <td align="right"> 36.8056 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-03 </td>
   <td align="right"> 36.7049 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-05 </td>
   <td align="right"> 36.2465 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-06 </td>
   <td align="right"> 28.9375 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-07 </td>
   <td align="right"> 44.7326 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-08 </td>
   <td align="right"> 11.1771 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-11 </td>
   <td align="right"> 43.7778 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-12 </td>
   <td align="right"> 37.3785 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-13 </td>
   <td align="right"> 25.4722 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-15 </td>
   <td align="right"> 0.1424 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-16 </td>
   <td align="right"> 18.8924 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-17 </td>
   <td align="right"> 49.7882 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-18 </td>
   <td align="right"> 52.4653 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-19 </td>
   <td align="right"> 30.6979 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-20 </td>
   <td align="right"> 15.5278 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-21 </td>
   <td align="right"> 44.3993 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-22 </td>
   <td align="right"> 70.9271 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-23 </td>
   <td align="right"> 73.5903 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-24 </td>
   <td align="right"> 50.2708 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-25 </td>
   <td align="right"> 41.0903 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-26 </td>
   <td align="right"> 38.7569 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-27 </td>
   <td align="right"> 47.3819 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-28 </td>
   <td align="right"> 35.3576 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-29 </td>
   <td align="right"> 24.4688 </td>
  </tr>
</tbody>
</table>

To ease readability we have shown the average steps per data as a plot below

```r
library(ggplot2)
qplot(averageStepsPerDay$date, averageStepsPerDay$steps, geom="line")
```

![plot of chunk unnamed-chunk-4](figure/unnamed-chunk-4.png) 

Median number of steps per day

```r
medianStepsPerDay <- aggregate(steps ~ date, data = activity,
          FUN = median) 

kable(medianStepsPerDay, format = "html", table.attr = "width=\"200\"")
```

<table width="200">
 <thead>
  <tr>
   <th align="left"> date </th>
   <th align="right"> steps </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td align="left"> 2012-10-02 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-03 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-04 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-05 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-06 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-07 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-09 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-10 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-11 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-12 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-13 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-14 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-15 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-16 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-17 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-18 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-19 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-20 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-21 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-22 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-23 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-24 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-25 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-26 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-27 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-28 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-29 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-30 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-31 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-02 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-03 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-05 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-06 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-07 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-08 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-11 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-12 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-13 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-15 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-16 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-17 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-18 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-19 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-20 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-21 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-22 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-23 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-24 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-25 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-26 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-27 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-28 </td>
   <td align="right"> 0 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-29 </td>
   <td align="right"> 0 </td>
  </tr>
</tbody>
</table>

## What is the average daily activity pattern?

The following figure illustrates the average number of steps taken, averaged across all days (y-axis) per 5-minute interval.


```r
library(ggplot2)

qplot(activity$interval, activity$steps, geom="line", stat="summary", fun.y=mean, xlab="5 minuttes time interval", ylab="Number of steps per 5 mins time interval")
```

```
## Warning: Removed 2304 rows containing missing values (stat_summary).
```

![plot of chunk unnamed-chunk-6](figure/unnamed-chunk-6.png) 

The following calculates the 5-minute interval, on average across all the days in the dataset, which contains the maximum number of steps:

```r
averageStepsPerInterval <- aggregate(steps ~ interval, data = activity,
          FUN = mean)
averageStepsPerInterval[which.max( averageStepsPerInterval$steps),1]
```

```
## [1] 835
```


## Imputing missing values

Below we describe a strategy for imputing missing data. The strategy used is to use the averageStepsPerInterval calculated previously and use this to look up average number of steps for time intervals not having a value. We also compare imputed with non imputed data and what we see are that the average number of steps per day match up pretty close but the medians does not. For non imputed data the median is zero for each day, but for imputed data, then we have non zero medians and we also see data for dates which previously had no data at all.

The number of missing steps values are:


```r
sum(is.na(activity$steps))
```

```
## [1] 2304
```


Below we will impute missing values with the mean of steps for the interval of the missing value.
The result is stored in "imputedActivity". 

For "calculating" the mean for a given interval we are using the previous result stored in "averageStepsPerInterval".


```r
imputedActivity <- activity
# The following will reassign NA steps values for a given time interval in imputedActivity to the average 
# value for the given time interval
imputedActivity$steps <-sapply(1:length(activity$steps), function(x){
  row <- activity[x, ]
  steps <- row[,1]
  interval <- row[, 3]
  if(is.na(steps)){
    # If the steps value is not set, then we set it to average steps value for the time interval.
    # We do this by looking up the value for the selected time interval in averageStepsPerInterval.
    averageStepsPerInterval[averageStepsPerInterval$interval==interval, 2]
  }else {
    # If the steps value is set, we just use it as it is.
    steps
  }
})
```

Total number of steps per day for imputed data

```r
totalStepsPerDayImputed <- aggregate(steps ~ date, data = imputedActivity,
          FUN = sum) 

barplot(totalStepsPerDayImputed$steps,  ylab="steps", xlab="date", space=1)

text(seq(1.5,2*length(totalStepsPerDayImputed$date),by=2), par("usr")[3]-0.25, 
     srt = 60, adj= 1, xpd = TRUE,
     labels = totalStepsPerDayImputed$date, cex=0.7)
```

![plot of chunk unnamed-chunk-10](figure/unnamed-chunk-10.png) 

Average number of steps per day for imputed data

```r
averageStepsPerDayImputed <- aggregate(steps ~ date, data = imputedActivity,
          FUN = mean) 

kable(averageStepsPerDayImputed, format = "html", table.attr = "width=\"200\"")
```

<table width="200">
 <thead>
  <tr>
   <th align="left"> date </th>
   <th align="right"> steps </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td align="left"> 2012-10-01 </td>
   <td align="right"> 37.3826 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-02 </td>
   <td align="right"> 0.4375 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-03 </td>
   <td align="right"> 39.4167 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-04 </td>
   <td align="right"> 42.0694 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-05 </td>
   <td align="right"> 46.1597 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-06 </td>
   <td align="right"> 53.5417 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-07 </td>
   <td align="right"> 38.2465 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-08 </td>
   <td align="right"> 37.3826 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-09 </td>
   <td align="right"> 44.4826 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-10 </td>
   <td align="right"> 34.3750 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-11 </td>
   <td align="right"> 35.7778 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-12 </td>
   <td align="right"> 60.3542 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-13 </td>
   <td align="right"> 43.1458 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-14 </td>
   <td align="right"> 52.4236 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-15 </td>
   <td align="right"> 35.2049 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-16 </td>
   <td align="right"> 52.3750 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-17 </td>
   <td align="right"> 46.7083 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-18 </td>
   <td align="right"> 34.9167 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-19 </td>
   <td align="right"> 41.0729 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-20 </td>
   <td align="right"> 36.0938 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-21 </td>
   <td align="right"> 30.6285 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-22 </td>
   <td align="right"> 46.7361 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-23 </td>
   <td align="right"> 30.9653 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-24 </td>
   <td align="right"> 29.0104 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-25 </td>
   <td align="right"> 8.6528 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-26 </td>
   <td align="right"> 23.5347 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-27 </td>
   <td align="right"> 35.1354 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-28 </td>
   <td align="right"> 39.7847 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-29 </td>
   <td align="right"> 17.4236 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-30 </td>
   <td align="right"> 34.0938 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-31 </td>
   <td align="right"> 53.5208 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-01 </td>
   <td align="right"> 37.3826 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-02 </td>
   <td align="right"> 36.8056 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-03 </td>
   <td align="right"> 36.7049 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-04 </td>
   <td align="right"> 37.3826 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-05 </td>
   <td align="right"> 36.2465 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-06 </td>
   <td align="right"> 28.9375 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-07 </td>
   <td align="right"> 44.7326 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-08 </td>
   <td align="right"> 11.1771 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-09 </td>
   <td align="right"> 37.3826 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-10 </td>
   <td align="right"> 37.3826 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-11 </td>
   <td align="right"> 43.7778 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-12 </td>
   <td align="right"> 37.3785 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-13 </td>
   <td align="right"> 25.4722 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-14 </td>
   <td align="right"> 37.3826 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-15 </td>
   <td align="right"> 0.1424 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-16 </td>
   <td align="right"> 18.8924 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-17 </td>
   <td align="right"> 49.7882 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-18 </td>
   <td align="right"> 52.4653 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-19 </td>
   <td align="right"> 30.6979 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-20 </td>
   <td align="right"> 15.5278 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-21 </td>
   <td align="right"> 44.3993 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-22 </td>
   <td align="right"> 70.9271 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-23 </td>
   <td align="right"> 73.5903 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-24 </td>
   <td align="right"> 50.2708 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-25 </td>
   <td align="right"> 41.0903 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-26 </td>
   <td align="right"> 38.7569 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-27 </td>
   <td align="right"> 47.3819 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-28 </td>
   <td align="right"> 35.3576 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-29 </td>
   <td align="right"> 24.4688 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-30 </td>
   <td align="right"> 37.3826 </td>
  </tr>
</tbody>
</table>

To ease comparability between imputed and non-imputed data we have shown the average steps per date for imputed and non-imputed data as a plot below. The blue line represents imputed data and the red line represents non imputed data. From the plot we can see that imputed and non-imputed data match up pretty close, but differences do exists.



```r
plot(averageStepsPerDayImputed$date, averageStepsPerDayImputed$steps, type="l", col="blue", xlab="date", ylab="Average number of steps per day")
title("Comparison between imputed and non-imputed data")
lines(averageStepsPerDay$date, averageStepsPerDay$steps, type="l", col="red")

legend(averageStepsPerDayImputed$date[30], 75, c("imputed", "non-imputed"), lty = 1, col = c("blue","red"),  adj = c(0, 0.6))
```

![plot of chunk unnamed-chunk-12](figure/unnamed-chunk-12.png) 


Median number of steps per day for imputed data. Notice that we have non zero medians and that we have
data for dates previously not have any data at all.


```r
medianStepsPerDayImputed <- aggregate(steps ~ date, data = imputedActivity,
          FUN = median) 

kable(medianStepsPerDayImputed, format = "html", table.attr = "width=\"200\"")
```

<table width="200">
 <thead>
  <tr>
   <th align="left"> date </th>
   <th align="right"> steps </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td align="left"> 2012-10-01 </td>
   <td align="right"> 34.11 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-02 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-03 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-04 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-05 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-06 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-07 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-08 </td>
   <td align="right"> 34.11 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-09 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-10 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-11 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-12 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-13 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-14 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-15 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-16 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-17 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-18 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-19 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-20 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-21 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-22 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-23 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-24 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-25 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-26 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-27 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-28 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-29 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-30 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-10-31 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-01 </td>
   <td align="right"> 34.11 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-02 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-03 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-04 </td>
   <td align="right"> 34.11 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-05 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-06 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-07 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-08 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-09 </td>
   <td align="right"> 34.11 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-10 </td>
   <td align="right"> 34.11 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-11 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-12 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-13 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-14 </td>
   <td align="right"> 34.11 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-15 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-16 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-17 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-18 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-19 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-20 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-21 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-22 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-23 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-24 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-25 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-26 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-27 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-28 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-29 </td>
   <td align="right"> 0.00 </td>
  </tr>
  <tr>
   <td align="left"> 2012-11-30 </td>
   <td align="right"> 34.11 </td>
  </tr>
</tbody>
</table>




## Are there differences in activity patterns between weekdays and weekends?

The graphs below shows the average number of steps taken during the time intervals of weekends
compared to weekdays. The graphs shows that the tested people, on average and per time interval, took more steps during weekends than during weekdays.


```r
activity$day <- as.factor(ifelse(weekdays(activity$date, TRUE)=="Sat"|weekdays(activity$date, TRUE)=="Sun", "WEEKEND", "WEEKDAY"))

activity$day <- factor(activity$day, levels = c("WEEKEND", "WEEKDAY"))

library(ggplot2)

qplot(interval, steps, data=activity, geom="line", stat="summary", fun.y=mean, xlab="5 minuttes time interval", ylab="Number of steps per 5 mins time interval") +     facet_wrap(~ day, scales="free", ncol=1)
```

```
## Warning: Removed 576 rows containing missing values (stat_summary).
## Warning: Removed 1728 rows containing missing values (stat_summary).
```

![plot of chunk unnamed-chunk-14](figure/unnamed-chunk-14.png) 

