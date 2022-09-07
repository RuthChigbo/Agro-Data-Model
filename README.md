# Agro-Data-Model
practicing t.test , chi test and ordinary test 


---
title: "Agro.prtc"
output: html_document
date: "2022-08-31"
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

## R Markdown

This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

```{r cars}
summary(cars)
```

## Including Plots

You can also embed plots, for example:

```{r pressure, echo=FALSE}
plot(pressure)
Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.
```
```{r}
# Load packages

install.packages("easypackages")
library(easypackages) 

# Data wrangling
 
library(tidyverse)

# Dates operations

library(lubridate) 

# Table formatting

library(kableExtra) 

# Weather databases
install.packages("weatherr")
install.packages("daymetr")
install.packages("nasapower")
install.packages("chirps")
library(nasapower)
library(chirps) 

# Shannon Diversity Index
install.packages("vegan")
library(vegan) 


### Importing a `.csv` file

Here we import your table from the csv file, and show how input tables should look like right after importing:
  
  #### Seasonal
  
  ```{r}


# Current directory or any path:

path <- paste0(getwd(), '/') 

# Place your file in the current working directory (getwd)


# input Seasonal data input
file_input <- paste0(path, 'Example_input.csv')
# Change to your file

# Open seasonal file
dataframe.input <- read.table('Example_input.csv', sep = ',', header = TRUE) %>%
  mutate_at(vars(6:ncol(.)), ~as.Date(., format = '%Y_%m_%d'))


  # DS: mutate_at has been superseded. Use across()...
  # dplyr::mutate_at(vars(6:ncol(.)), ~as.Date(., format = '%Y_%m_%d'))
  
 
# View Seasonal

kable(df.input) %>% 
  kable_styling(latex_options = c("striped"), position = "center", font_size
= 10)

```
####Historical 


# Current directory or any path:
path <- paste0(getwd(), '/')
# Place your file in the current working directory (getwd)

# Historical data input
file_historical <- paste0(path, 'Example_input_historical.csv') # Change to your file

# Open historical file
df.historical <- 
  read.table(file_historical, sep=',', header = TRUE) %>% 
  # mutate_at(vars(6:ncol(.)), ~as.Date(., format='%Y_%m_%d'))
  
  dplyr::mutate(across(6:ncol(.), ~as.Date(., format = '%Y_%m_%d')))

# View Historical
kable(df.historical) %>% 
  kable_styling(latex_options = c("striped"), position = "center", font_size = 10)


```

