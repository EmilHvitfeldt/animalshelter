
<!-- README.md is generated from README.Rmd. Please edit that file -->

# animalshelter

<!-- badges: start -->
<!-- badges: end -->

The goal of animalshelter is to provide a data set for [Long Beach
Animal
Shelter](https://data.longbeach.gov/explore/dataset/animal-shelter-intakes-and-outcomes).

## Installation

You can install the development version of animalshelter like so:

``` r
# install.packages("devtools")
devtools::install_github("EmilHvitfeldt/animalshelter")
```

## Example

This package contains one data set `longbeach`,

``` r
library(tidyverse)
#> ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
#> ✔ dplyr     1.1.4     ✔ readr     2.1.5
#> ✔ forcats   1.0.0     ✔ stringr   1.5.1
#> ✔ ggplot2   3.5.1     ✔ tibble    3.2.1
#> ✔ lubridate 1.9.4     ✔ tidyr     1.3.1
#> ✔ purrr     1.0.2     
#> ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
#> ✖ dplyr::filter() masks stats::filter()
#> ✖ dplyr::lag()    masks stats::lag()
#> ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
library(animalshelter)

longbeach
#> # A tibble: 29,787 × 23
#>    animal_id animal_name animal_type primary_color secondary_color sex     
#>    <chr>     <chr>       <chr>       <chr>         <chr>           <chr>   
#>  1 A693708   *charlien   dog         white         <NA>            Female  
#>  2 A708149   <NA>        reptile     brown         green           Unknown 
#>  3 A638068   <NA>        bird        green         red             Unknown 
#>  4 A639310   <NA>        bird        white         gray            Unknown 
#>  5 A618968   *morgan     cat         black         white           Female  
#>  6 A730385   *brandon    rabbit      black         white           Neutered
#>  7 A646202   <NA>        bird        black         <NA>            Unknown 
#>  8 A628138   <NA>        other       gray          black           Unknown 
#>  9 A597464   <NA>        cat         black         <NA>            Unknown 
#> 10 A734321   sophie      dog         cream         <NA>            Spayed  
#> # ℹ 29,777 more rows
#> # ℹ 17 more variables: dob <date>, intake_date <date>, intake_condition <chr>,
#> #   intake_type <chr>, intake_subtype <chr>, reason_for_intake <chr>,
#> #   outcome_date <date>, crossing <chr>, jurisdiction <chr>,
#> #   outcome_type <chr>, outcome_subtype <chr>, latitude <dbl>, longitude <dbl>,
#> #   intake_is_dead <chr>, outcome_is_dead <lgl>, was_outcome_alive <dbl>,
#> #   geopoint <chr>
```

``` r
glimpse(longbeach)
#> Rows: 29,787
#> Columns: 23
#> $ animal_id         <chr> "A693708", "A708149", "A638068", "A639310", "A618968…
#> $ animal_name       <chr> "*charlien", NA, NA, NA, "*morgan", "*brandon", NA, …
#> $ animal_type       <chr> "dog", "reptile", "bird", "bird", "cat", "rabbit", "…
#> $ primary_color     <chr> "white", "brown", "green", "white", "black", "black"…
#> $ secondary_color   <chr> NA, "green", "red", "gray", "white", "white", NA, "b…
#> $ sex               <chr> "Female", "Unknown", "Unknown", "Unknown", "Female",…
#> $ dob               <date> 2013-02-21, NA, NA, NA, 2014-12-18, 2023-04-19, NA,…
#> $ intake_date       <date> 2023-02-20, 2023-10-03, 2020-01-01, 2020-02-02, 201…
#> $ intake_condition  <chr> "ill mild", "normal", "injured  severe", "ill severe…
#> $ intake_type       <chr> "stray", "stray", "wildlife", "wildlife", "stray", "…
#> $ intake_subtype    <chr> "otc", "field", "field", "field", "field", "otc", "f…
#> $ reason_for_intake <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
#> $ outcome_date      <date> 2023-02-26, 2023-10-03, 2020-01-01, 2020-02-02, 201…
#> $ crossing          <chr> "[2600 BLK LONG BEACH BLVD, LONG BEACH CA, 90806", "…
#> $ jurisdiction      <chr> "Long Beach", "Long Beach", "Long Beach", "Long Beac…
#> $ outcome_type      <chr> "euthanasia", "rescue", "euthanasia", "transfer", "r…
#> $ outcome_subtype   <chr> "ill severe", "other resc", "inj severe", "lbah", "l…
#> $ latitude          <dbl> 33.80479, 33.86800, 33.76048, 33.76246, 33.84950, 33…
#> $ longitude         <dbl> -118.1889, -118.2009, -118.1481, -118.1597, -118.194…
#> $ intake_is_dead    <chr> "Alive on Intake", "Alive on Intake", "Alive on Inta…
#> $ outcome_is_dead   <lgl> TRUE, FALSE, TRUE, FALSE, FALSE, FALSE, TRUE, FALSE,…
#> $ was_outcome_alive <dbl> 0, 1, 0, 1, 1, 1, 0, 1, 1, 1, 1, 0, 1, 0, 0, 1, 1, 1…
#> $ geopoint          <chr> "33.8047935, -118.1889261", "33.8679994, -118.200930…
```

``` r
longbeach |>
  count(animal_type)
#> # A tibble: 10 × 2
#>    animal_type     n
#>    <chr>       <int>
#>  1 amphibian       3
#>  2 bird         2075
#>  3 cat         14145
#>  4 dog          9768
#>  5 guinea pig    172
#>  6 livestock      10
#>  7 other        1332
#>  8 rabbit        526
#>  9 reptile       344
#> 10 wild         1412
```

``` r
longbeach |>
  count(primary_color, sort = TRUE)
#> # A tibble: 76 × 2
#>    primary_color     n
#>    <chr>         <int>
#>  1 black          7540
#>  2 gray           3916
#>  3 white          3651
#>  4 brown          3531
#>  5 brown  tabby   2242
#>  6 tan            1393
#>  7 gray tabby     1189
#>  8 orange tabby    904
#>  9 calico          520
#> 10 orange          515
#> # ℹ 66 more rows
```
