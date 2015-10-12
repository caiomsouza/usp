<!-- R Commander Markdown Template -->

Curso de Verão na USP Leste
04 e 05 de Fevereiro de 2015
=======================

### Caio Moreno de Souza
### caio@it4biz.com.br

### 2015-02-04




```r
> Nations <- read.table("/Volumes/CAIO/CursoR-USP-Lest-Fev15/exemplos_R/datasets/Nations.txt", 
+   header=TRUE, sep="", na.strings="NA", dec=".", strip.white=TRUE)
```


```r
> summary(Nations)
```

```
      TFR        contraception   infant.mortality      GDP       
 Min.   :1.190   Min.   : 2.00   Min.   :  2.00   Min.   :   36  
 1st Qu.:1.950   1st Qu.:21.00   1st Qu.: 12.00   1st Qu.:  442  
 Median :3.070   Median :47.00   Median : 30.00   Median : 1779  
 Mean   :3.529   Mean   :43.43   Mean   : 43.48   Mean   : 6262  
 3rd Qu.:4.980   3rd Qu.:64.00   3rd Qu.: 66.00   3rd Qu.: 7272  
 Max.   :8.000   Max.   :86.00   Max.   :169.00   Max.   :42416  
 NA's   :10      NA's   :63      NA's   :6        NA's   :10     
      region  
 Africa  :55  
 Americas:41  
 Asia    :41  
 Europe  :45  
 Oceania :25  
              
              
```


```r
> library(abind, pos=16)
```


```r
> library(e1071, pos=17)
```


```r
> numSummary(Nations[,c("contraception", "GDP", "infant.mortality", "TFR")], 
+   statistics=c("mean", "sd", "IQR", "quantiles"), quantiles=c(0,.25,.5,.75,1))
```

```
                        mean          sd     IQR    0%    25%     50%
contraception      43.430556   23.706732   43.00  2.00  21.00   47.00
GDP              6261.954315 9355.659390 6830.00 36.00 442.00 1779.00
infant.mortality   43.477612   38.756041   54.00  2.00  12.00   30.00
TFR                 3.528782    1.761974    3.03  1.19   1.95    3.07
                     75%  100%   n NA
contraception      64.00    86 144 63
GDP              7272.00 42416 197 10
infant.mortality   66.00   169 201  6
TFR                 4.98     8 197 10
```


```r
> numSummary(Nations[,c("contraception", "GDP", "infant.mortality", "TFR")], 
+   statistics=c("mean", "sd", "IQR", "quantiles"), quantiles=c(0,.25,.5,.75,1))
```

```
                        mean          sd     IQR    0%    25%     50%
contraception      43.430556   23.706732   43.00  2.00  21.00   47.00
GDP              6261.954315 9355.659390 6830.00 36.00 442.00 1779.00
infant.mortality   43.477612   38.756041   54.00  2.00  12.00   30.00
TFR                 3.528782    1.761974    3.03  1.19   1.95    3.07
                     75%  100%   n NA
contraception      64.00    86 144 63
GDP              7272.00 42416 197 10
infant.mortality   66.00   169 201  6
TFR                 4.98     8 197 10
```


```r
> numSummary(Nations[,c("contraception", "GDP", "infant.mortality", "TFR")], 
+   statistics=c("mean", "sd", "IQR", "quantiles"), quantiles=c(0,.25,.5,.75,1))
```

```
                        mean          sd     IQR    0%    25%     50%
contraception      43.430556   23.706732   43.00  2.00  21.00   47.00
GDP              6261.954315 9355.659390 6830.00 36.00 442.00 1779.00
infant.mortality   43.477612   38.756041   54.00  2.00  12.00   30.00
TFR                 3.528782    1.761974    3.03  1.19   1.95    3.07
                     75%  100%   n NA
contraception      64.00    86 144 63
GDP              7272.00 42416 197 10
infant.mortality   66.00   169 201  6
TFR                 4.98     8 197 10
```


```r
> help("Prestige", package="car")
```


```r
> data(Prestige, package="car")
```


```r
> data()
```


```r
> data(Prestige, package="car")
```


```r
> LinearModel.1 <- lm(prestige ~ education + log(income), data=Prestige)
> summary(LinearModel.1)
```

```

Call:
lm(formula = prestige ~ education + log(income), data = Prestige)

Residuals:
     Min       1Q   Median       3Q      Max 
-17.0346  -4.5657  -0.1857   4.0577  18.1270 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept) -95.1940    10.9979  -8.656 9.27e-14 ***
education     4.0020     0.3115  12.846  < 2e-16 ***
log(income)  11.4375     1.4371   7.959 2.94e-12 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 7.145 on 99 degrees of freedom
Multiple R-squared:  0.831,	Adjusted R-squared:  0.8275 
F-statistic: 243.3 on 2 and 99 DF,  p-value: < 2.2e-16
```


