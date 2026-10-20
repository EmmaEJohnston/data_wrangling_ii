strings_and_factors
================
Emma
2026-10-20

## Strings vs Factors

Both look like character vectors but:

- strings are just strings
- factors have an underlying numeric structure with character labels
  sitting on top

Factors generally make sense for variables that take on a few meaningful
values

- scales (very bad, bad, okay, good, very good)
- race
- BMI category

Strings make sense for less structured character values

Base R had some biases towards factors

## Common string operations

There are lots of things you can do with strings some are very common:

- concatenating: joining snippets into a long string
- shortening, subsetting, truncating
- changing cases
- replacing one string segment with another

All in stringr package (in tidyverse)

## Regular expressions

String operations are easy when you know what you’re looking for when
you know a general pattern but not an exact match, you need to use
regular expressions

- instead of looking for the letter “a”, you might look for any string
  that starts with a lower-case vowel

## Factors

Controlling factors is critical for several situations

- defining reference group in models
- ordering vartiables in output (tables or plots)
- introducing new factor levels

Commons factor operations

- converting characters to factors
- re leveling by hand or by count or by second variable
- renaming levels
- dropping unused levels

The forcats package to go for the majority of your factor needs

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
