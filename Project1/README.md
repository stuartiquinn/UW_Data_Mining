---
title: "001 Capital Bike Share Project"
output:
  html_document:
    toc: yes
  pdf_document:
    toc: yes
    toc_depth: 2
date: "May 5, 2016"
---




#Introduction / About the Data

The City of Seattle recently bought out the bike-share service Pronto, which was established in 2014. The membership of the program has continued to see declines over the previous two years, resulting in the $1.4M buy-out acquisition by the city. In order to identify areas to improve the program the city is hoping to determine factors that define a good station in other bike-share programs, specifically the Capital City Bikeshare in the DC, MD, VA area. The exercise will require defining and collecting attributes that drive or are indicative of high-usage as measured by number of rentals. 

<b><i> About the Data </b></i><br>
<ol>
<li> Source: Capital City Bikeshare</li>
<li> Time Period: Jan 1, 2015 - Dec 31, 2015 </li>
<li> Stations: 157</li>
<li> Zipcodes: 21 </li>
<li> Total Rentals: 2180215 </li>
<li> Variables: 83 </li>
</ol><br>

<b><i> Sources of Data </b></i><br>
The data comes from four separate sources: [Capital Bikeshare](https://www.capitalbikeshare.com/system-data), [Open Streetmap](http://osmar.r-forge.r-project.org/), [Google Maps API](https://developers.google.com/maps/documentation/geocoding/intro#Geocoding) and [NeighborhoodInfo](http://neighborhoodinfodc.org/index.html) (a collaborative composed of the Urban Institute and partner of the National Neighborhood Indicators Partnership (NNIP) ). 


From mapping the number of rentals we find that there is large distribution near the National Mall and reflecting pool, which also share proximity to a number of the national memorial monuments (Lincoln, Vietnam War, WWII and Korean War). Thus, it may be fairly likely that these sites contribute to our usage trends and deserve more exploration. 

Furthermore, we find in our table, that the majority of top rental stations occur in the warmer months, indicating weather influence on usage trends. In fact, on average, we find that there are more rentals in the warmer seasons across the entire data set. 

preservee710fa5917d26d97

<b><i> Figure 1: Get Geographic Distribution of Number of Rentals</b></i>

preserve663569c92fbd86e9


#Methods & Variable Selection
Since our analysis desired to understand attributes that increase usage trends of stations, we began with a base file that included aggregated number of rentals and mean duration based on station from the Capital City Bikeshare. The data set was also accompanied with geographic information (lat/long) variables for each station and surrounding features such as ATM, Cafe, etc. The total data set was 78 variables. We then reverse geocoded the lat/long variables with the Google API to get the associated zipcode of each station. Once we had the zipcode we loaded and merged local socioeconomic and demographic statistics at the zip level. In total, there were 83 before using pre-processing and subset algorithm techniques to reduce the number/complexity of the model. 

##Pre-processing
In order to reduce concerns of multicollinearity or correlated predictors, we removed all variables that had a correlation over 0.75. Additionally, we combined a number of like terms into broader buckets. For example, we created <i> retail </i> which was a composite of shop_art, shop_books, etc. Utilizing the `caret` package we also normalized and scaled our data to make better sense of our model. Essentially, this process makes it possible to compare on an 'on-average' basis of the predictors impact to the outcome (number of rentals), rather than the outcome variable value when other predictors = 0. 

##Variable and Model Selection 
Given the number of variables available to us and limited knowledge about what specifically drives rentals usage, we employed a number of  best subset variable selection algorithms to inform our selection of model features. The selection metric of measurement used for this analysis was the root-mean-squared-error (RMSE) or the average error of prediction when all model features are too at their average level. The result output and most important variables can be seen represented in graphs and tables within the appendix. 

<ol>
<li> Forward Regression </li>
<li> Hybrid Regression </li>
<li> Ridge Regression </li>
<li> Lasso Regression </li> 
</ol>

Upon running these algorithms, we find that a number of the most important features are consistent across methods, though the modelRidge produces the lowest RMSE on average. However, it is still quite elevated at 1942 -- meaning on average the error term prediction is off by that quantity when compared to actual results. The most significant predictors seem to be <i> tourism </i> as expected from our mapping. Finally, it is important to notice that despite our selection of variables being set to a max of 23, the feature importance drops rapidly after the top 10. Therefore, we will only use the top selected features in our final model. 

#Conclusion & Recommendations

Overall, tourism is the largest indicator of increased number of rentals per station. Based on this finding, it would benefit Pronto to not only include more stations/bikes in central tourist areas such as the Pike Place Market, but it may also benefit them to create a promotional strategy that targets tourists. This might include providing one-time discounted pricing for select hotels in the area to give away or perhaps increased marketing materials at major entry points (airport, ferry or via I-5 corridor). Fortunately, Seattle tourism figures have continued to increase and correspond closely to those of Washington D.C. (~20 million/year).

Secondarily, we find a strong negative correspondence to number of rentals based on increases in the unemployment rate. This may be indicative of commuting preference for those employed versus unemployed. An additional and surprising metric related to number of rentals per station is the percent of teen births. Though on the surface this may not make sense, it does have the potential to be a proxy for urban density, where those teens having births may be in more rural or suburban communities. 

The last series of features that are highly predictive of number of rentals are those that lie within other existing transportation infrastructure. For instance, we see that the railway subway entrance, traffic signals and bus stops all represent relationships to the number of rentals at a station. City ownership for Pronto may assist in leveraging transportation planning in a new way that elevates the usage of Pronto. For instance, participation in Sound Transit planning for future light rail stations or further integrated planning with Seattle may assist in driving rentals. 

Due to the RMSE remaining slightly elevated, more work can be done to attempt to drive this figure down by testing more outside data. For instance, it may be valuable to explore visitor statistics, transient nature of population as measured by total percent of population born in state (and presently living there), elevation topography (hills) or finding survey information measuring the number of bike owners in an area. Though both D.C. and Seattle populations are similar in size, it is important to understand how the geography and behaviors differ to get a read on how to install more stations and optimize the Pronto program further. 

#Appendix

##Full Model Results

<img src="001_Project_1_files/figure-html/distributionData-1.png" title="" alt="" width="864" style="display: block; margin: auto;" />






```r
#Full Model 
par(mfrow = c(2,2))
plot(model_full)
```

<img src="001_Project_1_files/figure-html/fullModelPlot-1.png" title="" alt="" width="768" style="display: block; margin: auto;" />

```r
#Graphical Analysis from full model
#[1] Residual v. Fitted: Heteroscedacity is present, as indicated by the "cone shape." This means the variability of a variable (num_rentals) is not constant across the range of values of a second variable(s) that predict it. Accuracy wanes in prediction of high volume rentals
#Source: http://www.statsmakemecry.com/smmctheblog/confusing-stats-terms-explained-heteroscedasticity-heteroske.html
#[2] Indicates leptokurtosis (high-kurtosis) or the distribution has "Fat-Tails". 
#Source: http://stats.stackexchange.com/questions/101274/how-to-interpret-a-qq-plot
#[4] Cooks Distance: How far the predicted value of your data points would move if your model were built without that data point included
#####Leverage: The impact on the OLS line of best fit (individually point impact)
```







###Forward Model:Cross-Validated(10); VarMax (25)
<b><i>Top 12 Vars: Scaled and Centered (in-sample)</b></i><br>
<img src="001_Project_1_files/figure-html/modelForward-1.png" title="" alt="" width="384" /><img src="001_Project_1_files/figure-html/modelForward-2.png" title="" alt="" width="384" />

###Hybrid Model:Cross-Validated(10); VarMax (25)
<b><i>Top 12 Vars: Scaled and Centered (in-sample)</b></i><br>
<img src="001_Project_1_files/figure-html/modelHybrid-1.png" title="" alt="" width="384" /><img src="001_Project_1_files/figure-html/modelHybrid-2.png" title="" alt="" width="384" />

###Ridge Model:Cross-Validated(10); Tune Length(10)
<b><i>Top 12 Vars: Scaled and Centered (in-sample)</b></i><br>
<img src="001_Project_1_files/figure-html/modelRidge-1.png" title="" alt="" width="384" /><img src="001_Project_1_files/figure-html/modelRidge-2.png" title="" alt="" width="384" />

###Lasso Regression:Cross-Validated(10); Tune Lenth (10)
<b><i>Top 12 Vars: Scaled and Centered (in-sample)</b></i><br>
<img src="001_Project_1_files/figure-html/modelLasso-1.png" title="" alt="" width="384" /><img src="001_Project_1_files/figure-html/modelLasso-2.png" title="" alt="" width="384" />

###Model Metric Comparison
<b><i>In-Sample</b></i><br>




```
## 
## Call:
## summary.resamples(object = results)
## 
## Models: forward, hybrid, ridge, lasso 
## Number of resamples: 10 
## 
## RMSE 
##         Min. 1st Qu. Median Mean 3rd Qu. Max. NA's
## forward 1704    1753   1927 2128    2307 3094    0
## hybrid  1639    1844   2021 2156    2502 3067    0
## ridge   1512    1636   1752 1942    2146 2788    0
## lasso   1510    1583   1790 1949    2214 2818    0
## 
## Rsquared 
##           Min. 1st Qu. Median   Mean 3rd Qu.   Max. NA's
## forward 0.4788  0.4940 0.5911 0.5823  0.6427 0.7429    0
## hybrid  0.3621  0.4711 0.5918 0.5582  0.6193 0.7113    0
## ridge   0.4571  0.6007 0.6416 0.6376  0.7276 0.7738    0
## lasso   0.4637  0.5673 0.6597 0.6305  0.7077 0.7623    0
```

<img src="001_Project_1_files/figure-html/compareModels-1.png" title="" alt="" width="864" style="display: block; margin: auto;" />

###Model Performance on Test Data

```
##   modelType TrainRMSE TestRMSE      diff
## 1   Forward  2127.863 1977.412 150.45121
## 2    Hybrid  2155.614 1976.436 179.17804
## 3     Ridge  1942.020 1897.543  44.47654
## 4     Lasso  1948.905 1854.540  94.36512
```

###R Packages Used


```r
sessionInfo()
```

```
## R version 3.2.3 (2015-12-10)
## Platform: x86_64-w64-mingw32/x64 (64-bit)
## Running under: Windows >= 8 x64 (build 9200)
## 
## locale:
## [1] LC_COLLATE=English_United States.1252 
## [2] LC_CTYPE=English_United States.1252   
## [3] LC_MONETARY=English_United States.1252
## [4] LC_NUMERIC=C                          
## [5] LC_TIME=English_United States.1252    
## 
## attached base packages:
## [1] grid      stats     graphics  grDevices utils     datasets  methods  
## [8] base     
## 
## other attached packages:
##  [1] leaps_2.9       elasticnet_1.1  lars_1.2        car_2.1-1      
##  [5] MASS_7.3-45     caret_6.0-64    lattice_0.20-33 knitr_1.12.3   
##  [9] DT_0.1          rmarkdown_0.9.2 stringr_1.0.0   maps_3.1.0     
## [13] leaflet_1.0.0   gridExtra_2.2.1 arulesViz_1.1-1 ggplot2_2.1.0  
## [17] dplyr_0.4.3     arules_1.4-1    Matrix_1.2-3   
## 
## loaded via a namespace (and not attached):
##  [1] Rcpp_0.12.4          vcd_1.4-1            zoo_1.7-12          
##  [4] gtools_3.5.0         assertthat_0.1       digest_0.6.9        
##  [7] lmtest_0.9-34        foreach_1.4.3        R6_2.1.2            
## [10] plyr_1.8.3           MatrixModels_0.4-1   stats4_3.2.3        
## [13] evaluate_0.8         gplots_2.17.0        lazyeval_0.1.10     
## [16] SparseM_1.7          minqa_1.2.4          gdata_2.17.0        
## [19] whisker_0.3-2        nloptr_1.0.4         labeling_0.3        
## [22] splines_3.2.3        lme4_1.1-11          htmlwidgets_0.5     
## [25] munsell_0.4.3        compiler_3.2.3       mgcv_1.8-9          
## [28] htmltools_0.3        nnet_7.3-11          seriation_1.2-0     
## [31] codetools_0.2-14     dendextend_1.1.8     bitops_1.0-6        
## [34] jsonlite_0.9.19      nlme_3.1-124         gtable_0.2.0        
## [37] registry_0.3         DBI_0.3.1            magrittr_1.5        
## [40] formatR_1.2.1        scales_0.4.0         KernSmooth_2.23-15  
## [43] stringi_1.0-1        mapproj_1.2-4        reshape2_1.4.1      
## [46] scatterplot3d_0.3-36 RColorBrewer_1.1-2   iterators_1.0.8     
## [49] tools_3.2.3          gclus_1.3.1          parallel_3.2.3      
## [52] pbkrtest_0.4-6       yaml_2.1.13          colorspace_1.2-6    
## [55] cluster_2.0.3        caTools_1.17.1       TSP_1.1-4           
## [58] quantreg_5.21
```

```r
#render()
```
