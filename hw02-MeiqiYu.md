hw02-MeiqiYu
================

``` r
library(gapminder)
library(tidyverse)
```

    ## -- Attaching packages -------------------- tidyverse 1.2.1 --

    ## v ggplot2 3.0.0     v purrr   0.2.5
    ## v tibble  1.4.2     v dplyr   0.7.6
    ## v tidyr   0.8.1     v stringr 1.3.1
    ## v readr   1.1.1     v forcats 0.3.0

    ## -- Conflicts ----------------------- tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

# Smell test the data

  - Gapminder is a data.frame which is a rectangular collection of
    variables (in the columns) and observations (in the rows).
  - It contains 6 cloumns and 1704 rows.
  - We could get the facts about “extent” and “size” in the following
    six ways.

<!-- end list -->

1.  `gapminder` It shows the entire dataframe which contains 6 comlumns
    and 1704 rows.

<!-- end list -->

``` r
gapminder
```

    ## # A tibble: 1,704 x 6
    ##    country     continent  year lifeExp      pop gdpPercap
    ##    <fct>       <fct>     <int>   <dbl>    <int>     <dbl>
    ##  1 Afghanistan Asia       1952    28.8  8425333      779.
    ##  2 Afghanistan Asia       1957    30.3  9240934      821.
    ##  3 Afghanistan Asia       1962    32.0 10267083      853.
    ##  4 Afghanistan Asia       1967    34.0 11537966      836.
    ##  5 Afghanistan Asia       1972    36.1 13079460      740.
    ##  6 Afghanistan Asia       1977    38.4 14880372      786.
    ##  7 Afghanistan Asia       1982    39.9 12881816      978.
    ##  8 Afghanistan Asia       1987    40.8 13867957      852.
    ##  9 Afghanistan Asia       1992    41.7 16317921      649.
    ## 10 Afghanistan Asia       1997    41.8 22227415      635.
    ## # ... with 1,694 more rows

2.  `head(gapminder)` By runnig this command, it is clear that this
    datframe contains 6 rows as it shows below.

<!-- end list -->

``` r
head(gapminder)
```

    ## # A tibble: 6 x 6
    ##   country     continent  year lifeExp      pop gdpPercap
    ##   <fct>       <fct>     <int>   <dbl>    <int>     <dbl>
    ## 1 Afghanistan Asia       1952    28.8  8425333      779.
    ## 2 Afghanistan Asia       1957    30.3  9240934      821.
    ## 3 Afghanistan Asia       1962    32.0 10267083      853.
    ## 4 Afghanistan Asia       1967    34.0 11537966      836.
    ## 5 Afghanistan Asia       1972    36.1 13079460      740.
    ## 6 Afghanistan Asia       1977    38.4 14880372      786.

3.  `str(gapminder)` The result shows apparently the class, number of
    rows and
    varibles.

<!-- end list -->

