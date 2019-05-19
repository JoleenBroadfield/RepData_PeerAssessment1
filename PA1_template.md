------------------------------------------------------------------------

#### *My Rmarkdown settings*

    library(knitr)
    opts_chunk$set(echo = TRUE, results = "asis")

------------------------------------------------------------------------

### Loading and Preprocessing the data

1.  Loading the dataset

<!-- -->

    data <- read.csv("/Users/datascience/Downloads/activity.csv")
    data$date <- as.Date(data$date, "%Y-%m-%d")

1.  Process/transform the data (if necessary) into a format suitable for
    your analysis (dataset without missing values) :

<!-- -->

    dataNoNA <- na.omit(data)

------------------------------------------------------------------------

What is mean total number of steps taken per day?
-------------------------------------------------

*Missing values were ignored here.*

1.  Calculate the total number of steps taken per day

<!-- -->

    totalperday <- aggregate(x=dataNoNA$steps, by = list(Category=dataNoNA$date), FUN= sum)
    colnames(totalperday) <- c("date","total.steps")

<table>
<caption>Total number of steps taken per day</caption>
<thead>
<tr class="header">
<th align="left">date</th>
<th align="right">total.steps</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">2012-10-02</td>
<td align="right">126</td>
</tr>
<tr class="even">
<td align="left">2012-10-03</td>
<td align="right">11352</td>
</tr>
<tr class="odd">
<td align="left">2012-10-04</td>
<td align="right">12116</td>
</tr>
<tr class="even">
<td align="left">2012-10-05</td>
<td align="right">13294</td>
</tr>
<tr class="odd">
<td align="left">2012-10-06</td>
<td align="right">15420</td>
</tr>
<tr class="even">
<td align="left">2012-10-07</td>
<td align="right">11015</td>
</tr>
<tr class="odd">
<td align="left">2012-10-09</td>
<td align="right">12811</td>
</tr>
<tr class="even">
<td align="left">2012-10-10</td>
<td align="right">9900</td>
</tr>
<tr class="odd">
<td align="left">2012-10-11</td>
<td align="right">10304</td>
</tr>
<tr class="even">
<td align="left">2012-10-12</td>
<td align="right">17382</td>
</tr>
<tr class="odd">
<td align="left">2012-10-13</td>
<td align="right">12426</td>
</tr>
<tr class="even">
<td align="left">2012-10-14</td>
<td align="right">15098</td>
</tr>
<tr class="odd">
<td align="left">2012-10-15</td>
<td align="right">10139</td>
</tr>
<tr class="even">
<td align="left">2012-10-16</td>
<td align="right">15084</td>
</tr>
<tr class="odd">
<td align="left">2012-10-17</td>
<td align="right">13452</td>
</tr>
<tr class="even">
<td align="left">2012-10-18</td>
<td align="right">10056</td>
</tr>
<tr class="odd">
<td align="left">2012-10-19</td>
<td align="right">11829</td>
</tr>
<tr class="even">
<td align="left">2012-10-20</td>
<td align="right">10395</td>
</tr>
<tr class="odd">
<td align="left">2012-10-21</td>
<td align="right">8821</td>
</tr>
<tr class="even">
<td align="left">2012-10-22</td>
<td align="right">13460</td>
</tr>
<tr class="odd">
<td align="left">2012-10-23</td>
<td align="right">8918</td>
</tr>
<tr class="even">
<td align="left">2012-10-24</td>
<td align="right">8355</td>
</tr>
<tr class="odd">
<td align="left">2012-10-25</td>
<td align="right">2492</td>
</tr>
<tr class="even">
<td align="left">2012-10-26</td>
<td align="right">6778</td>
</tr>
<tr class="odd">
<td align="left">2012-10-27</td>
<td align="right">10119</td>
</tr>
<tr class="even">
<td align="left">2012-10-28</td>
<td align="right">11458</td>
</tr>
<tr class="odd">
<td align="left">2012-10-29</td>
<td align="right">5018</td>
</tr>
<tr class="even">
<td align="left">2012-10-30</td>
<td align="right">9819</td>
</tr>
<tr class="odd">
<td align="left">2012-10-31</td>
<td align="right">15414</td>
</tr>
<tr class="even">
<td align="left">2012-11-02</td>
<td align="right">10600</td>
</tr>
<tr class="odd">
<td align="left">2012-11-03</td>
<td align="right">10571</td>
</tr>
<tr class="even">
<td align="left">2012-11-05</td>
<td align="right">10439</td>
</tr>
<tr class="odd">
<td align="left">2012-11-06</td>
<td align="right">8334</td>
</tr>
<tr class="even">
<td align="left">2012-11-07</td>
<td align="right">12883</td>
</tr>
<tr class="odd">
<td align="left">2012-11-08</td>
<td align="right">3219</td>
</tr>
<tr class="even">
<td align="left">2012-11-11</td>
<td align="right">12608</td>
</tr>
<tr class="odd">
<td align="left">2012-11-12</td>
<td align="right">10765</td>
</tr>
<tr class="even">
<td align="left">2012-11-13</td>
<td align="right">7336</td>
</tr>
<tr class="odd">
<td align="left">2012-11-15</td>
<td align="right">41</td>
</tr>
<tr class="even">
<td align="left">2012-11-16</td>
<td align="right">5441</td>
</tr>
<tr class="odd">
<td align="left">2012-11-17</td>
<td align="right">14339</td>
</tr>
<tr class="even">
<td align="left">2012-11-18</td>
<td align="right">15110</td>
</tr>
<tr class="odd">
<td align="left">2012-11-19</td>
<td align="right">8841</td>
</tr>
<tr class="even">
<td align="left">2012-11-20</td>
<td align="right">4472</td>
</tr>
<tr class="odd">
<td align="left">2012-11-21</td>
<td align="right">12787</td>
</tr>
<tr class="even">
<td align="left">2012-11-22</td>
<td align="right">20427</td>
</tr>
<tr class="odd">
<td align="left">2012-11-23</td>
<td align="right">21194</td>
</tr>
<tr class="even">
<td align="left">2012-11-24</td>
<td align="right">14478</td>
</tr>
<tr class="odd">
<td align="left">2012-11-25</td>
<td align="right">11834</td>
</tr>
<tr class="even">
<td align="left">2012-11-26</td>
<td align="right">11162</td>
</tr>
<tr class="odd">
<td align="left">2012-11-27</td>
<td align="right">13646</td>
</tr>
<tr class="even">
<td align="left">2012-11-28</td>
<td align="right">10183</td>
</tr>
<tr class="odd">
<td align="left">2012-11-29</td>
<td align="right">7047</td>
</tr>
</tbody>
</table>

