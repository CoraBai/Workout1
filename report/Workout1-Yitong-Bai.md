Workout1-Yitong-Bai
================
Cora Bai
9/30/2018

``` r
library("ggplot2")
```

    ## Warning: package 'ggplot2' was built under R version 3.4.4

``` r
library("dplyr")
```

    ## Warning: package 'dplyr' was built under R version 3.4.4

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
nba= read.csv("~/Desktop/133/workout1/data/nba2018-teams.csv")
ggplot(data = nba, aes(x = reorder(team, sum_salary), y = sum_salary))+ 
  geom_bar(stat = 'identity', fill = "grey")+ coord_flip()+
  labs(x = "Team", y = "Salary (in millions)", title = "NBA Teams ranked by Total Salary")+ 
  scale_y_continuous(limits = c(0,140), breaks = seq(0,120, by =40))+
  geom_hline(yintercept = mean(nba$sum_salary), col ="red")
```

![](Workout1-Yitong-Bai_files/figure-markdown_github/unnamed-chunk-2-1.png)

``` r
ggplot (data = nba, aes(x = reorder(team, sum_points), y = sum_points)) +
  geom_bar(stat = 'identity', fill = "grey")+ coord_flip()+ labs(x = "Team", y = "Points", title = "NBA Teams ranked by Total Points") + 
  scale_y_continuous(limits = c(0,10000),breaks = seq(2500,10000, by =1500)) +
  geom_hline(yintercept = mean(nba$sum_points), col ="red")
```

![](Workout1-Yitong-Bai_files/figure-markdown_github/unnamed-chunk-3-1.png)

``` r
ggplot(data = nba, aes(x = reorder(team, sum_efficiency), y = sum_efficiency))+ 
  geom_bar(stat = 'identity', fill = "grey")+ coord_flip()+
  labs(x = "Team", y = "Efficiency", title = "NBA Teams ranked by Efficiency")+ 
   scale_y_continuous(limits = c(0,350), breaks = seq(0,350, by =50))+
  geom_hline(yintercept = mean(nba$sum_efficiency), col ="red")
```

![](Workout1-Yitong-Bai_files/figure-markdown_github/unnamed-chunk-4-1.png)

My own index is called points3 per year, which means the average number of points3 that a player get. My reasoning is that points3 is a good measurement of a player's skills and preciseness. However, the total number of points3 may be affected by the experience (the older the player is, the more likely he/she has more points3). Therefore, use points3/experience is a good indicator.

``` r
avg_points3 = nba$sum_points3 / nba$sum_experience
 ggplot(data = nba, aes(x = reorder(nba$team, avg_points3), y = avg_points3))+ 
  geom_bar(stat = 'identity', fill = "grey")+ coord_flip()+
  labs(x = "Team", y = "Average Points3 Per Year", title = "NBA Teams ranked by Points3 Per Year")+ 
  geom_hline(yintercept = mean(avg_points3), col ="red")
```

![](Workout1-Yitong-Bai_files/figure-markdown_github/unnamed-chunk-5-1.png)

Comments and Reflections
------------------------

-   It is my first time working on building complete file structure, and I feel it is a really detail-oriented and time-consuming work.
-   This is not my first time using relative path, but I still made mistakes because the console location might be different from the location of md or rmd file. That is really confusing to me.
-   This is my first time writing Rscript, and just writing code is not that straightforward. But it is abstract.
-   I think ggplot2 is still hard for me to memorize all variables.
-   I think the command line and git is easy.
-   I finished the project on my own. I searched for R functions online (Stackoverflow).
-   The most time consuming part is creating the dictionary as I was not that familiar with markdown syntax.
-   The interesting part would be git push.