``` r
str(gapminder)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    1704 obs. of  6 variables:
    ##  $ country  : Factor w/ 142 levels "Afghanistan",..: 1 1 1 1 1 1 1 1 1 1 ...
    ##  $ continent: Factor w/ 5 levels "Africa","Americas",..: 3 3 3 3 3 3 3 3 3 3 ...
    ##  $ year     : int  1952 1957 1962 1967 1972 1977 1982 1987 1992 1997 ...
    ##  $ lifeExp  : num  28.8 30.3 32 34 36.1 ...
    ##  $ pop      : int  8425333 9240934 10267083 11537966 13079460 14880372 12881816 13867957 16317921 22227415 ...
    ##  $ gdpPercap: num  779 821 853 836 740 ...

4.  `summary(gapminder)` It is a summary about the dataframe so you can
    easily find that how many varibles it contains. It will be used to
    help us get a knowledge about the minimun value, the max value, 1st
    Qu.,3rd Qu. and median.

<!-- end list -->

``` r
summary(gapminder)
```

    ##         country        continent        year         lifeExp     
    ##  Afghanistan:  12   Africa  :624   Min.   :1952   Min.   :23.60  
    ##  Albania    :  12   Americas:300   1st Qu.:1966   1st Qu.:48.20  
    ##  Algeria    :  12   Asia    :396   Median :1980   Median :60.71  
    ##  Angola     :  12   Europe  :360   Mean   :1980   Mean   :59.47  
    ##  Argentina  :  12   Oceania : 24   3rd Qu.:1993   3rd Qu.:70.85  
    ##  Australia  :  12                  Max.   :2007   Max.   :82.60  
    ##  (Other)    :1632                                                
    ##       pop              gdpPercap       
    ##  Min.   :6.001e+04   Min.   :   241.2  
    ##  1st Qu.:2.794e+06   1st Qu.:  1202.1  
    ##  Median :7.024e+06   Median :  3531.8  
    ##  Mean   :2.960e+07   Mean   :  7215.3  
    ##  3rd Qu.:1.959e+07   3rd Qu.:  9325.5  
    ##  Max.   :1.319e+09   Max.   :113523.1  
    ## 

5\.`dim(gapminder)` `dim()` can be used to obtain the dimensions of the
data frame (number of rows and number of columns). The output is a
vector.

``` r
dim(gapminder)
```

    ## [1] 1704    6

6\.`nrow()`and`ncol()` These two function can help us get number of rows
and number of columns, respectively.

``` r
nrow(gapminder)
```

    ## [1] 1704

``` r
ncol(gapminder)
```

    ## [1] 6

  - There are six varibles in gapminder: country, continent, year,
    lifeExp, pop and gdpRercap. Data type of each varible:
  - country: character
  - continent: character
  - year: integar
  - lifeExp: double
  - pop: integar
  - gdpPercap: double The first two varibles are categerical
    varibles(qualitative) and the last four are quantitative
    varibles(numerical).

# Explore individual variables

In this part, I choose the following two varibles to explore:
`continent` and `year`. \* Possible range of `continent`: Asia, Europe,
Africa Americas and Oceania \* Possible values of `year`: 1952 1957 1962
1967 1972 1977 1982 1987 1992 1997 2002 2007.

``` r
unique(gapminder$continent) 
```

    ## [1] Asia     Europe   Africa   Americas Oceania 
    ## Levels: Africa Americas Asia Europe Oceania

``` r
unique(gapminder$year) 
```

    ##  [1] 1952 1957 1962 1967 1972 1977 1982 1987 1992 1997 2002 2007

  - Typical values contain the Min., 1st Qu., Median, Mean, 3rd QU.,
    Max. For the `year` varible, the Min= 1952, 1st quartile= 1966,
    Median= 1980, Mean= 1980, 3rd quartile= 1993, Max= 2007.

<!-- end list -->

``` r
summary(gapminder$year)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##    1952    1966    1980    1980    1993    2007

  - Spread of data

Overall range = max-min Overall range of `year` equals to 55.

  - Distribution of data

  - The shape of `year` is uniform, which means about the same amount of
    data occurs for each varible value.

  - Mean and Median of `year` both equal to 1980.

<!-- end list -->

``` r
ggplot(gapminder,aes(year))+
  geom_histogram(bins=50)
```

![](hw02-MeiqiYu_files/figure-gfm/unnamed-chunk-10-1.png)<!-- -->

  - The standard deviation of an observation variable is the square root
    of its variance. We can know the standard deviation of `year` equals
    to 17.26533 from the below.

<!-- end list -->

``` r
sd(gapminder$year)
```

    ## [1] 17.26533

# Explore various plot types

  - A scatterplot of lifeExp and gdpPercap in blue.

<!-- end list -->

``` r
ggplot(gapminder,aes(x=lifeExp, y=(gdpPercap)))+
  geom_point(color='steelblue',size=1)
```

![](hw02-MeiqiYu_files/figure-gfm/unnamed-chunk-12-1.png)<!-- -->

  - A histogram of lifeExp with bins = 100.

<!-- end list -->

``` r
ggplot(gapminder,aes(lifeExp))+
  geom_histogram(bins=100)
```

![](hw02-MeiqiYu_files/figure-gfm/unnamed-chunk-13-1.png)<!-- -->

  - A densityplot of lifeExp.

<!-- end list -->

``` r
ggplot(gapminder,aes(lifeExp))+
  geom_density(bw=2)
```

![](hw02-MeiqiYu_files/figure-gfm/unnamed-chunk-14-1.png)<!-- -->

\*A boxplot for all the continents vs lifeExp.

``` r
a <- ggplot(gapminder,aes(continent,lifeExp)) + 
  scale_y_log10()
a + geom_boxplot()
```

![](hw02-MeiqiYu_files/figure-gfm/unnamed-chunk-15-1.png)<!-- -->

\*A violin plot for all entries of Americas and Africa occuring in the
’60s. vs lifeExp.

``` r
gapminder %>% 
  filter((continent == 'Americas' |continent == 'Africa'|continent == 'Asia') & year>=1960 & year < 1970) %>% 
  ggplot(aes(continent,lifeExp))+
  geom_violin()
```

