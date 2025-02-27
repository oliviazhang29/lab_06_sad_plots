Lab 06 - Ugly charts and Simpson’s paradox
================
Olivia Zhang
02/27/2025

### Load packages and data

``` r
library(tidyverse) 
library(dsbox)
library(mosaicData) 

staff <- read_csv("data/instructional-staff.csv")

#wide to long
staff_long <- staff %>%
  pivot_longer(cols = -faculty_type, names_to = "year") %>%
  mutate(value = as.numeric(value))
```

### Exercise 1

``` r
staff_long %>%
  ggplot(aes(
    x = year,
    y = value,
    group = faculty_type,
    color = faculty_type
  )) +
  geom_line() +
  labs(title = "Trends in Instractional Staff Employmees", 
       subtitle = "between 1975 and 2011", 
       x = "Year", 
       y = "Percentage of Hires", 
       color = "Faculty Type")
```

![](lab-06_files/figure-gfm/line-plot-1.png)<!-- -->

### Exercise 2

To make the porportion of part-time faculty pop up, I would change the
color of other faculty types to black.

``` r
staff_long %>%
  ggplot(aes(
    x = year,
    y = value,
    group = faculty_type,
    color = ifelse(faculty_type == "Part-Time Faculty", "red", "black")
  )) +
  geom_line() +
  labs(title = "Trends in Instractional Staff Employmees", 
       subtitle = "between 1975 and 2011", 
       x = "Year", 
       y = "Percentage of Hires", 
       color = "Faculty Type")
```

![](lab-06_files/figure-gfm/line-plot-part-time-1.png)<!-- -->

### Exercise 3

…

Add exercise headings as needed.
