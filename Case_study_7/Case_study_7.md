---
title: "Case Study 7: Counting names in scripture
"
author: "Lorenzo Leme"
date: "February 29, 2020"
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
scripture <- read_csv("scriptures.csv")
names <- read_rds(gzcon(url("https://byuistats.github.io/M335/data/BoM_SaviorNames.rds")))
```

## Background

In 1978 Susan Easton Black penned an article in the Ensign title Even statistically, he is the dominant figure of the Book of Mormon. which makes some statistical claims about the Book of Mormon. With our “string” skills we are going to check her result and build an improved statistic using using number of words between references.

[ ] Get the scripture and savior name data into R
[ ] Download the data from http://scriptures.nephi.org/downloads/lds-scriptures.csv.zip
[ ] Read in the .csv file that was in the zip file and examine the structure of the data
[ ] Use read_rds(gzcon(url("https://byuistats.github.io/M335/data/BoM_SaviorNames.rds"))) to download and load the Savior names table into R
[ ] Use the list of Savior names and the Book of Mormon verses to figure out the average number of words between references to the Savior
[ ] Find each instance of a Savior name in the Book of Mormon
[ ] Split on those instances and then count the number of words between each instance
[ ] Use the example code below for some hints on how to tackle this task
[ ] Report the average number of words between each Savior name
[ ] Create an .Rmd file with 1-2 paragraphs summarizing your graphic that shows how the distance between Savior names is distributed across the Book of Mormon
[ ] Compile your .md and .html file into your git repository
[ ] Find two other student’s compiled files in their repository and provide feedback using the issues feature in GitHub (If they already have three issues find a different student to critique)
[ ] Address 1-2 of the issues posted on your project and push the updates to GitHub

## Data Wrangling


```r
# Use this R-Chunk to clean & wrangle your data!
#Get only the Book of Mormon
BoM <- scripture %>% 
  filter(volume_title == "Book of Mormon")

#Savior names
names <- str_c(names$name, collapse = "|")
```


```r
#Split everything into the respective books and only show the text
Nephi1 <- filter(BoM, book_title == "1 Nephi") %>% 
  select(scripture_text)

Nephi2 <- filter(BoM, book_title == "2 Nephi") %>% 
  select(scripture_text)

Jacob <- filter(BoM, book_title == "Jacob") %>% 
  select(scripture_text)

Enos <- filter(BoM, book_title == "Enos") %>% 
  select(scripture_text)

Jarom <- filter(BoM, book_title == "Jarom") %>% 
  select(scripture_text)

Omni <- filter(BoM, book_title == "Omni") %>% 
  select(scripture_text)

WordsMormon <- filter(BoM, book_title == "Words of Mormon") %>% 
  select(scripture_text)

Mosiah <- filter(BoM, book_title == "Mosiah") %>% 
  select(scripture_text)

Alma <- filter(BoM, book_title == "Alma") %>% 
  select(scripture_text)

Helaman <- filter(BoM, book_title == "Helaman") %>% 
  select(scripture_text)

Nephi3 <- filter(BoM, book_title == "3 Nephi") %>% 
  select(scripture_text)

Nephi4 <- filter(BoM, book_title == "4 Nephi") %>% 
  select(scripture_text)

Mormon <- filter(BoM, book_title == "Mormon") %>% 
  select(scripture_text)

Ether <- filter(BoM, book_title == "Ether") %>% 
  select(scripture_text)

Moroni <- filter(BoM, book_title == "Moroni") %>% 
  select(scripture_text)
```



```r
#For loop to split the names out
for (i in seq_along(names)){
  Nephi1 <- Nephi1 %>% 
    str_split(names[i]) %>% 
    unlist()
  
  Nephi2 <- Nephi2 %>% 
    str_split(names[i]) %>% 
    unlist()
  
  Jacob <- Jacob %>% 
    str_split(names[i]) %>% 
    unlist()
  
  Enos <- Enos %>% 
    str_split(names[i]) %>% 
    unlist()
  
  Jarom <- Jarom %>% 
    str_split(names[i]) %>% 
    unlist()
  
  Omni <- Omni %>% 
    str_split(names[i]) %>% 
    unlist()
  
  WordsMormon <- WordsMormon %>% 
    str_split(names[i]) %>% 
    unlist()
  
  Mosiah <- Mosiah %>% 
    str_split(names[i]) %>% 
    unlist()
  
  Alma <- Alma %>% 
    str_split(names[i]) %>% 
    unlist()
  
  Helaman <- Helaman %>% 
    str_split(names[i]) %>% 
    unlist()
  
  Nephi3 <- Nephi3 %>% 
    str_split(names[i]) %>% 
    unlist()
  
  Nephi4 <- Nephi4 %>% 
    str_split(names[i]) %>% 
    unlist()
  
  Mormon <- Mormon %>% 
    str_split(names[i]) %>% 
    unlist()
  
  Ether <- Ether %>% 
    str_split(names[i]) %>% 
    unlist()
  
  Moroni <- Moroni %>% 
    str_split(names[i]) %>% 
    unlist()
}
```
## Data Visualization


```r
# Use this R-Chunk to plot & visualize your data!
```

## Conclusions
