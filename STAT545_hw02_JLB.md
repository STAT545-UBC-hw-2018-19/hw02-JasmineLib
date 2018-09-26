STAT545\_hw02\_JLB
================

STAT 545 Homework 2
===================

The different sections of this homework are broken down into the sections outlined in [the homework instructions](http://stat545.com/Classroom/assignments/hw02/hw02.html):

**Homework 2 Task list: **

1.  Getting Started: Install Gapminder & dyplyr
2.  Smell test the data: Explore the gapminder object
3.  Explore individual variables
4.  Explore various plot types
5.  Extra exercise
6.  Conclusions and Reflection

Something useful: A [guide](https://ggplot2.tidyverse.org/reference/annotation_logticks.html) to changing tick marks on axes when plotting graphs.

### 1. Getting Started:

Install/Load Gapminder and dyplyr (through the tidyverse package)

``` r
library(gapminder)
library(tidyverse)
```

### 2. Smell test the data:

Explore the gapminder object:

**2a. Is it a dataframe, matrix, vector, list?**
The typeof() function will tell me what data types gapminder contains.
The class() function will tell me the class of the object gapminder.

``` r
typeof(gapminder)
```

    ## [1] "list"

``` r
class(gapminder)
```

    ## [1] "tbl_df"     "tbl"        "data.frame"

Conclusion:
- Gapminder is a data frame that contains list data.

**2b. What is its class?**
As shown above, we can use the class() function to determine the class of the gapminder object:

``` r
(class(gapminder))
```

    ## [1] "tbl_df"     "tbl"        "data.frame"

Conclusion:
- The class of gapminder is a data frame, specifically, a tibble (which we have not yet explored in class)

**2c. How many columns/variables?**

``` r
(ncol(gapminder))
```

    ## [1] 6

Conclusion:
- There are 6 variables in gapminder.

**2d. How many rows/observations?**

``` r
(nrow(gapminder))
```

    ## [1] 1704

Conclusion:
- There are 1704 observations in gapminder.

**2e Can you get these facts about “extent” or “size” in more than one way? Can you imagine different functions being useful in different contexts?**
I found additional information on how to further explore gapminder [here](http://adv-r.had.co.nz/Data-structures.html)

``` r
dim(gapminder) #returns the number of rows and columns, respectively.
```

    ## [1] 1704    6

``` r
length(gapminder) #returns the number of columns
```

    ## [1] 6

``` r
levels(gapminder$continent) #returns the groups in a particular variable
```

    ## [1] "Africa"   "Americas" "Asia"     "Europe"   "Oceania"

Conclusion:
- using ?gapminder in the console is another way to get information about gapminder such as format, names and types of variables in the object, and specific descriptions of each variable.
context: This function is useful for getting a quick overview and understanding the data and where it comes from.
- length(gapminder) returns the number of elements inside it. The length() function might be used to make a loop that repeats for each value in the array.
- the levels(), attributes(), and summary() functions can provide useful information about the variables inside a dataset, as well as basic statistical information about these.

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

Conclusion:
The variables in gapminder are lists containing different datatypes:
- country - factors
- continent - factors
- year - integers
- lifeExp - numbers
- pop - integers
- gdpPercap - numbers

#### 3. Explore individual variables

Categorical variable selected: continent
Quantitative variable selected: gdpPercap

**3a. Exploring possible values (or range, whichever is appropriate) of variables:**

``` r
min(gapminder$gdpPercap) #returns minimum value of gdpPercap
```

    ## [1] 241.1659

``` r
max(gapminder$gdpPercap) #returns maximum value of gdpPercap
```

    ## [1] 113523.1

``` r
range(gapminder$gdpPercap) #returns the range lowest and highest values of gdpPercap
```

    ## [1]    241.1659 113523.1329

``` r
levels(gapminder$continent)#returns the groups or levels contained in the continent variable
```

    ## [1] "Africa"   "Americas" "Asia"     "Europe"   "Oceania"

Conclusion:
- The range of GDP per capita in the gapminder dataset is $241-113 523.
- The possible values of the continent variable are: Africa, Americas, Asia, Europe, and Oceania. - By inspection, the range of values contained in GDP per capita and the possible values contained in the continent variable seem appropriate.

#### 4. Explore various plot types

**4a. A scatterplot of two quantitative variables.**

I will compare population growth in Canada and the United States from 1952-2007.

``` r
gapminder_CAN_USA = gapminder %>% 
  filter(country == "Canada"|country == "United States")
  
  ggplot(gapminder_CAN_USA, aes(x=year, y=pop)) + 
  geom_point() +
  geom_line(aes(colour = country)) +
  xlab("Year") +
  ylab("Population of Canada and United States") +
  ggtitle("North American Population Trends")
```

https://github.com/STAT545-UBC-students/hw02-JasmineLib/blob/master/ggPlot%20Figures/Scatterplot%20Canada%20USA%20Population-1.png?raw=true

![plot](https://github.com/STAT545-UBC-students/hw02-JasmineLib/blob/master/ggPlot%20Figures/Scatterplot%20Canada%20USA%20Population-1.png?raw=true)

I will compare GDP per Capita in Canada and the United States from 1952-2007.

``` r
  ggplot(gapminder_CAN_USA,aes(x=year, y = gdpPercap)) +
  geom_line(aes(group = country, colour = country)) +
  geom_point() +
  xlab("Year") +
  ylab("GDP Per Capita") +
  ggtitle("North American GDP Per Capita Trends")
```

![](STAT545_hw02_JLB_files/figure-markdown_github/Scatterplot%20Canada%20USA%20GDP%20per%20Capita-1.png)

**4b. A plot of one quantitative variable.**

I will make a histogram of GDP per capita in 2007. I will first assign the filtered gapminder dataframe for the year 2007, as I will use this for subsequent plots.

``` r
gapminder_2007 = gapminder %>%
  filter (year == "2007")

  ggplot(gapminder_2007, aes(gdpPercap)) +
  geom_histogram(aes(y=..density..), bins = 35, fill = "royalblue1", colour = "royalblue4") + 
  geom_density(fill = "skyblue1", alpha = 0.2) +
  scale_x_log10(labels = scales::trans_format("log10", scales::math_format(10^.x))) + #the labels = scales details makes for nicer x-axis ticks. 
  xlab("GDP Per Capita") +
  ylab("Density") +
  ggtitle("Histogram of GDP Per Capita in 2007")
```

![](STAT545_hw02_JLB_files/figure-markdown_github/Histogram%20Plot%20GDP%20per%20Capita%202007-1.png)

**4c. A plot of one quantitative variable and one categorical.**

I will plot the gdp per capita of various continents in 2007.

``` r
  ggplot(gapminder_2007, aes(continent, gdpPercap)) +
  scale_y_log10(labels = scales::trans_format("log10", scales::math_format(10^.x))) +
  geom_violin(fill = "darkslategray1", alpha = 0.5) +
  geom_jitter(alpha = 0.33) +
  xlab("Continent")+
  ylab("GDP Per Capita") +
  ggtitle("GDP Per Capita by Continent in 2007")
```

![](STAT545_hw02_JLB_files/figure-markdown_github/GDP%20per%20capita%20by%20continent%20in%202007-1.png)

**4d. Exploring other dyplr functions beyond filter() and select()**

**The mutate() function:**

The mutate function can be used to create a new variable by making changes to existing data.
Here I will multiply the GDP per capita by the population to examine the GDP of countries, organized by continent.

``` r
gapminder_2007 %>% 
  mutate(GDP = gdpPercap * pop) %>% 
  ggplot(aes(continent, GDP)) +
  geom_boxplot() +
  geom_jitter(alpha = 0.2) +
  scale_y_log10(breaks = scales::trans_breaks("log10", function(x) 10^x),
   labels = scales::trans_format("log10", scales::math_format(10^.x))) +
  ylab("Gross Domestic Product") +
  xlab("Continent") +
  ggtitle("GDP in 2007 by Continent")
```

![](STAT545_hw02_JLB_files/figure-markdown_github/GDP%20by%20Continent%20in%202007-1.png)

**The between() function: **

The between() function selects for values of a variable between two assigned values.
Here I will look at the countries with a GDP Per capita between two values for the year 2007.

``` r
gapminder_2007 %>% 
  filter (between(gdpPercap, 30000,50000) ) %>% 
  ggplot(aes(gdpPercap)) + geom_histogram(aes(fill = continent), bins = 10) +
  facet_wrap(~continent)+
  ylab("Count") +
  xlab("GDP per capita") +
  ggtitle("Countries with GDP per capita between 30 and 50k")
```

![](STAT545_hw02_JLB_files/figure-markdown_github/Countries%20with%20GDP%20per%20Capita%20between%2030%20and%2050k-1.png)

**The top\_n() function **

The top\_n() function can be used to select the top (or bottom) values in a data set. Here I will show two tibbles showing the countries with the lowest and highest GDP per capita in 2007.

``` r
#Table showing the 5 countries with the lowest GDP per capita in 2007, in ascending order. 
gapminder_2007 %>% 
  select (country, gdpPercap) %>% 
  top_n (-5) %>% 
  arrange(gdpPercap)
```

    ## Selecting by gdpPercap

    ## # A tibble: 5 x 2
    ##   country          gdpPercap
    ##   <fctr>               <dbl>
    ## 1 Congo, Dem. Rep.       278
    ## 2 Liberia                415
    ## 3 Burundi                430
    ## 4 Zimbabwe               470
    ## 5 Guinea-Bissau          579

``` r
#Table showing the 5 countries with highest GDP per capita in 2007 in ascending order
gapminder_2007 %>% 
  select (country, gdpPercap) %>% 
  top_n (5) %>% 
  arrange(gdpPercap)
```

    ## Selecting by gdpPercap

    ## # A tibble: 5 x 2
    ##   country       gdpPercap
    ##   <fctr>            <dbl>
    ## 1 Ireland           40676
    ## 2 United States     42952
    ## 3 Singapore         47143
    ## 4 Kuwait            47307
    ## 5 Norway            49357

#### 5. Extra Exercise:

Instructions: Evaluate this code and describe the result. Presumably the analyst’s intent was to get the data for Rwanda and Afghanistan. Did they succeed? Why or why not? If not, what is the correct way to do this?

Result: No the analyst was not successful.

``` r
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
#looking at the output, the analyst's code returns 12 rows of data (6 for Rwanda, 6 for Afghanistan).   
#However, when I run the code below I get 24 rows of data.

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

When the analyst used c(), they ommitted half of the rows.
Why?
When we use c(), the code it will go row by row through the different countries it will compare row1 with "Rwanda".
Next, it will compare row2 with "Afghanistan".
It will then start over and evaluate row 3 == "Rwanda", and row 4 =="Afghanistan", etc.
If the result is TRUE, it will add it to the tibble.
Therefore, when comparing to "Rwanda" it will return FALSE if the row contains "Afghanistan" and vice versa

To test if the above explanation is correct:

If I run the code below, I should obtain 8 rows with values for Rwanda, but only 4 for Afghanistan
**Note** - this is only applicable for this dataset, as I know there are equal numbers of rows for Rwanda and Afghanistan, and I know they are organized alphabetically.

``` r
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

Interestingly, If I run the code shown below, it returns a warning.

``` r
filter(gapminder, country == c("Rwanda", "Afghanistan", "Norway", "China", "Japan")) 
```

    ## Warning in is.na(e1) | is.na(e2): longer object length is not a multiple of
    ## shorter object length

    ## Warning in `==.default`(country, c("Rwanda", "Afghanistan", "Norway",
    ## "China", : longer object length is not a multiple of shorter object length

    ## # A tibble: 13 x 6
    ##    country     continent  year lifeExp        pop gdpPercap
    ##    <fctr>      <fctr>    <int>   <dbl>      <int>     <dbl>
    ##  1 Afghanistan Asia       1957    30.3    9240934       821
    ##  2 Afghanistan Asia       1982    39.9   12881816       978
    ##  3 Afghanistan Asia       2007    43.8   31889923       975
    ##  4 China       Asia       1952    44.0  556263527       400
    ##  5 China       Asia       1977    64.0  943455000       741
    ##  6 China       Asia       2002    72.0 1280400000      3119
    ##  7 Japan       Asia       1962    68.7   95831757      6577
    ##  8 Japan       Asia       1987    78.7  122091325     22376
    ##  9 Norway      Europe     1962    73.5    3638919     13450
    ## 10 Norway      Europe     1987    75.9    4186147     31541
    ## 11 Rwanda      Africa     1957    41.5    2822082       540
    ## 12 Rwanda      Africa     1982    46.2    5507565       882
    ## 13 Rwanda      Africa     2007    46.2    8860588       863

The reason for the warning is because the list of countries is not fully cycled through, as we cannot divide 5 into the number of rows of data in gapminder.

Conclusion:
- A correct way to filter the data without accidentally leaving out rows of data is shown below:

``` r
gapminder %>% 
  filter (country =="Rwanda" | country == "Afghanistan")
```
