STAT545\_hw02\_JLB
================

STAT 545 Homework 2
===================

The different sections of this homework are broken down into the sections outlined in [the homework instructions](http://stat545.com/Classroom/assignments/hw02/hw02.html):

**Homework 2 Task list: **

1.  \[x\] Getting Started: Install Gapminder & dyplyr
2.  \[ \]Smell test the data: Explore the gapminder object
3.  \[ \]Explore individual variables:
4.  \[ \]Explore various plot types:
5.  \[ \]Extra exercise:
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

**2a. Is it a dataframe, matrix, vector, list?** The typeof() function will tell me what data types gapminder contains. The class() function will tell me the class of the object gapminder.

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

**5. Can you get these facts about “extent” or “size” in more than one way? Can you imagine different functions being useful in different contexts?** I found additional information on how to further explore gapminder [here](http://adv-r.had.co.nz/Data-structures.html)

``` r
?gapminder
length(gapminder) 
```

    ## [1] 6

``` r
attributes(gapminder)
```

    ## $names
    ## [1] "country"   "continent" "year"      "lifeExp"   "pop"       "gdpPercap"
    ## 
    ## $class
    ## [1] "tbl_df"     "tbl"        "data.frame"
    ## 
    ## $row.names
    ##    [1]    1    2    3    4    5    6    7    8    9   10   11   12   13
    ##   [14]   14   15   16   17   18   19   20   21   22   23   24   25   26
    ##   [27]   27   28   29   30   31   32   33   34   35   36   37   38   39
    ##   [40]   40   41   42   43   44   45   46   47   48   49   50   51   52
    ##   [53]   53   54   55   56   57   58   59   60   61   62   63   64   65
    ##   [66]   66   67   68   69   70   71   72   73   74   75   76   77   78
    ##   [79]   79   80   81   82   83   84   85   86   87   88   89   90   91
    ##   [92]   92   93   94   95   96   97   98   99  100  101  102  103  104
    ##  [105]  105  106  107  108  109  110  111  112  113  114  115  116  117
    ##  [118]  118  119  120  121  122  123  124  125  126  127  128  129  130
    ##  [131]  131  132  133  134  135  136  137  138  139  140  141  142  143
    ##  [144]  144  145  146  147  148  149  150  151  152  153  154  155  156
    ##  [157]  157  158  159  160  161  162  163  164  165  166  167  168  169
    ##  [170]  170  171  172  173  174  175  176  177  178  179  180  181  182
    ##  [183]  183  184  185  186  187  188  189  190  191  192  193  194  195
    ##  [196]  196  197  198  199  200  201  202  203  204  205  206  207  208
    ##  [209]  209  210  211  212  213  214  215  216  217  218  219  220  221
    ##  [222]  222  223  224  225  226  227  228  229  230  231  232  233  234
    ##  [235]  235  236  237  238  239  240  241  242  243  244  245  246  247
    ##  [248]  248  249  250  251  252  253  254  255  256  257  258  259  260
    ##  [261]  261  262  263  264  265  266  267  268  269  270  271  272  273
    ##  [274]  274  275  276  277  278  279  280  281  282  283  284  285  286
    ##  [287]  287  288  289  290  291  292  293  294  295  296  297  298  299
    ##  [300]  300  301  302  303  304  305  306  307  308  309  310  311  312
    ##  [313]  313  314  315  316  317  318  319  320  321  322  323  324  325
    ##  [326]  326  327  328  329  330  331  332  333  334  335  336  337  338
    ##  [339]  339  340  341  342  343  344  345  346  347  348  349  350  351
    ##  [352]  352  353  354  355  356  357  358  359  360  361  362  363  364
    ##  [365]  365  366  367  368  369  370  371  372  373  374  375  376  377
    ##  [378]  378  379  380  381  382  383  384  385  386  387  388  389  390
    ##  [391]  391  392  393  394  395  396  397  398  399  400  401  402  403
    ##  [404]  404  405  406  407  408  409  410  411  412  413  414  415  416
    ##  [417]  417  418  419  420  421  422  423  424  425  426  427  428  429
    ##  [430]  430  431  432  433  434  435  436  437  438  439  440  441  442
    ##  [443]  443  444  445  446  447  448  449  450  451  452  453  454  455
    ##  [456]  456  457  458  459  460  461  462  463  464  465  466  467  468
    ##  [469]  469  470  471  472  473  474  475  476  477  478  479  480  481
    ##  [482]  482  483  484  485  486  487  488  489  490  491  492  493  494
    ##  [495]  495  496  497  498  499  500  501  502  503  504  505  506  507
    ##  [508]  508  509  510  511  512  513  514  515  516  517  518  519  520
    ##  [521]  521  522  523  524  525  526  527  528  529  530  531  532  533
    ##  [534]  534  535  536  537  538  539  540  541  542  543  544  545  546
    ##  [547]  547  548  549  550  551  552  553  554  555  556  557  558  559
    ##  [560]  560  561  562  563  564  565  566  567  568  569  570  571  572
    ##  [573]  573  574  575  576  577  578  579  580  581  582  583  584  585
    ##  [586]  586  587  588  589  590  591  592  593  594  595  596  597  598
    ##  [599]  599  600  601  602  603  604  605  606  607  608  609  610  611
    ##  [612]  612  613  614  615  616  617  618  619  620  621  622  623  624
    ##  [625]  625  626  627  628  629  630  631  632  633  634  635  636  637
    ##  [638]  638  639  640  641  642  643  644  645  646  647  648  649  650
    ##  [651]  651  652  653  654  655  656  657  658  659  660  661  662  663
    ##  [664]  664  665  666  667  668  669  670  671  672  673  674  675  676
    ##  [677]  677  678  679  680  681  682  683  684  685  686  687  688  689
    ##  [690]  690  691  692  693  694  695  696  697  698  699  700  701  702
    ##  [703]  703  704  705  706  707  708  709  710  711  712  713  714  715
    ##  [716]  716  717  718  719  720  721  722  723  724  725  726  727  728
    ##  [729]  729  730  731  732  733  734  735  736  737  738  739  740  741
    ##  [742]  742  743  744  745  746  747  748  749  750  751  752  753  754
    ##  [755]  755  756  757  758  759  760  761  762  763  764  765  766  767
    ##  [768]  768  769  770  771  772  773  774  775  776  777  778  779  780
    ##  [781]  781  782  783  784  785  786  787  788  789  790  791  792  793
    ##  [794]  794  795  796  797  798  799  800  801  802  803  804  805  806
    ##  [807]  807  808  809  810  811  812  813  814  815  816  817  818  819
    ##  [820]  820  821  822  823  824  825  826  827  828  829  830  831  832
    ##  [833]  833  834  835  836  837  838  839  840  841  842  843  844  845
    ##  [846]  846  847  848  849  850  851  852  853  854  855  856  857  858
    ##  [859]  859  860  861  862  863  864  865  866  867  868  869  870  871
    ##  [872]  872  873  874  875  876  877  878  879  880  881  882  883  884
    ##  [885]  885  886  887  888  889  890  891  892  893  894  895  896  897
    ##  [898]  898  899  900  901  902  903  904  905  906  907  908  909  910
    ##  [911]  911  912  913  914  915  916  917  918  919  920  921  922  923
    ##  [924]  924  925  926  927  928  929  930  931  932  933  934  935  936
    ##  [937]  937  938  939  940  941  942  943  944  945  946  947  948  949
    ##  [950]  950  951  952  953  954  955  956  957  958  959  960  961  962
    ##  [963]  963  964  965  966  967  968  969  970  971  972  973  974  975
    ##  [976]  976  977  978  979  980  981  982  983  984  985  986  987  988
    ##  [989]  989  990  991  992  993  994  995  996  997  998  999 1000 1001
    ## [1002] 1002 1003 1004 1005 1006 1007 1008 1009 1010 1011 1012 1013 1014
    ## [1015] 1015 1016 1017 1018 1019 1020 1021 1022 1023 1024 1025 1026 1027
    ## [1028] 1028 1029 1030 1031 1032 1033 1034 1035 1036 1037 1038 1039 1040
    ## [1041] 1041 1042 1043 1044 1045 1046 1047 1048 1049 1050 1051 1052 1053
    ## [1054] 1054 1055 1056 1057 1058 1059 1060 1061 1062 1063 1064 1065 1066
    ## [1067] 1067 1068 1069 1070 1071 1072 1073 1074 1075 1076 1077 1078 1079
    ## [1080] 1080 1081 1082 1083 1084 1085 1086 1087 1088 1089 1090 1091 1092
    ## [1093] 1093 1094 1095 1096 1097 1098 1099 1100 1101 1102 1103 1104 1105
    ## [1106] 1106 1107 1108 1109 1110 1111 1112 1113 1114 1115 1116 1117 1118
    ## [1119] 1119 1120 1121 1122 1123 1124 1125 1126 1127 1128 1129 1130 1131
    ## [1132] 1132 1133 1134 1135 1136 1137 1138 1139 1140 1141 1142 1143 1144
    ## [1145] 1145 1146 1147 1148 1149 1150 1151 1152 1153 1154 1155 1156 1157
    ## [1158] 1158 1159 1160 1161 1162 1163 1164 1165 1166 1167 1168 1169 1170
    ## [1171] 1171 1172 1173 1174 1175 1176 1177 1178 1179 1180 1181 1182 1183
    ## [1184] 1184 1185 1186 1187 1188 1189 1190 1191 1192 1193 1194 1195 1196
    ## [1197] 1197 1198 1199 1200 1201 1202 1203 1204 1205 1206 1207 1208 1209
    ## [1210] 1210 1211 1212 1213 1214 1215 1216 1217 1218 1219 1220 1221 1222
    ## [1223] 1223 1224 1225 1226 1227 1228 1229 1230 1231 1232 1233 1234 1235
    ## [1236] 1236 1237 1238 1239 1240 1241 1242 1243 1244 1245 1246 1247 1248
    ## [1249] 1249 1250 1251 1252 1253 1254 1255 1256 1257 1258 1259 1260 1261
    ## [1262] 1262 1263 1264 1265 1266 1267 1268 1269 1270 1271 1272 1273 1274
    ## [1275] 1275 1276 1277 1278 1279 1280 1281 1282 1283 1284 1285 1286 1287
    ## [1288] 1288 1289 1290 1291 1292 1293 1294 1295 1296 1297 1298 1299 1300
    ## [1301] 1301 1302 1303 1304 1305 1306 1307 1308 1309 1310 1311 1312 1313
    ## [1314] 1314 1315 1316 1317 1318 1319 1320 1321 1322 1323 1324 1325 1326
    ## [1327] 1327 1328 1329 1330 1331 1332 1333 1334 1335 1336 1337 1338 1339
    ## [1340] 1340 1341 1342 1343 1344 1345 1346 1347 1348 1349 1350 1351 1352
    ## [1353] 1353 1354 1355 1356 1357 1358 1359 1360 1361 1362 1363 1364 1365
    ## [1366] 1366 1367 1368 1369 1370 1371 1372 1373 1374 1375 1376 1377 1378
    ## [1379] 1379 1380 1381 1382 1383 1384 1385 1386 1387 1388 1389 1390 1391
    ## [1392] 1392 1393 1394 1395 1396 1397 1398 1399 1400 1401 1402 1403 1404
    ## [1405] 1405 1406 1407 1408 1409 1410 1411 1412 1413 1414 1415 1416 1417
    ## [1418] 1418 1419 1420 1421 1422 1423 1424 1425 1426 1427 1428 1429 1430
    ## [1431] 1431 1432 1433 1434 1435 1436 1437 1438 1439 1440 1441 1442 1443
    ## [1444] 1444 1445 1446 1447 1448 1449 1450 1451 1452 1453 1454 1455 1456
    ## [1457] 1457 1458 1459 1460 1461 1462 1463 1464 1465 1466 1467 1468 1469
    ## [1470] 1470 1471 1472 1473 1474 1475 1476 1477 1478 1479 1480 1481 1482
    ## [1483] 1483 1484 1485 1486 1487 1488 1489 1490 1491 1492 1493 1494 1495
    ## [1496] 1496 1497 1498 1499 1500 1501 1502 1503 1504 1505 1506 1507 1508
    ## [1509] 1509 1510 1511 1512 1513 1514 1515 1516 1517 1518 1519 1520 1521
    ## [1522] 1522 1523 1524 1525 1526 1527 1528 1529 1530 1531 1532 1533 1534
    ## [1535] 1535 1536 1537 1538 1539 1540 1541 1542 1543 1544 1545 1546 1547
    ## [1548] 1548 1549 1550 1551 1552 1553 1554 1555 1556 1557 1558 1559 1560
    ## [1561] 1561 1562 1563 1564 1565 1566 1567 1568 1569 1570 1571 1572 1573
    ## [1574] 1574 1575 1576 1577 1578 1579 1580 1581 1582 1583 1584 1585 1586
    ## [1587] 1587 1588 1589 1590 1591 1592 1593 1594 1595 1596 1597 1598 1599
    ## [1600] 1600 1601 1602 1603 1604 1605 1606 1607 1608 1609 1610 1611 1612
    ## [1613] 1613 1614 1615 1616 1617 1618 1619 1620 1621 1622 1623 1624 1625
    ## [1626] 1626 1627 1628 1629 1630 1631 1632 1633 1634 1635 1636 1637 1638
    ## [1639] 1639 1640 1641 1642 1643 1644 1645 1646 1647 1648 1649 1650 1651
    ## [1652] 1652 1653 1654 1655 1656 1657 1658 1659 1660 1661 1662 1663 1664
    ## [1665] 1665 1666 1667 1668 1669 1670 1671 1672 1673 1674 1675 1676 1677
    ## [1678] 1678 1679 1680 1681 1682 1683 1684 1685 1686 1687 1688 1689 1690
    ## [1691] 1691 1692 1693 1694 1695 1696 1697 1698 1699 1700 1701 1702 1703
    ## [1704] 1704

Conclusion:

1.  using ?gapminder is another quick way to get information about gapminder including: the format, the names and types of variables inside the object, and specific descriptions of each variable. context: This function would be useful for getting a quick overview of the object, as well as in the context of needing help with understanding the data and where it comes from.

2.  Using length(gapminder) will return how many elements are inside it, in this case, returns the number of variables. Another application of the length() function would become useful when looking at the length of variables such as an array. This function would also be useful for creating a loop that repeats for each value within a variable.

3.  the attributes(gapminder) function is similar to the summary(), but it gives information about the row names as well. In this context the row names are simply numbers 1, 2, 3, etc..., but in other contexts these names may be more useful.

**What data type is each variable?** using the str() function allows us to look at the structure of the variables

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

#### Explore individual variables

#### Exploring the year variable:

I can look at the range of years contained in the data: The min() function shows the earliest year, while the max() function shows the latest year. The range() function gives both min and max as an output (ie, the range of the years).

``` r
min(gapminder$year)
```

    ## [1] 1952

``` r
max(gapminder$year)
```

    ## [1] 2007

``` r
range(gapminder$year)
```

    ## [1] 1952 2007

**Conclusion:** the range of years in the gapminder dataset is 1952-2007.

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
