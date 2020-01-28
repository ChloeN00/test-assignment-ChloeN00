Test statistical assignment
================
Chloe Neal
26 January 2020

## Introduction

Please change the author and date fields above as appropriate. Do not
change the output format. Once you have completed the assignment you
want to knit your document into a markdown document in the
“github\_document” format and then commit both the .Rmd and .md files
(and all the associated files with graphs) to your private assignment
repository on Github.

## Reading data (40 points)

First, we need to read the data into R. For this assignment, I ask you
to use data from the youth self-completion questionnaire (completed by
children between 10 and 15 years old) from Wave 9 of the Understanding
Society. It is one of the files you have downloaded as part of SN6614
from the UK Data Service. To help you find and understand this file you
will need the following documents:

1)  The Understanding Society Waves 1-9 User Guide:
    <https://www.understandingsociety.ac.uk/sites/default/files/downloads/documentation/mainstage/user-guides/mainstage-user-guide.pdf>
2)  The youth self-completion questionnaire from Wave 9:
    <https://www.understandingsociety.ac.uk/sites/default/files/downloads/documentation/mainstage/questionnaire/wave-9/w9-gb-youth-self-completion-questionnaire.pdf>
3)  The codebook for the file:
    <https://www.understandingsociety.ac.uk/documentation/mainstage/dataset-documentation/datafile/youth/wave/9>

