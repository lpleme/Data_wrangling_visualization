---
title: "Case Study 4: Reducing Gun Deaths (FiveThirtyEight)"
author: "Lorenzo Leme"
date: "February 04, 2020"
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
gun <- read_csv("data.csv")
```

## Background

The world is a dangerous place. During 2015 and 2016 there was a lot of discussion in the news about police shootings. FiveThirtyEight reported on gun deaths in 2016. As leaders in data journalism, they have posted a clean version of this data in their GitHub repo called full_data.csv for us to use.

While their visualizations focused on yearly averages, our client wants to create commercials that help reduce the gun deaths in the US. They would like to target the commercials in different seasons of the year (think month variable) to audiences that could have the most impact in reducing gun deaths. Our challenge is to summarize and visualize seasonal trends accros the other variables in these data.

## Data Wrangling


```r
# Use this R-Chunk to clean & wrangle your data!
gun1 <- gun %>%
  filter(!is.na(intent))

# gun2 <- gun1 %>% 
#   mutate(season = case_when(
#     month %in% 10:12 ~ "Fall",
#     month %in% 01:03 ~ "Winter",
#     month %in% 04:06 ~ "Spring",
#     TRUE ~ "Summer"
#   ))

gunwinter <- gun1 %>% 
  filter(month == c("01", "02", "03"))

gunspring <- gun1 %>% 
  filter(month == c("04", "05", "06"))

gunsummer <- gun1 %>% 
  filter(month == c("07", "08", "09"))

gunfall <- gun1 %>% 
  filter(month == c("10", "11", "12"))
```

## Data Visualization
Below is the full data set visualized before we conduct any data wrangling.


```r
# Use this R-Chunk to plot & visualize your data!
ggplot(gun1, aes(x = intent, y = X1))+
  geom_boxplot()+
  labs(y = "Number of gun deaths", x = "Intent", title = "Number of deaths based on Intent")+
  theme_minimal()
```

![](Case_Study_4_files/figure-html/plot_data-1.png)<!-- -->

Now lets filter the data in a way that will seperate it into seasons of the year. This way we can present the right data nad provide a educated answer to our respective client.


```r
ggplot(gunwinter, aes(x = intent, y = X1))+
  geom_boxplot(col = "Blue")+
  labs(y = "Number of gun deaths", x = "Intent", title = "Number of deaths based on Intent during Winter")+
  theme_minimal()
```

![](Case_Study_4_files/figure-html/unnamed-chunk-2-1.png)<!-- -->

During winter we can see that the number of suicides are far greater. That could be attributed to seasonal depression and less day time, but that can't be determined unless more data is provided. The number of undetermined gun deaths are far less than any other season that we were given data for.



```r
ggplot(gunfall, aes(x = intent, y = X1))+
  geom_boxplot(col = "Orange")+
  labs(y = "Number of gun deaths", x = "Intent", title = "Number of deaths based on Intent during fall")+
  theme_minimal()
```

![](Case_Study_4_files/figure-html/unnamed-chunk-3-1.png)<!-- -->

During the fall months we can see that the number of homicides are higher than any other season. The number of accidental gun deaths are also pretty high but not the highest among the seasons.



```r
ggplot(gunsummer, aes(x = intent, y = X1))+
  geom_boxplot(col = "Red")+
  labs(y = "Number of gun deaths", x = "Intent", title = "Number of deaths based on Intent during Summer")+
  theme_minimal()
```

![](Case_Study_4_files/figure-html/unnamed-chunk-4-1.png)<!-- -->

Accidental gun deaths are far greater during the summer seasons with the homicide gun related deaths are the lowest types of intent for that season.



```r
ggplot(gunspring, aes(x = intent, y = X1))+
  geom_boxplot(col = "Green")+
  labs(y = "Number of gun deaths", x = "Intent", title = "Number of deaths based on Intent during Spring")+
  theme_minimal()
```

![](Case_Study_4_files/figure-html/unnamed-chunk-5-1.png)<!-- -->

Spring season is has the highest number of undetermined deaths. By looking at the graph it looks similar to the summer season with slight variation. These variations are how the spring suicides are less than the summer suicides.


## Conclusions

After breaking up the data depending on seasons we can see that the number of accidental deaths by guns is far greater during the summer. The number of homicides dramatically increase during the fall months. The number of suicides are far greater during the winter months. Lastly the number of undetermined deaths are far greater during the spring months. If we had more data surrounding those seasons we could try to determine the why factor to those intents. We would be able to figure out why winter has the highest suicide rates, or why homicides are far greater during the fall season.