1.  Histogram of the total number of steps taken each day :

<!-- -->

    hist(totalperday$total.steps, breaks=20, xlim = c(0, 25000), ylim = c(0, 15), xlab="Total steps per day", main= "Total number of steps per day", las=1)

![](PA1_template_files/figure-markdown_strict/hist%20total%20step-1.png)

1.  Calculate and report the mean and median of the total number of
    steps taken per day

<!-- -->

    summary(totalperday)

    ##       date             total.steps   
    ##  Min.   :2012-10-02   Min.   :   41  
    ##  1st Qu.:2012-10-16   1st Qu.: 8841  
    ##  Median :2012-10-29   Median :10765  
    ##  Mean   :2012-10-30   Mean   :10766  
    ##  3rd Qu.:2012-11-16   3rd Qu.:13294  
    ##  Max.   :2012-11-29   Max.   :21194

*The mean is : 10 766 steps, the median is : 10 765 steps.*

------------------------------------------------------------------------

What is the average daily activity pattern?
-------------------------------------------

1.  Make a time series plot (i.e. type="l") of the 5-minute interval
    (x-axis) and the average number of steps taken, averaged across all
    days (y-axis)

<!-- -->

    library(reshape)
    dtmtd <- melt(dataNoNA, id=c("interval", "date"))
    dailymean <- cast(dtmtd, interval~variable, mean)

    plot(x=dailymean$interval, y=dailymean$steps, type="l", main= "Average daily activity pattern", xlab="interval in the day", ylab="average steps per interval")

![](PA1_template_files/figure-markdown_strict/average%20activity%20pattern%20step-1.png)

1.  Which 5-minute interval, on average across all the days in the
    dataset, contains the maximum number of steps?

<!-- -->

    stepmax <- which.max(dailymean$steps)
    dailymean[stepmax,]

    ##     interval    steps
    ## 104      835 206.1698

*Interval 835 contains the maximum of steps (i.e., 206.1698).*

------------------------------------------------------------------------

Imputing Missing Values
-----------------------

1.  Calculate and report the total number of missing values in the
    dataset (i.e. the total number of rows with NAs)

<!-- -->

    paste("The total number of missing values is ", sum(is.na(data$steps)), ".")

\[1\] "The total number of missing values is 2304 ."

1.  Devise a strategy for filling in all of the missing values in the
    dataset. The strategy does not need to be sophisticated. For
    example, you could use the mean/median for that day, or the mean for
    that 5-minute interval, etc.

