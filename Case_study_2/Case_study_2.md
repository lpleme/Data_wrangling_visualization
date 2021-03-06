---
title: "Case Study 2: Wealth and Life Expectancy (Gapminder)"
author: "Lorenzo Leme"
date: "January 22, 2020"
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
data(gapminder)
gapminder2 <- gapminder[!(gapminder$country == "Kuwait"), ]
```

## Background

Hans Rosling is one of the most popular data scientists on the web. His original TED talk was very popular among my friends when it came out. We are going to create some graphics using his formatted data as our weekly case study. Note that we need to remove Kuwait from the data.

I learned that with ggplot you can add a lot more variation to your graph then you can with base R. I'm honestly liking tdyverse a lot more than base R just because of how much you can manipulate your graph in one string of code. I need to get better at using the group_by statement with the summarise statement. I also want to learn more about the weighted.mean because I didn't fully get that.

## Data Wrangling


```r
# Use this R-Chunk to clean & wrangle your data!
gapminder2 <- gapminder[!(gapminder$country == "Kuwait"), ]
```

## Images


```r
# Use this R-Chunk to plot & visualize your data!

ggplot(data = gapminder2)+
  geom_point(mapping = aes(x = lifeExp, y = gdpPercap, col = continent, size = (pop/100000)))+
  scale_y_continuous(name = "GDP per capital", limits = c(300, 50000), trans = "sqrt")+
  scale_x_continuous(name = "Life Expectancy", limits = c(20,80))+
  theme_bw()+
  facet_wrap(~ year, nrow = 1)
```

![](Case_study_2_files/figure-html/plot_data-1.png)<!-- -->

```r
ggplot(gapminder)+
  geom_path(mapping = aes(x = year, y = gdpPercap, color = continent))+
  geom_point(mapping = aes(x = year, y = weighted.mean(gdpPercap), size = pop/100000))+
  scale_y_continuous(name = "GDP per capital", limits = c(0, 50000))+
  theme_bw()+
  facet_wrap(~ continent, nrow = 1)
```

![](Case_study_2_files/figure-html/plot_data-2.png)<!-- -->



