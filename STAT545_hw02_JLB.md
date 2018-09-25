STAT545\_hw02\_JLB
================

STAT 545 Homework 2
===================

The different sections of this homework are broken down into the sections outlined in [the homework instructions](http://stat545.com/Classroom/assignments/hw02/hw02.html):

**Homework 2 Task list: **

1.  \[x\] Getting Started: Install Gapminder & dyplyr
2.  \[x\]Smell test the data: Explore the gapminder object
3.  \[x\]Explore individual variables:
4.  \[x\]Explore various plot types:
5.  \[x\]Extra exercise:
6.  \[ \]Conclusions and Reflection:

### 1. Getting Started:

Install/Load Gapminder and dyplyr (through the tidyverse package)

``` r
library(gapminder)
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.2.1 ──

    ## ✔ ggplot2 2.2.1     ✔ purrr   0.2.4
    ## ✔ tibble  1.4.1     ✔ dplyr   0.7.4
    ## ✔ tidyr   0.7.2     ✔ stringr 1.2.0
    ## ✔ readr   1.1.1     ✔ forcats 0.2.0

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

### 2. Smell test the data:

Explore the gapminder object:

**2a. Is it a dataframe, matrix, vector, list?**
The typeof() function will tell me what data types gapminder contains.
The class() function will tell me the class of the object gapminder.

``` r
?gapminder
typeof(gapminder)
```

    ## [1] "list"

``` r
class(gapminder)
```

    ## [1] "tbl_df"     "tbl"        "data.frame"

Conclusion: - Gapminder is a data frame that contains list data.

**2b. What is its class?**
As shown above, we can use the class() function to determine the class of the gapminder object:

``` r
(class(gapminder))
```

    ## [1] "tbl_df"     "tbl"        "data.frame"

Conclusion: The class of gapminder is a data frame, specifically, a tibble (which we have not yet explored in class)

**2c. How many columns/variables?**

``` r
(ncol(gapminder))
```

    ## [1] 6

Conclusion: There are 6 variables in gapminder.

**2d. How many rows/observations?**

``` r
(nrow(gapminder))
```

    ## [1] 1704

Conclusion: There are 1704 observations in gapminder.

**2e Can you get these facts about “extent” or “size” in more than one way? Can you imagine different functions being useful in different contexts?**
I found additional information on how to further explore gapminder [here](http://adv-r.had.co.nz/Data-structures.html)

``` r
?gapminder
length(gapminder) 
```

    ## [1] 6

``` r
#attributes(gapminder)
```

Conclusion:

1.  using ?gapminder is another way to get information about gapminder such as format, names and types of variables in the object, and specific descriptions of each variable. context: This function is useful for getting a quick overview and understanding the data and where it comes from.

2.  length(gapminder) returns the number of elements inside it, in this case, the number of variables. Another application of the length() function is to look at length of and array variable, allowing users to make a loop that repeats for each value in the array.

3.  the attributes(gapminder) function is similar to summary(), but gives information about row names as well. In this context the row names are simply numbers 1, 2, 3, etc... (so, less useful), but in other contexts these names may be more informative.

**2f What data type is each variable?**
using the str() function allows us to look at the structure of the variables

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

``` r
#to double check the output of str(), I can check a variable individually:
class(gapminder$year)
```

    ## [1] "integer"

Conclusion: The variables in gapminder are lists containing different datatypes: country - factors continent - factors year - integers lifeExp - numbers pop - integers gdpPercap - numbers

#### 3. Explore individual variables

Categorical variable selected: continent Quantitative variable selected: gdpPercap

\*\* 3a. Exploring possible values (or range, whichever is appropriate) of variables:\*\*

I can look at the range of GDP per capitda in the data:
The min() function shows the lowest, while the max() function shows the highest GDP per Capita. The range() function gives both min and max as an output.

``` r
min(gapminder$gdpPercap)
```

    ## [1] 241.1659

``` r
max(gapminder$gdpPercap)
```

    ## [1] 113523.1

``` r
range(gapminder$gdpPercap)
```

    ## [1]    241.1659 113523.1329

**Conclusion:**
the range of GDP per capitda in the gapminder dataset is $241-113 523.

Looking at the spread of values :

``` r
#spread(gapminder, key,value)
```

I can also use the min(), max() and range() functions with the lifeExp, because it contains integers, however, this will not work for the country variable, as these functions do not apply.

``` r
min(gapminder$lifeExp)
```

    ## [1] 23.599

``` r
max(gapminder$lifeExp)
```

    ## [1] 82.603

``` r
range(gapminder$lifeExp)
```

    ## [1] 23.599 82.603

Conclusion: The range of life expectancies contained in the gapminder dataset is 23.6 - 82.6 years.

To look at the distribution of the continent variable:

``` r
attributes(gapminder$continent)
```

    ## $levels
    ## [1] "Africa"   "Americas" "Asia"     "Europe"   "Oceania" 
    ## 
    ## $class
    ## [1] "factor"

These values seem typical, as they are representative of the world's continents.

SUMMARY TABLE:

Looking more closely at the country and lifeExp variables:

``` r
select(gapminder, country, year, lifeExp) %>% 
  filter(year == "2007") %>% 
  summary()
```

    ##         country         year         lifeExp     
    ##  Afghanistan:  1   Min.   :2007   Min.   :39.61  
    ##  Albania    :  1   1st Qu.:2007   1st Qu.:57.16  
    ##  Algeria    :  1   Median :2007   Median :71.94  
    ##  Angola     :  1   Mean   :2007   Mean   :67.01  
    ##  Argentina  :  1   3rd Qu.:2007   3rd Qu.:76.41  
    ##  Australia  :  1   Max.   :2007   Max.   :82.60  
    ##  (Other)    :136

#### Explore various plot types

useful [site](https://stackoverflow.com/questions/10438752/adding-x-and-y-axis-labels-in-ggplot2) for how to add axis labels and title for your ggplot

-   A scatterplot of two quantitative variables.

``` r
#similar to how we saw filtering by a variable such as 'country' in class for geom_line, we can also do this to assign colours using colour = country. 

gapminder %>% 
  
  filter(country == "Canada"|country == "United States") %>% 
  ggplot(aes(x=year, y=pop)) + 
  geom_point() +
  geom_line(aes(filter = country,colour = country)) +
  xlab("Year") +
  ylab("Population of Canada and United States") +
  ggtitle("North American Population Trends")
```

    ## Warning: Ignoring unknown aesthetics: filter

![](STAT545_hw02_JLB_files/figure-markdown_github/unnamed-chunk-14-1.png)

``` r
gapminder %>% 
  filter(country == "Canada" | country =="United States")%>% 
  ggplot(aes(x=year, y = gdpPercap)) +
  geom_line(aes(group = country, colour = country)) +
  geom_point() +
  xlab("Year") +
  ylab("GDP Per Capita") +
  ggtitle("North American GDP Per Capita Trends")
```

![](STAT545_hw02_JLB_files/figure-markdown_github/unnamed-chunk-15-1.png)

-   A plot of one quantitative variable. Maybe a histogram or densityplot or frequency polygon.

``` r
gapminder %>%
  filter (year == "2007") %>% 
  ggplot(aes(gdpPercap)) +
  geom_histogram(aes(y=..density..),bins = 35) + 
  geom_density(fill = "green", alpha = 0.2)
```

![](STAT545_hw02_JLB_files/figure-markdown_github/unnamed-chunk-16-1.png)

``` r
#looking more closely at the spread of density where gdpPercap is less than  5000:

gapminder %>% 
  filter (year == "2007" & gdpPercap < 5000) %>% 
  ggplot(aes(gdpPercap)) +
  geom_histogram(bins = 20)
```

![](STAT545_hw02_JLB_files/figure-markdown_github/unnamed-chunk-16-2.png)

``` r
#Table showing the 20 countries with the lowest GDP per capita in 2007, in ascending order. 
gapminder %>%
  filter (year == "2007") %>% 
  select (country, gdpPercap) %>% 
  top_n (-20) %>% 
  arrange(gdpPercap)
```

    ## Selecting by gdpPercap

    ## # A tibble: 20 x 2
    ##    country                  gdpPercap
    ##    <fctr>                       <dbl>
    ##  1 Congo, Dem. Rep.               278
    ##  2 Liberia                        415
    ##  3 Burundi                        430
    ##  4 Zimbabwe                       470
    ##  5 Guinea-Bissau                  579
    ##  6 Niger                          620
    ##  7 Eritrea                        641
    ##  8 Ethiopia                       691
    ##  9 Central African Republic       706
    ## 10 Gambia                         753
    ## 11 Malawi                         759
    ## 12 Mozambique                     824
    ## 13 Sierra Leone                   863
    ## 14 Rwanda                         863
    ## 15 Togo                           883
    ## 16 Somalia                        926
    ## 17 Guinea                         943
    ## 18 Myanmar                        944
    ## 19 Afghanistan                    975
    ## 20 Comoros                        986

``` r
#Table showing the 20 countries with highest GDP per capita in 2007 in ascending order
gapminder %>%
  filter (year == "2007") %>% 
  select (country, gdpPercap) %>% 
  top_n (20) %>% 
  arrange(gdpPercap)
```

    ## Selecting by gdpPercap

    ## # A tibble: 20 x 2
    ##    country          gdpPercap
    ##    <fctr>               <dbl>
    ##  1 France               30470
    ##  2 Japan                31656
    ##  3 Germany              32170
    ##  4 United Kingdom       33203
    ##  5 Finland              33207
    ##  6 Belgium              33693
    ##  7 Sweden               33860
    ##  8 Australia            34435
    ##  9 Denmark              35278
    ## 10 Austria              36126
    ## 11 Iceland              36181
    ## 12 Canada               36319
    ## 13 Netherlands          36798
    ## 14 Switzerland          37506
    ## 15 Hong Kong, China     39725
    ## 16 Ireland              40676
    ## 17 United States        42952
    ## 18 Singapore            47143
    ## 19 Kuwait               47307
    ## 20 Norway               49357

``` r
gapminder %>%
  select(gdpPercap, continent) %>% 
  ggplot(aes(continent, gdpPercap)) +
  scale_y_log10() +
  geom_violin() +
  geom_jitter(alpha = 0.15) +
  xlab("Continent")+
  ylab("GDP Per Capita (log10)") +
  ggtitle("GDP Per Capita by Continent")
```

![](STAT545_hw02_JLB_files/figure-markdown_github/unnamed-chunk-17-1.png)

-   A plot of one quantitative variable and one categorical. Maybe boxplots for several continents or countries. \#\#\#\#Extra Exercise:

Instructions: Evaluate this code and describe the result. Presumably the analyst’s intent was to get the data for Rwanda and Afghanistan. Did they succeed? Why or why not? If not, what is the correct way to do this?

``` r
#no they were not successful. 

filter(gapminder, country == c("Rwanda", "Afghanistan"))
```

    ## # A tibble: 12 x 6
    ##    country     continent  year lifeExp      pop gdpPercap
    ##    <fctr>      <fctr>    <int>   <dbl>    <int>     <dbl>
    ##  1 Afghanistan Asia       1957    30.3  9240934       821
    ##  2 Afghanistan Asia       1967    34.0 11537966       836
    ##  3 Afghanistan Asia       1977    38.4 14880372       786
    ##  4 Afghanistan Asia       1987    40.8 13867957       852
    ##  5 Afghanistan Asia       1997    41.8 22227415       635
    ##  6 Afghanistan Asia       2007    43.8 31889923       975
    ##  7 Rwanda      Africa     1952    40.0  2534927       493
    ##  8 Rwanda      Africa     1962    43.0  3051242       597
    ##  9 Rwanda      Africa     1972    44.6  3992121       591
    ## 10 Rwanda      Africa     1982    46.2  5507565       882
    ## 11 Rwanda      Africa     1992    23.6  7290203       737
    ## 12 Rwanda      Africa     2002    43.4  7852401       786

``` r
#looking at the data that results from this code, the analyst's code returns 12 rows of data (8 for Rwanda, 8 for Afghanistan). 
#when I run the code below: 

gapminder %>% 
  filter (country =="Rwanda" | country == "Afghanistan")
```

    ## # A tibble: 24 x 6
    ##    country     continent  year lifeExp      pop gdpPercap
    ##    <fctr>      <fctr>    <int>   <dbl>    <int>     <dbl>
    ##  1 Afghanistan Asia       1952    28.8  8425333       779
    ##  2 Afghanistan Asia       1957    30.3  9240934       821
    ##  3 Afghanistan Asia       1962    32.0 10267083       853
    ##  4 Afghanistan Asia       1967    34.0 11537966       836
    ##  5 Afghanistan Asia       1972    36.1 13079460       740
    ##  6 Afghanistan Asia       1977    38.4 14880372       786
    ##  7 Afghanistan Asia       1982    39.9 12881816       978
    ##  8 Afghanistan Asia       1987    40.8 13867957       852
    ##  9 Afghanistan Asia       1992    41.7 16317921       649
    ## 10 Afghanistan Asia       1997    41.8 22227415       635
    ## # ... with 14 more rows

``` r
#I get 24 rows of data. It appears that somehow, by concatenating the countries he wanted to collect data for, the analyst ommitted half of the rows. 

#why?
#When we use the combine function it will go row by row through the different countries
#it will compare row1 with "Rwanda"
#then it will compare row2 with "Afghanistan"
#Then it will start over and compare row 3 == "Rwanda", and if row 4 =="Afghanistan", etc. 
#If the result is TRUE, then it will add it to the tibble. 
#However, this means rows containing "Rwanda" will return FALSE if the code is currently comparing to "Afghanistan" and vice versa

#To test if this explanation is true, if I run the code below, I should obtain 8 rows with values for Rwanda, but only 4 for Afghanistan (note - this is only applicable for this dataset, as I know there are equal rows for Rwanda and Afghanistan, organized alphabetically. The result would be different for another dataset). 

filter(gapminder, country == c("Rwanda", "Afghanistan", "Rwanda"))
```

    ## # A tibble: 12 x 6
    ##    country     continent  year lifeExp      pop gdpPercap
    ##    <fctr>      <fctr>    <int>   <dbl>    <int>     <dbl>
    ##  1 Afghanistan Asia       1957    30.3  9240934       821
    ##  2 Afghanistan Asia       1972    36.1 13079460       740
    ##  3 Afghanistan Asia       1987    40.8 13867957       852
    ##  4 Afghanistan Asia       2002    42.1 25268405       727
    ##  5 Rwanda      Africa     1952    40.0  2534927       493
    ##  6 Rwanda      Africa     1962    43.0  3051242       597
    ##  7 Rwanda      Africa     1967    44.1  3451079       511
    ##  8 Rwanda      Africa     1977    45.0  4657072       670
    ##  9 Rwanda      Africa     1982    46.2  5507565       882
    ## 10 Rwanda      Africa     1992    23.6  7290203       737
    ## 11 Rwanda      Africa     1997    36.1  7212583       590
    ## 12 Rwanda      Africa     2007    46.2  8860588       863

``` r
## Interestingly, I noticed that the length of the combined list must be divisible into the number of rows in the dataframe. 
#If I try to run the code below, it will return an error. 

#filter(gapminder, country == c("Rwanda", "Afghanistan", "Norway", "China", "Japan")) 

#The reason for this is because it must be able to fully cycle through the combined list, we cannot divide 5 into the number of rows of data in gapminder. 


#conclude: 
#a correct way to run the code is: 
gapminder %>% 
  filter (country =="Rwanda" | country == "Afghanistan")
```

    ## # A tibble: 24 x 6
    ##    country     continent  year lifeExp      pop gdpPercap
    ##    <fctr>      <fctr>    <int>   <dbl>    <int>     <dbl>
    ##  1 Afghanistan Asia       1952    28.8  8425333       779
    ##  2 Afghanistan Asia       1957    30.3  9240934       821
    ##  3 Afghanistan Asia       1962    32.0 10267083       853
    ##  4 Afghanistan Asia       1967    34.0 11537966       836
    ##  5 Afghanistan Asia       1972    36.1 13079460       740
    ##  6 Afghanistan Asia       1977    38.4 14880372       786
    ##  7 Afghanistan Asia       1982    39.9 12881816       978
    ##  8 Afghanistan Asia       1987    40.8 13867957       852
    ##  9 Afghanistan Asia       1992    41.7 16317921       649
    ## 10 Afghanistan Asia       1997    41.8 22227415       635
    ## # ... with 14 more rows