*The strategy chosen will be the mean of that 5-minute interval.*

1.  Create a new dataset that is equal to the original dataset but with
    the missing data filled in.

<!-- -->

    newdata <- merge(data, dailymean, by = "interval")
    NaIndex <- is.na(newdata$steps.x)
    newdata <- within(newdata, steps.x[NaIndex] <- steps.y[NaIndex])
    newdata$steps.y <- NULL
    colnames(newdata) <- c("interval", "steps", "date")

1.  Make a histogram of the total number of steps taken each day and
    Calculate and report the mean and median total number of steps taken
    per day. Do these values differ from the estimates from the first
    part of the assignment? What is the impact of imputing missing data
    on the estimates of the total daily number of steps?

<!-- -->

    newtotalperday <- aggregate(x=newdata$steps, by = list(Category=newdata$date), FUN= sum)
    hist(newtotalperday$x, breaks=20, xlim = c(0, 25000), xlab="Total steps per day", main= "Total number of steps per day (imputed)", las=1)

![](PA1_template_files/figure-markdown_strict/new%20histogram%20step-1.png)

    summary(newtotalperday)

    ##     Category                x        
    ##  Min.   :2012-10-01   Min.   :   41  
    ##  1st Qu.:2012-10-16   1st Qu.: 9819  
    ##  Median :2012-10-31   Median :10766  
    ##  Mean   :2012-10-31   Mean   :10766  
    ##  3rd Qu.:2012-11-15   3rd Qu.:12811  
    ##  Max.   :2012-11-30   Max.   :21194

<br> *There is little difference between the original data and imputed
data, the median remains 10 766, the mean stightly changed from 10 765
to 10 766. The histogram shows a higher number of steps with imputed
data.*

------------------------------------------------------------------------

Are there differences in activity patterns between weekdays and weekends?
-------------------------------------------------------------------------

*The dataset with the filled-in missing values is used here.*

1.  Create a new factor variable in the dataset with two levels –
    “weekday” and “weekend” indicating whether a given date is a weekday
    or weekend day.

<!-- -->

    ## 
    ## Attaching package: 'lubridate'

    ## The following object is masked from 'package:reshape':
    ## 
    ##     stamp

    ## The following object is masked from 'package:base':
    ## 
    ##     date

    ## ── Attaching packages ─────────────────────────────────────────── tidyverse 1.2.1 ──

    ## ✔ ggplot2 3.1.1       ✔ purrr   0.3.2  
    ## ✔ tibble  2.1.1       ✔ dplyr   0.8.0.1
    ## ✔ tidyr   0.8.3       ✔ stringr 1.4.0  
    ## ✔ readr   1.3.1       ✔ forcats 0.4.0

    ## ── Conflicts ────────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ lubridate::as.difftime() masks base::as.difftime()
    ## ✖ lubridate::date()        masks base::date()
    ## ✖ tidyr::expand()          masks reshape::expand()
    ## ✖ dplyr::filter()          masks stats::filter()
    ## ✖ lubridate::intersect()   masks base::intersect()
    ## ✖ dplyr::lag()             masks stats::lag()
    ## ✖ dplyr::rename()          masks reshape::rename()
    ## ✖ lubridate::setdiff()     masks base::setdiff()
    ## ✖ lubridate::stamp()       masks reshape::stamp()
    ## ✖ lubridate::union()       masks base::union()

    weekday <- c('Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday')
    newdata$wkday <- factor((weekdays(newdata$date) %in% weekday), levels=c(FALSE, TRUE), labels=c('weekend', 'weekday'))

1.  Make a panel plot containing a time series plot (i.e. type="l") of
    the 5-minute interval (x-axis) and the average number of steps
    taken, averaged across all weekday days or weekend days (y-axis).
    See the README file in the GitHub repository to see an example of
    what this plot should look like using simulated data.

<!-- -->

    library(ggplot2)
    newplt <- ggplot(newdata, aes(interval, steps)) +
        geom_line(stat = "identity", aes(colour = wkday)) + theme_gray() +
        facet_grid(wkday ~ ., scales="fixed", space="fixed") +
        labs(x="Interval", y=expression("Number of Steps")) +
        ggtitle("Number of steps Per Interval by type of day")
    print(newplt)

![](PA1_template_files/figure-markdown_strict/panel%20plot%20step-1.png)
<br/> *We can observe that activity starts later during the week-end,
with a peak in second half of the day. Activity patterns during week
days differ from week-end activity patterns, with an earlier start and a
peak in activity in the first half of the day.*

------------------------------------------------------------------------
