---
title: "Case Study 3: Becoming a databender"
author: "Lorenzo Leme"
date: "January 28, 2020"
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
flights<-nycflights13::flights
```



## Background

You just started your internship at a big firm in New York, and your manager gave you an extensive file of flights that departed JFK, LGA, or EWR in 2013. From this data (nycflights13::flights), which you can obtain in R (install.packages("nycflights13"); library(nycflights13)), your manager wants you to answer the following questions;

If I am leaving before noon, which two airlines do you recommend at each airport (JFK, LGA, EWR) that will have the lowest delay time at the 75th percentile?
Which origin airport is best to minimize my chances of a late arrival when I am using Delta Airlines?
Which destination airport is the worst (you decide on the metric for worst) airport for arrival time?

## Data Wrangling

This graph is totally unreadable and highlights the importance of filtering our data. Below we'll filter our data according to the question in order to make it more readable.


```r
ggplot(flights, aes(x = dep_time, y = arr_time, color = carrier))+
  geom_line()+
  facet_wrap(~origin)+
  theme_minimal()
```

![](Case_study_3_files/figure-html/unnamed-chunk-2-1.png)<!-- -->




```r
# Use this R-Chunk to clean & wrangle your data!
f1<-flights %>% 
  filter(origin %in% c("JFK","LGA","EWR"), !is.na(origin)) %>% 
    select(origin, dep_delay, dep_time) %>% 
      filter(dep_time<1200)
      

delta<-flights %>%  
  filter(carrier == "DL") %>% 
    select(carrier, arr_delay, origin)
```

## Data Visualization
## Question 1

If I am leaving before noon, which two airlines do you recommend at each airport (JFK, LGA, EWR) that will have the lowest delay time at the 75th percentile?


```r
# Use this R-Chunk to plot & visualize your data!
ggplot(f1, aes(x = origin, y = dep_delay))+
  geom_boxplot(col= "skyblue")+
  coord_cartesian(ylim = c(-20, 20))+
    labs(y = "Departure Delay", x = "Origin", title = "Departure delay when, leaving before noon, according to origin airpot")+
  theme_minimal()
```

![](Case_study_3_files/figure-html/unnamed-chunk-3-1.png)<!-- -->

## Question 2

Which origin airport is best to minimize my chances of a late arrival when I am using Delta Airlines?


```r
ggplot(delta, aes(x= origin, y=arr_delay))+
  geom_boxplot(col= "skyblue")+
  coord_cartesian(ylim = c(-50,50))+
  labs(y = "Arrival Delay", x = "Origin", title = "Arrival delay according to the origin airport")+
  theme_minimal()
```

![](Case_study_3_files/figure-html/unnamed-chunk-4-1.png)<!-- -->

## Conclusions

For question one we can see a boxplot that displays the departure delay flights will have before noon. Looking at the graph we can see that the 75th percentile for JFK and LGA are pretty similar sitting around 0. We can highlight these two graphs and look at their means. LGA has a lower mean than JFK. This means that if you plan on leaving before noon you will want to go from LGA for your chances of a delay to be less than the other airports.

Question two highlights Delta Airlines. This graph is looking at Delta Airlines arrival delay according to what airport you leave from. For this graph we will only be looking at the mean of the boxplots. By looking at the means, we can see that JFK has a lower mean of arrival delays when you're using Delta Airlines. To limit your chances of arrival delay when using Delta, you should leave from JFK.