<!-- end list -->

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────────────────────────────── tidyverse 1.3.0 ──

    ## ✓ ggplot2 3.2.1     ✓ purrr   0.3.3
    ## ✓ tibble  2.1.3     ✓ dplyr   0.8.3
    ## ✓ tidyr   1.0.0     ✓ stringr 1.4.0
    ## ✓ readr   1.3.1     ✓ forcats 0.4.0

    ## ── Conflicts ────────────────────────────────────────────────────────────────── tidyverse_conflicts() ──
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
# This attaches the tidyverse package. If you get an error here you need to install the package first. 
Data <- read_tsv("/Users/chloeneal/Data Analysis 3/test-assignment-ChloeN00/UKDA-6614-tab/tab/ukhls_w9/i_youth.tab")
```

    ## Parsed with column specification:
    ## cols(
    ##   .default = col_double()
    ## )

    ## See spec(...) for full column specifications.

``` r
# You need to add between the quotation marks a full path to the required file on your computer.
Data
```

    ## # A tibble: 2,821 x 216
    ##      pidp   pid i_hidp i_pno i_hhorig i_memorig i_psu i_strata i_sampst i_ivfio
    ##     <dbl> <dbl>  <dbl> <dbl>    <dbl>     <dbl> <dbl>    <dbl>    <dbl>   <dbl>
    ##  1 6.80e7    -8 6.82e7     4        1         1  2084     2042        1      21
    ##  2 6.80e7    -8 6.82e7     3        1         1  2084     2042        1      21
    ##  3 6.80e7    -8 6.82e7     3        1         1  2084     2042        1      21
    ##  4 6.81e7    -8 6.83e7     4        1         1  2108     2054        1      21
    ##  5 6.81e7    -8 6.83e7     3        1         1  2108     2054        1      21
    ##  6 6.81e7    -8 6.83e7     3        1         1  2132     2066        1      21
    ##  7 6.81e7    -8 6.86e7     5        1         1  2276     2138        1      21
    ##  8 6.82e7    -8 6.88e7     4        1         1  2348     2174        1      21
    ##  9 6.82e7    -8 6.88e7     2        1         1  2372     2186        1      21
    ## 10 6.82e7    -8 6.88e7     5        1         1  2396     2198        1      21
    ## # … with 2,811 more rows, and 206 more variables: i_sex <dbl>, i_dvage <dbl>,
    ## #   i_ypdoby <dbl>, i_ypsex <dbl>, i_ypsocweb <dbl>, i_ypnetcht <dbl>,
    ## #   i_yptvvidhrs <dbl>, i_ypmobu <dbl>, i_ypsmartph <dbl>, i_ypnpal <dbl>,
    ## #   i_ypeatlivu <dbl>, i_ypfamsup <dbl>, i_ypupset <dbl>, i_yplate <dbl>,
    ## #   i_ypsibling <dbl>, i_ypsibhit <dbl>, i_ypsibsteal <dbl>,
    ## #   i_ypsibverab <dbl>, i_ypsibtease <dbl>, i_yphitsib <dbl>,
    ## #   i_ypstealsib <dbl>, i_ypverabsib <dbl>, i_ypteasesib <dbl>, i_ypargm <dbl>,
    ## #   i_ypargf <dbl>, i_yptlkm <dbl>, i_yptlkf <dbl>, i_ypstephas <dbl>,
    ## #   i_ypsteprel <dbl>, i_ypsdqa <dbl>, i_ypsdqb <dbl>, i_ypsdqc <dbl>,
    ## #   i_ypsdqd <dbl>, i_ypsdqe <dbl>, i_ypsdqf <dbl>, i_ypsdqg <dbl>,
    ## #   i_ypsdqh <dbl>, i_ypsdqi <dbl>, i_ypsdqj <dbl>, i_ypsdqk <dbl>,
    ## #   i_ypsdql <dbl>, i_ypsdqm <dbl>, i_ypsdqn <dbl>, i_ypsdqo <dbl>,
    ## #   i_ypsdqp <dbl>, i_ypsdqq <dbl>, i_ypsdqr <dbl>, i_ypsdqs <dbl>,
    ## #   i_ypsdqt <dbl>, i_ypsdqu <dbl>, i_ypsdqv <dbl>, i_ypsdqw <dbl>,
    ## #   i_ypsdqx <dbl>, i_ypsdqy <dbl>, i_yphsw <dbl>, i_yphap <dbl>,
    ## #   i_yphfm <dbl>, i_yphfr <dbl>, i_yphsc <dbl>, i_yphlf <dbl>,
    ## #   i_ypllknbrd <dbl>, i_ypcrwra <dbl>, i_ypcrworb <dbl>, i_yphmwrk <dbl>,
    ## #   i_ypfhmwrk <dbl>, i_ypfhweve <dbl>, i_yphmwkhrs <dbl>, i_yphmwkwe <dbl>,
    ## #   i_yphmwkhlp <dbl>, i_yphmwkwho1 <dbl>, i_yphmwkwho2 <dbl>,
    ## #   i_yphmwkwho3 <dbl>, i_yphmwkwho4 <dbl>, i_yphmwkwho5 <dbl>,
    ## #   i_yphmwkwho6 <dbl>, i_ypacvwell <dbl>, i_yplvsc2do <dbl>, i_yp2uni <dbl>,
    ## #   i_yptruant <dbl>, i_ypparsch <dbl>, i_yppareve <dbl>, i_ypotrmisb <dbl>,
    ## #   i_ypmisbsch <dbl>, i_ypfrpbulli <dbl>, i_ypfrobulli <dbl>,
    ## #   i_ypfrpbully <dbl>, i_ypfrobully <dbl>, i_ypsave <dbl>, i_yppkmp <dbl>,
    ## #   i_ypwklw <dbl>, i_ypwhrs <dbl>, i_yppay <dbl>, i_ypcare <dbl>,
    ## #   i_ypcawho1 <dbl>, i_ypcawho2 <dbl>, i_ypcawho3 <dbl>, i_ypcawho4 <dbl>,
    ## #   i_ypcawho5 <dbl>, i_ypcawho6 <dbl>, i_ypcawho7 <dbl>, …

## Tabulate variables (10 points)

In the survey children were asked the following question: “Do you have a
social media profile or account on any sites or apps?”. In this
assignment we want to explore how the probability of having an account
on social media depends on children’s age and gender.

Tabulate three variables: children’s gender, age (please use derived
variables) and having an account on social media.

``` r
# add your code here
source("http://pcwww.liv.ac.uk/~william/R/crosstab.r")
Try <- data.frame(Data$i_ypsex,Data$i_age_dv, Data$i_ypsocweb)

