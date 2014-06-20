---
title       : User's Data Analysis
subtitle    : An R app for analysis of small numeric data set   
author      : James
job         : Analyst
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides

---
## About This App

1. Designed for analysis of user-generated data 
2. Powerful presentation using R 
3. Statistical analysis including t-test and ANOVA

--- 
## How to Use This App
1.  Upload your data
    * Selelct a data file using "Choose File" button
    * Select the "Header" checkbox if the file has headers
    * Check appropriate "separator" and "Qoute" radiobuttons 
   
   => Your raw data will appear on the "My Data" tab on the right-hand side
      To view the data, click on the "My Data" tab
   
2.  To select the plot, choose a plot type using the dropdown button in the "2.  Select the plot type".  
    * To view the plot, click on the "Presentation" tab on the right
    
3.  For statistical analysis select a test type using the dropdown button in "3. Select Statistical Analysis to be performed"
    * To view the result, click on the "Stat Test" tab

---
## Sample Data - Generate a data 
Use R to generate random numbers and a data frame as following:

```r
library(reshape)
```

```
## Loading required package: plyr
## 
## Attaching package: 'reshape'
## 
## The following objects are masked from 'package:plyr':
## 
##     rename, round_any
```

```r
P <- round(rnorm(25, 8, 2.5), 2)
A <- round(rnorm(25, 10, 3), 2)
B <- round(rnorm(25, 11, 3.5), 2)
AB <- round(rnorm(25, 14, 3.5), 2)
combo <- data.frame(P, A, B, AB)
write.csv(combo, "combo.csv", row.names = FALSE)
melted <- melt(combo)
```

```
## Using  as id variables
```

* "combo.csv" would be found in your R woring directory.  After you click the "Choose File" button, you have to go to this working directory to find the file.

---
## Sample "Presentation" Tab - Default; boxplot

```
##        P               A               B               AB       
##  Min.   : 1.37   Min.   : 4.61   Min.   : 2.86   Min.   : 5.34  
##  1st Qu.: 6.38   1st Qu.: 7.39   1st Qu.: 8.14   1st Qu.:11.14  
##  Median : 7.41   Median :11.26   Median :10.89   Median :14.33  
##  Mean   : 7.85   Mean   :10.51   Mean   :10.64   Mean   :14.40  
##  3rd Qu.: 9.28   3rd Qu.:13.11   3rd Qu.:13.10   3rd Qu.:17.20  
##  Max.   :14.46   Max.   :15.68   Max.   :17.16   Max.   :21.50
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3.png) 


---
## Sample "Stat Test" Tab - Default; t-test



```
## 
## 	Pairwise comparisons using t tests with pooled SD 
## 
## data:  melted$value and melted$variable 
## 
##    P       A       B      
## A  0.01369 -       -      
## B  0.01369 0.89497 -      
## AB 4.9e-09 0.00052 0.00068
## 
## P value adjustment method: holm
```

