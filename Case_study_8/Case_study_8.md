---
title: "Case Study 8: It’s about time
"
author: "Lorenzo Leme"
date: "March 10, 2020"
output:
  html_document:  
    keep_md: true
    toc: true
    toc_float: true
    code_folding: hide
    fig_height: 6
    fig_width: 12
    fig_align: 'center'
---






```r
# Use this R-Chunk to import all your datasets!
download("https://byuistats.github.io/M335/data/sales.csv", destfile = "Sales.csv", mode = "wb")

sales <- read_csv("Sales.csv")
```

## Background

[ ] Read in the data from https://byuistats.github.io/M335/data/sales.csv and format it for visualization and analysis
[ ] The data are for businesses in the mountain time zone make sure you read in times correctly
[ ] This is point of sale (pos) data, so you will need to use library(lubridate) to create the correct time aggregations
[ ] Check the data for any inaccuracies
[ ] Help your boss understand which business is the best investment through visualizations
[ ] Provide an understanding and recommendation for hours of operation
[ ] We don’t have employee numbers, but sales traffic can help. Provide some visualizations on customer traffic
[ ] Provide a final comparison of the six companies and a final recommendation
[ ] Compile your .md and .html file into your git repository
[ ] Find two other student’s compiled files in their repository and provide feedback using the issues feature in GitHub (If they already have three issues find a different student to critique)
[ ] Address 1-2 of the issues posted on your project and push the updates to GitHub

## Data Wrangling


```r
# Use this R-Chunk to clean & wrangle your data!
sales1 <- sales %>% mutate(
  time = with_tz(Time, tzone = "America/Denver"),
  ceiling_time = ceiling_date(time, unit = "hour"),
  monthly = month(time),
  hourly = hour(time),
  date = date(time),
  weekly = week(time),)

sales2 <- sales1 %>% 
  filter(hourly > 1, Name != "Missing")
```

## Data Visualization


```r
# Use this R-Chunk to plot & visualize your data!
ggplot(sales2)+
  geom_jitter(aes(x = hourly, y = Amount, col = as.factor(monthly)))+
  scale_colour_brewer()+
  facet_wrap(~ Name, nrow=3)+
  theme_minimal()+
  labs(x = "Hour", y = "Amount", title = "Amount Hourly by Month", color = "Month")
```

![](Case_study_8_files/figure-html/plot_data-1.png)<!-- -->



```r
ggplot(sales2)+
  geom_jitter(aes(x = weekly, y = Amount))+
  facet_wrap(~ Name, nrow=3)+
  theme_minimal()+
  labs(x = "Week", y = "Amount", title = "Amount Weekly")
```

![](Case_study_8_files/figure-html/unnamed-chunk-2-1.png)<!-- -->

## Conclusions

Looking at the weekly and hourly data that we have created, I would recommend investing into LeBelle. LeBelle has the most hourly traffic over all months comparative to any other company. Not even that but the traffic is at a high for the majority of the hours. If we look at the weekly amount we can see that the data is pretty much on top of eachother, but also has a high maximum. This means that they consistently get high traffic over the weeks. A close second company would be HotDiggity because they are more spread out, but still very consistent 
