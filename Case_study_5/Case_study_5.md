---
title: "Case Study 5: I can clean your data"
author: "Lorenzo Leme"
date: "February 08, 2020"
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
download("https://byuistats.github.io/M335/data/heights/germanconscr.dta", destfile= "germanconscr.dta", mode="wb")
height_conscr <- read_dta("germanconscr.dta")

download("https://byuistats.github.io/M335/data/heights/germanprison.dta", destfile= "germanprison.dta", mode="wb")
height_prison <- read_dta("germanprison.dta")

download("https://github.com/hadley/r4ds/raw/master/data/heights.csv", destfile= "height.csv", mode="wb")
height <- read_csv("height.csv")

download("http://www.ssc.wisc.edu/nsfh/wave3/NSFH3%20Apr%202005%20release/main05022005.sav", destfile = "height.sav", mode="wb")
heights <- read_sav("height.sav")

xlsx_height <- read_xlsx("Height.xlsx", skip = 2)

dbf_height <- read.dbf("Heights_south-east/B6090.DBF")
```

## Background

The Scientific American argues that humans have been getting taller over the years. As the data scientists that we are becoming, we would like to find data that validates this concept. Our challenge is to show different male heights across the centuries.

This project is not as severe as the two quotes below, but it will give you a taste of pulling various data and file formats together into “tidy” data for visualization and analysis. You will not need to search for data as all the files are listed here

“Classroom data are like teddy bears and real data are like a grizzly bear with salmon blood dripping out its mouth.” - Jenny Bryan
“Up to 80% of data analysis is spent on the process of cleaning and preparing data” - Hadley Wickham

## Data Wrangling


```r
# Use this R-Chunk to clean & wrangle your data!
colnames(xlsx_height)[2] <- "Country"
clean_xl <- xlsx_height %>% 
  gather(year, height, -c(Code, Country), na.rm = TRUE) %>%
    mutate(height_in = conv_unit(height, "cm", "inch"),
          century = substr(as.character(year), 1,2),
          decade = substr(as.character(year), 3,4),
          year = substr(as.character(year),1,4),)

colnames(height_conscr)[2] <- "birth_year"
colnames(height_conscr)[3] <- "height_cm"

height_conscr1 <- height_conscr %>% 
  mutate(height_in = conv_unit(height_cm, "cm","inch"),
         century = substr(as.character(birth_year), 1,2)) %>% 
  select(height_cm, height_in, birth_year, century)
         
colnames(height_prison)[2] <- "birth_year"
colnames(height_prison)[4] <- "height_cm"

height_prison1 <- height_prison %>%
  mutate(height_in = conv_unit(height_cm, "cm", "inch"),
         century = substr(as.character(birth_year), 1,2)) %>% 
  select(height_cm, height_in, birth_year, century)

colnames(dbf_height)[14] <- "birth_year"
colnames(dbf_height)[15] <- "height_cm"

height1 <- dbf_height %>% 
  mutate(height_in = conv_unit(height_cm, "cm", "inch"),
         century = substr(as.character(birth_year), 1,2)) %>% 
  select(height_cm, height_in, birth_year, century)

colnames(height)[2] <- "height_cm"

height_csv <- height %>% 
  mutate(birth_year = 1950,
         height_in = conv_unit(height_cm, "cm", "inch"),
         century = substr(as.character(birth_year), 1,2)) %>% 
  select(height_cm, height_in, birth_year, century)

colnames(heights)[6] <- "birth_year"
colnames(heights)[367] <-  "height_ft"
colnames(heights)[368] <- "height_inch"

height_sav <- heights %>% 
  filter(height_inch < 12) %>%
    mutate(height_in1 = conv_unit(height_ft, "feet", "inch"),
         height_in = (height_in1 + height_inch),
         height_cm = conv_unit(height_in, "cm", "inch"),
         birth_year = (birth_year + 1900),
         century = substr(as.character(birth_year), 1,2)) %>% 
  select(height_cm, height_in, birth_year, century)

combined_height_data <- rbind(height_csv, height_sav, height1, height_prison1, height_conscr1)


germany <- clean_xl %>% 
  filter(Country == "Germany")
```

## Data Visualization


```r
# Use this R-Chunk to plot & visualize your data!

ggplot(clean_xl, aes(x = decade, y = height_in))+
  geom_point()+
  geom_point(data = germany, aes(decade, height_in, color = "Germany", size = 4))+
  theme_minimal()+
  labs(title = "Height distribution over the decades in relation to Germany", x = "Decades", y= "Height (Inches)")
```

![](Case_study_5_files/figure-html/plot_data-1.png)<!-- -->

```r
ggplot(combined_height_data, aes(x = century, y = height_in))+
  geom_point()+
  theme_minimal()+
  labs(title = "Distribution in height over the centuries", x = "Century", y = "Height (Inches)")
```

![](Case_study_5_files/figure-html/plot_data-2.png)<!-- -->

## Conclusions

According to the first graph we can see that the average of height becomes a lot small and more spread out comparatively with the other decades. More data would be needed to figure out why that is. According to the second graph the 19th century also has a larger spread than the other centuries. This is probably due to population growth.
