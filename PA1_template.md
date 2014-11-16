# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data

```r
unzip("activity.zip", "activity.csv")
rawdata <- read.csv("activity.csv")
dailysteps <- aggregate(steps ~ date, data = rawdata,sum)
```

## What is mean total number of steps taken per day?
Let's start by looking at distribution of daily step totals.  The following chart shows how many times the daily total occurs in each strip of 500.


```r
library(ggplot2)
plot1 <- ggplot(dailysteps, aes(steps))
plot1 + geom_histogram(fill = "darkgreen",
                       binwidth = 500) + 
    theme_bw(base_size = 12)
```

![](./PA1_template_files/figure-html/unnamed-chunk-2-1.png) 

But what about the average daily total?

```r
meansteps <- as.character(round(mean(dailysteps$steps),2))
mediansteps <- median(dailysteps$steps)
```
The mean total daily steps is 10766.19 and the median is 10765.  
  
## What is the average daily activity pattern?
How does the time interval pattern change across the day?

```r
intmeansteps <- aggregate(steps ~ interval, data = rawdata, mean)
plot2 <- ggplot(intmeansteps, aes(interval, steps))
plot2 + geom_line()+ 
     theme_bw(base_size = 12)
```

![](./PA1_template_files/figure-html/unnamed-chunk-4-1.png) 

What time of day is the most active?  We can answer this by looking at the time interval with the largest average steps.

```r
maxint <- round(head(intmeansteps[order(-intmeansteps$steps),],1),2)
```

The time interval with the highest number of steps across the period is 835, with an average of 206.17 steps.

## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?