![](hw02-MeiqiYu_files/figure-gfm/unnamed-chunk-16-1.png)<!-- -->

# Use filter(), select() and %\>%

``` r
select(gapminder, year,lifeExp) %>% 
  filter(year>=1960 & year < 1970) %>% 
  ggplot(aes(year,lifeExp))+
  geom_line()
```

![](hw02-MeiqiYu_files/figure-gfm/unnamed-chunk-17-1.png)<!-- -->

# But I want to do more\!

By running this code `filter(gapminder, country == c("Rwanda",
"Afghanistan"))`, the analyst didn’t secceed to get what they want. They
only got part of the result.

``` r
filter(gapminder, country == c("Rwanda", "Afghanistan"))
```

    ## # A tibble: 12 x 6
    ##    country     continent  year lifeExp      pop gdpPercap
    ##    <fct>       <fct>     <int>   <dbl>    <int>     <dbl>
    ##  1 Afghanistan Asia       1957    30.3  9240934      821.
    ##  2 Afghanistan Asia       1967    34.0 11537966      836.
    ##  3 Afghanistan Asia       1977    38.4 14880372      786.
    ##  4 Afghanistan Asia       1987    40.8 13867957      852.
    ##  5 Afghanistan Asia       1997    41.8 22227415      635.
    ##  6 Afghanistan Asia       2007    43.8 31889923      975.
    ##  7 Rwanda      Africa     1952    40    2534927      493.
    ##  8 Rwanda      Africa     1962    43    3051242      597.
    ##  9 Rwanda      Africa     1972    44.6  3992121      591.
    ## 10 Rwanda      Africa     1982    46.2  5507565      882.
    ## 11 Rwanda      Africa     1992    23.6  7290203      737.
    ## 12 Rwanda      Africa     2002    43.4  7852401      786.

The correct way to do this is listed below:

``` r
  d <- filter(gapminder,country == 'Rwanda' | country == 'Afghanistan')
  knitr::kable(d)
```

| country     | continent | year | lifeExp |      pop | gdpPercap |
| :---------- | :-------- | ---: | ------: | -------: | --------: |
| Afghanistan | Asia      | 1952 |  28.801 |  8425333 |  779.4453 |
| Afghanistan | Asia      | 1957 |  30.332 |  9240934 |  820.8530 |
| Afghanistan | Asia      | 1962 |  31.997 | 10267083 |  853.1007 |
| Afghanistan | Asia      | 1967 |  34.020 | 11537966 |  836.1971 |
| Afghanistan | Asia      | 1972 |  36.088 | 13079460 |  739.9811 |
| Afghanistan | Asia      | 1977 |  38.438 | 14880372 |  786.1134 |
| Afghanistan | Asia      | 1982 |  39.854 | 12881816 |  978.0114 |
| Afghanistan | Asia      | 1987 |  40.822 | 13867957 |  852.3959 |
| Afghanistan | Asia      | 1992 |  41.674 | 16317921 |  649.3414 |
| Afghanistan | Asia      | 1997 |  41.763 | 22227415 |  635.3414 |
| Afghanistan | Asia      | 2002 |  42.129 | 25268405 |  726.7341 |
| Afghanistan | Asia      | 2007 |  43.828 | 31889923 |  974.5803 |
| Rwanda      | Africa    | 1952 |  40.000 |  2534927 |  493.3239 |
| Rwanda      | Africa    | 1957 |  41.500 |  2822082 |  540.2894 |
| Rwanda      | Africa    | 1962 |  43.000 |  3051242 |  597.4731 |
| Rwanda      | Africa    | 1967 |  44.100 |  3451079 |  510.9637 |
| Rwanda      | Africa    | 1972 |  44.600 |  3992121 |  590.5807 |
| Rwanda      | Africa    | 1977 |  45.000 |  4657072 |  670.0806 |
| Rwanda      | Africa    | 1982 |  46.218 |  5507565 |  881.5706 |
| Rwanda      | Africa    | 1987 |  44.020 |  6349365 |  847.9912 |
| Rwanda      | Africa    | 1992 |  23.599 |  7290203 |  737.0686 |
| Rwanda      | Africa    | 1997 |  36.087 |  7212583 |  589.9445 |
| Rwanda      | Africa    | 2002 |  43.413 |  7852401 |  785.6538 |
| Rwanda      | Africa    | 2007 |  46.242 |  8860588 |  863.0885 |