```r
> LinearModel.2 <- lm(prestige ~ (education + log(income))*type, data=Prestige)
> summary(LinearModel.2)
```

```

Call:
lm(formula = prestige ~ (education + log(income)) * type, data = Prestige)

Residuals:
    Min      1Q  Median      3Q     Max 
-13.970  -4.124   1.206   3.829  18.059 

Coefficients:
                          Estimate Std. Error t value Pr(>|t|)    
(Intercept)              -120.0459    20.1576  -5.955 5.07e-08 ***
education                   2.3357     0.9277   2.518  0.01360 *  
log(income)                15.9825     2.6059   6.133 2.32e-08 ***
type[T.prof]               85.1601    31.1810   2.731  0.00761 ** 
type[T.wc]                 30.2412    37.9788   0.796  0.42800    
education:type[T.prof]      0.6974     1.2895   0.541  0.58998    
education:type[T.wc]        3.6400     1.7589   2.069  0.04140 *  
log(income):type[T.prof]   -9.4288     3.7751  -2.498  0.01434 *  
log(income):type[T.wc]     -8.1556     4.4029  -1.852  0.06730 .  
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 6.409 on 89 degrees of freedom
  (4 observations deleted due to missingness)
Multiple R-squared:  0.871,	Adjusted R-squared:  0.8595 
F-statistic: 75.15 on 8 and 89 DF,  p-value: < 2.2e-16
```


```r
> Anova(LinearModel.2, type="II")
```

```
Anova Table (Type II tests)

Response: prestige
                 Sum Sq Df F value    Pr(>F)    
education        1209.3  1 29.4446 4.912e-07 ***
log(income)      1690.8  1 41.1670 6.589e-09 ***
type              469.1  2  5.7103  0.004642 ** 
education:type    178.8  2  2.1762  0.119474    
log(income):type  290.3  2  3.5344  0.033338 *  
Residuals        3655.4 89                      
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```


```r
> LinearModel.3 <- lm(log2(income) ~ education, data=Prestige)
> summary(LinearModel.3)
```

```

Call:
lm(formula = log2(income) ~ education, data = Prestige)

Residuals:
     Min       1Q   Median       3Q      Max 
-3.02037 -0.36190  0.04731  0.48525  1.90414 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept) 10.65385    0.28972  36.773  < 2e-16 ***
education    0.17141    0.02616   6.553 2.48e-09 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 0.7173 on 100 degrees of freedom
Multiple R-squared:  0.3004,	Adjusted R-squared:  0.2934 
F-statistic: 42.94 on 1 and 100 DF,  p-value: 2.48e-09
```


```r
> LinearModel.4 <- lm(prestige ~ (education + log(income))*type, data=Prestige)
> summary(LinearModel.4)
```

```

Call:
lm(formula = prestige ~ (education + log(income)) * type, data = Prestige)

Residuals:
    Min      1Q  Median      3Q     Max 
-13.970  -4.124   1.206   3.829  18.059 

Coefficients:
                          Estimate Std. Error t value Pr(>|t|)    
(Intercept)              -120.0459    20.1576  -5.955 5.07e-08 ***
education                   2.3357     0.9277   2.518  0.01360 *  
log(income)                15.9825     2.6059   6.133 2.32e-08 ***
type[T.prof]               85.1601    31.1810   2.731  0.00761 ** 
type[T.wc]                 30.2412    37.9788   0.796  0.42800    
education:type[T.prof]      0.6974     1.2895   0.541  0.58998    
education:type[T.wc]        3.6400     1.7589   2.069  0.04140 *  
log(income):type[T.prof]   -9.4288     3.7751  -2.498  0.01434 *  
log(income):type[T.wc]     -8.1556     4.4029  -1.852  0.06730 .  
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 6.409 on 89 degrees of freedom
  (4 observations deleted due to missingness)
Multiple R-squared:  0.871,	Adjusted R-squared:  0.8595 
F-statistic: 75.15 on 8 and 89 DF,  p-value: < 2.2e-16
```


```r
> Anova(LinearModel.4, type="II")
```

```
Anova Table (Type II tests)

Response: prestige
                 Sum Sq Df F value    Pr(>F)    
education        1209.3  1 29.4446 4.912e-07 ***
log(income)      1690.8  1 41.1670 6.589e-09 ***
type              469.1  2  5.7103  0.004642 ** 
education:type    178.8  2  2.1762  0.119474    
log(income):type  290.3  2  3.5344  0.033338 *  
Residuals        3655.4 89                      
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```


