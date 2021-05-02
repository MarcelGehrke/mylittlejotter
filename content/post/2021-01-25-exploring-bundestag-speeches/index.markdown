---
title: Exploring Bundestag speeches
author: Marcel
date: '2021-05-02'
slug: []
categories:
  - R
tags:
  - Open Data
  - Society
  - Politics
  - R
hero: /assets/images/default-hero.webp
---

# tl;dr

[gganimate](https://gganimate.com/index.html "gganimate") is great to visualize time-dependent data. E.g. [Open Discourse](https://opendiscourse.de/ "Open Discourse"), a well designed comprehensive, machine readable open-source corpus of the plenary proceedings of the federal German Parliament.

# Plotting Bundestag speeches

The plot below shows the summed speeches of politicians in the german Bundestag by Year. The colors are indicating the party each politician belongs to.

Honestly, this is mostly a quick proof of concept on publishing a website via Git commits, utilizing [Hugo](https://gohugo.io/), R [blogdown](https://bookdown.org/yihui/blogdown/) and [Netlify](https://www.netlify.com/).

Code below.

![](plot.gif)






```r
data %<>%
  filter(firstName != "Not found",
         positionShort == "Member of Parliament") %>%
  mutate(year = year(date),
         full_name = paste(firstName, lastName))

context_data <-
  data %>%
  group_by(full_name) %>%
  filter(year == max(year)) %>%
  ungroup() %>%
  select(full_name,
         positionShort,
         party = abbreviation) %>%
  unique()

data %<>%
  group_by(year, full_name) %>%
  count(name = "sum_speeches") %>%
  ungroup()

all_years <- tibble(year = seq(min(data$year), max(data$year), 1))

all_combos <- merge(data %>%
                      select(full_name) %>%
                      distinct(), all_years, all = TRUE)

all_data_interp <- merge(data, all_combos, all.y = TRUE)

all_data_interp %<>%
  mutate(sum_speeches = if_else(is.na(sum_speeches), 0L, sum_speeches)) %>%
  group_by(full_name) %>%
  mutate(speeches_cum = cumsum(sum_speeches)) %>%
  ungroup() %>%
  left_join(context_data, by = "full_name")

plot_data <-
  all_data_interp %>%
  group_by(year) %>%
  arrange(-speeches_cum) %>%
  mutate(rank = row_number()) %>%
  filter(rank <= 15) %>%
  ungroup()

plot_data %<>%
  mutate(party = if_else(
    party %in% c("BP", "DA", "DP", "FU", "KPD", "WAV", "GB/BHE"), 
    "other",
    party
  ))

cols <-
  c(
    "CDU/CSU" = "#000000",
    "DIE LINKE." = "#DF044D",
    "FDP" = "#FFED00",
    "Grüne" = "#347020",
    "other" = "grey",
    "SPD" = "#E30400"
  )
```


```r
plot_theme <- theme_bw() +
  theme(
    plot.title = element_text(size = 40, face = "bold", hjust = 0.5),
    plot.caption = element_text(size = 20),
    plot.subtitle = element_text(size = 30, hjust = 0.5),
    plot.background = element_rect(fill = "#f9fafc"),
    panel.grid.major.y = element_blank(),
    panel.grid.minor.x = element_blank(),
    panel.background = element_rect(fill = "#f9fafc"),
    panel.border = element_blank(),
    legend.background = element_rect(fill = "#f9fafc"),
    legend.text = element_text(size = 20),
    legend.title = element_text(size = 20),
    legend.position = "bottom",
    axis.text.y = element_blank(),
    axis.text.x = element_blank()
  )
```



### Sources

Richter, F.; Koch, P.; Franke, O.; Kraus, J.; Kuruc, F.; Thiem, A.; Högerl, J.; Heine, S.; Schöps, K., 2020, "Open Discourse", <https://doi.org/10.7910/DVN/FIKIBO,> Harvard Dataverse

Pedersen, T. L.; Robinson, D., 2020. "[gganimate](https://gganimate.com/index.html "gganimate"): A Grammar of Animated Graphics", R package version 1.0.7.

Xie, Y; Hill, A., P.; Thomas, A., 2020. "[blogdown](https://bookdown.org/yihui/blogdown/): Create Blogs and Websites with R Markdown", R package version 0.21.71

Further setup below:


```
## R version 4.0.2 (2020-06-22)
## Platform: x86_64-pc-linux-gnu (64-bit)
## Running under: Pop!_OS 20.10
## 
## Matrix products: default
## BLAS:   /usr/lib/x86_64-linux-gnu/openblas-pthread/libblas.so.3
## LAPACK: /usr/lib/x86_64-linux-gnu/openblas-pthread/libopenblasp-r0.3.10.so
## 
## locale:
##  [1] LC_CTYPE=en_US.UTF-8       LC_NUMERIC=C              
##  [3] LC_TIME=de_DE.UTF-8        LC_COLLATE=en_US.UTF-8    
##  [5] LC_MONETARY=de_DE.UTF-8    LC_MESSAGES=en_US.UTF-8   
##  [7] LC_PAPER=de_DE.UTF-8       LC_NAME=C                 
##  [9] LC_ADDRESS=C               LC_TELEPHONE=C            
## [11] LC_MEASUREMENT=de_DE.UTF-8 LC_IDENTIFICATION=C       
## 
## attached base packages:
## [1] stats     graphics  grDevices utils     datasets  methods   base     
## 
## other attached packages:
## [1] pander_0.6.3      zoo_1.8-8         purrr_0.3.4       lubridate_1.7.9.2
## [5] gganimate_1.0.7   dplyr_1.0.5       magrittr_2.0.1    ggplot2_3.3.2    
## 
## loaded via a namespace (and not attached):
##  [1] Rcpp_1.0.5           pillar_1.5.1         compiler_4.0.2      
##  [4] prettyunits_1.1.1    progress_1.2.2       tools_4.0.2         
##  [7] digest_0.6.27        lattice_0.20-41      evaluate_0.14       
## [10] lifecycle_1.0.0.9000 tibble_3.1.0         gtable_0.3.0        
## [13] pkgconfig_2.0.3      rlang_0.4.10         DBI_1.1.0           
## [16] yaml_2.2.1           blogdown_0.21.71     xfun_0.19           
## [19] withr_2.3.0          stringr_1.4.0        knitr_1.30          
## [22] hms_1.0.0            generics_0.1.0       vctrs_0.3.7         
## [25] grid_4.0.2           tidyselect_1.1.0     glue_1.4.2          
## [28] R6_2.5.0             gifski_0.8.6         fansi_0.4.2         
## [31] rmarkdown_2.6        bookdown_0.21        farver_2.0.3        
## [34] tweenr_1.0.1         scales_1.1.1         ellipsis_0.3.1      
## [37] htmltools_0.5.1      assertthat_0.2.1     colorspace_2.0-0    
## [40] utf8_1.2.1           stringi_1.5.3        munsell_0.5.0       
## [43] crayon_1.4.1
```
