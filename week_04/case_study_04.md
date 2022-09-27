Case Study 04
================
Ehsan Ul Hoque Tanim
September 26, 2022

## Load Packages

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
    ## ✔ ggplot2 3.3.6      ✔ purrr   0.3.4 
    ## ✔ tibble  3.1.8      ✔ dplyr   1.0.10
    ## ✔ tidyr   1.2.1      ✔ stringr 1.4.1 
    ## ✔ readr   2.1.2      ✔ forcats 0.5.2 
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
library(nycflights13)
```

## Code

``` r
airports2 <- airports %>% 
  select(faa, name)%>%
  rename(dest = faa)

flights2 <- flights %>%
  select(dest,origin, distance)

flights2 %>% 
  left_join(airports2, by= "dest") %>%
  filter(distance==4983) %>% slice(1)
```

    ## # A tibble: 1 × 4
    ##   dest  origin distance name         
    ##   <chr> <chr>     <dbl> <chr>        
    ## 1 HNL   JFK        4983 Honolulu Intl