colnames(Try) <- c("Gender", "Age", "Social Media")

ftable(table(Try))
```

    ##            Social Media  -9   1   2
    ## Gender Age                         
    ## 1      9                  0   0   0
    ##        10                 1 102 129
    ##        11                 1 151  88
    ##        12                 4 208  35
    ##        13                 0 190  23
    ##        14                 2 236  16
    ##        15                 0 204  15
    ##        16                 0   6   0
    ## 2      9                  0   0   1
    ##        10                 1 121 106
    ##        11                 0 195  61
    ##        12                 2 191  27
    ##        13                 3 231  16
    ##        14                 0 227  10
    ##        15                 0 212   3
    ##        16                 0   3   0

## Recode variables (10 points)

We want to create a new binary variable for having an account on social
media so that 1 means “yes”, 0 means “no”, and all missing values are
coded as NA. We also want to recode gender into a new variable with the
values “male” and “female” (this can be a character vector or a factor).

``` r
# add your code here
Social_media <- ifelse(Data$i_ypsocweb == 1 ,"yes",
                       ifelse(Data$i_ypsocweb == 2, "No",
                              ifelse(Data$i_ypsocweb == -9, "NA", 0)))


table(Data$i_ypsocweb)
```

    ## 
    ##   -9    1    2 
    ##   14 2277  530

``` r
table(Social_media)
```

    ## Social_media
    ##   NA   No  yes 
    ##   14  530 2277

``` r
Gender <- ifelse(Data$i_ypsex == 1, "Male",
                 ifelse(Data$i_ypsex == 2, "Female", 0))

table(Data$i_ypsex)
```

    ## 
    ##    1    2 
    ## 1411 1410

``` r
table(Gender)
```

    ## Gender
    ## Female   Male 
    ##   1410   1411

## Calculate means (10 points)

Produce code that calculates probabilities of having an account on
social media (i.e. the mean of your new binary variable produced in the
previous problem) by age and gender.

``` r
# add your code here
Age_media <- tapply(Social_media == "yes", Data$i_age_dv, mean, na.rm = TRUE)
Age_media
```

    ##         9        10        11        12        13        14        15        16 
    ## 0.0000000 0.4847826 0.6975806 0.8543897 0.9092873 0.9429735 0.9585253 1.0000000

``` r
Gender_media <- tapply(Social_media == "yes", Gender, mean, na.rm = TRUE)
Gender_media
```

    ##    Female      Male 
    ## 0.8368794 0.7774628

## Write short interpretation (10 points)

Write two or three sentences interpreting your findings above.

The age and media mean shows that all 16 year olds have media, while 0
nine year olds have media. Its clear that as the ages increase from 9 to
16, the averages having media do too. Also, females are more likely to
use social media with an average of 0.84 (2 d.p) with males closely
followed with 0.78 (2 d.p).

## Visualise results (20 points)

Create a statistical graph (only one, but it can be faceted)
illustrating your results (i.e. showing how the probability of having an
account on social media changes with age and gender). Which type of
statistical graph would be most appropriate for this?

``` r
# add your code here

d <- ggplot(Data, aes(Data$i_age_dv))
d + geom_bar()
```

![](testAssignment_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->

``` r
d + stat_summary_bin(aes(y = Social_media), fun.y = "mean", geom = "bar")
```

![](testAssignment_files/figure-gfm/unnamed-chunk-5-2.png)<!-- -->

``` r
## Could not complete.
```

## Conclusion

This is a test formative assignment and the mark will not count towards
your final mark. If you cannot answer any of the questions above this is
fine – we are just starting this module\! However, please do submit this
assignment in any case to make sure that you understand the procedure,
that it works correctly and you do not have any problems with summative
assignments later.
