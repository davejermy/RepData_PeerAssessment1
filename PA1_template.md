# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data

```r
unzip("activity.zip", "activity.csv")
rawdata <- read.csv("activity.csv")
dailysteps <- aggregate(steps ~ date, data = rawdata,sum)
```
## What is mean total number of steps taken per day?

```r
library(ggplot2)
plot1 <- ggplot(dailysteps, aes(steps))
plot1 + geom_histogram(fill = "darkgreen",
                       binwidth = 500) + 
    theme_bw(base_size = 12)
```

![](./PA1_template_files/figure-html/unnamed-chunk-2-1.png) 

```r
meansteps <- round(mean(dailysteps$steps),2)
mediansteps <- median(dailysteps$steps)
```
The mean total daily steps is 1.076619\times 10^{4} and the median is 10765.

## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?

