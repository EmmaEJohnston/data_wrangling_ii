strings_and_factors
================
Emma
2026-10-20

``` r
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.2.1     ✔ readr     2.2.0
    ## ✔ forcats   1.0.1     ✔ stringr   1.6.0
    ## ✔ ggplot2   4.0.3     ✔ tibble    3.3.1
    ## ✔ lubridate 1.9.5     ✔ tidyr     1.3.2
    ## ✔ purrr     1.2.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
data("starwars")
```

``` r
starwars |> 
  filter(name == "Luke Skywalker") |> 
  select(name, height, films) |> 
  unnest(films)
```

    ## # A tibble: 5 × 3
    ##   name           height films                  
    ##   <chr>           <int> <chr>                  
    ## 1 Luke Skywalker    172 A New Hope             
    ## 2 Luke Skywalker    172 The Empire Strikes Back
    ## 3 Luke Skywalker    172 Return of the Jedi     
    ## 4 Luke Skywalker    172 Revenge of the Sith    
    ## 5 Luke Skywalker    172 The Force Awakens

Unnest to see all of the different films
