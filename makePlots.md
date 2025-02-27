# Make plots

# All the countries

## Load the .csv and exclude so id vars


```r
datS <- read.csv("http://www.qogdata.pol.gu.se/data/qog_std_ts_15may13.csv", 
    sep = ";")
datSmot <- datS[, c(-1, -4, -5, -6, -7, -8, -9)]

datSP <- read.csv("http://www.qogdata.pol.gu.se/data/qog_soc_tsl_4apr12.csv", 
    sep = ";")
datSPmot <- datSP[, c(-1, -4, -5, -6, -7, -8)]
```



## Generate the Motion Chart and save it

```r
datSmot2 <- datSmot[datSmot$year >= 2000, ]
library(googleVis)
motionStandard <- gvisMotionChart(datSmot2, idvar = "cname", timevar = "year", 
    xvar = "mad_gdppc", yvar = "undp_hdi", colorvar = "fh_pr", sizevar = "mad_pop", 
    options = list(height = 900, width = 1100))
## Save
print(motionStandard, file = "motionStandard.html")
## plot
datSPmot2 <- datSmot[datSPmot$year >= 2000, ]
motionSocialPolicy <- gvisMotionChart(datSPmot2, idvar = "cname", timevar = "year", 
    xvar = "wdi_gdp", yvar = "wdi_gini", colorvar = "fh_pr", sizevar = "wdi_pop", 
    options = list(height = 900, width = 1100))
## Save
print(motionSocialPolicy, file = "motionSocialPolicy.html")
```



- [Click here to browse the motion chart](http://muuankarski.github.io/QogGVis/motionStandard.html)
- [Click here to browse the motion chart](http://muuankarski.github.io/QogGVis/motionSocialPolicy.html)

# Post socialist countries from 1990

## Generate the Motion Chart and save it

```r
clist <- c("Czech Republic", "Estonia", "Hungary", "Bulgaria", "Latvia", "Lithuania", 
    "Poland", "Slovakia", "Slovenia", "Romania", "Albania", "Bosnia", "Bulgaria", 
    "Croatia", "Macedonia", "Montenegro", "Kosovo", "Serbia", "Armenia", "Azerbaijan", 
    "Belarus", "Georgia", "Kazakhstan", "Kyrgyzstan", "Moldova", "Mongolia", 
    "Russia", "Tajikistan", "Ukraine", "Uzbekistan")

datSmot2 <- datSmot[datSmot$year >= 1990, ]
datSmot3 <- datSmot2[datSmot2$cname %in% clist, ]
library(googleVis)
motionStandardPostS <- gvisMotionChart(datSmot3, idvar = "cname", timevar = "year", 
    xvar = "mad_gdppc", yvar = "undp_hdi", sizevar = "mad_pop", colorvar = "fh_pr", 
    options = list(height = 900, width = 1100))
## Save
print(motionStandardPostS, file = "motionStandardPostS.html")
## plot
datSPmot2 <- datSPmot[datSPmot$year >= 1990, ]
datSPmot3 <- datSPmot2[datSPmot2$cname %in% clist, ]
motionSocialPolicyPostS <- gvisMotionChart(datSPmot3, idvar = "cname", timevar = "year", 
    xvar = "wdi_gdp", yvar = "wdi_gini", sizevar = "wdi_pop", colorvar = "fh_pr", 
    options = list(height = 900, width = 1100))
## Save
print(motionSocialPolicyPostS, file = "motionSocialPolicyPostS.html")
```



- [Click here to browse the motion chart](http://muuankarski.github.io/QogGVis/motionStandardPostS.html)
- [Click here to browse the motion chart](http://muuankarski.github.io/QogGVis/motionSocialPolicyPostS.html)


# Eu countries from 1990

## Generate the Motion Chart and save it

```r
clistEu <- c("Austria", "Belgium", "Bulgaria", "Cyprus", "Czech Republic", "Denmark", 
    "Estonia", "Finland", "France", "Germany", "Greece", "Hungary", "Iceland", 
    "Ireland", "Italy", "Latvia", "Lithuania", "Luxembourg", "Malta", "Netherlands", 
    "Norway", "Poland", "Portugal", "Romania", "Slovakia", "Slovenia", "Spain", 
    "Sweden", "Switzerland", "United Kingdom")
datSmot2 <- datSmot[datSmot$year >= 1990, ]
datSmot3 <- datSmot2[datSmot2$cname %in% clistEu, ]
library(googleVis)
motionStandardEu <- gvisMotionChart(datSmot3, idvar = "cname", timevar = "year", 
    xvar = "mad_gdppc", yvar = "undp_hdi", colorvar = "fh_pr", sizevar = "mad_pop", 
    options = list(height = 900, width = 1100))
## Save
print(motionStandardEu, file = "motionStandardEu.html")
## plot
datSPmot2 <- datSPmot[datSPmot$year >= 1990, ]
datSPmot3 <- datSPmot2[datSPmot2$cname %in% clistEu, ]
motionSocialPolicyEu <- gvisMotionChart(datSPmot3, idvar = "cname", timevar = "year", 
    xvar = "wdi_gdp", yvar = "wdi_gini", colorvar = "fh_pr", sizevar = "wdi_pop", 
    options = list(height = 900, width = 1100))
## Save
print(motionSocialPolicyEu, file = "motionSocialPolicyEu.html")
```


- [Click here to browse the motion chart](http://muuankarski.github.io/QogGVis/motionStandardEu.html)
- [Click here to browse the motion chart](http://muuankarski.github.io/QogGVis/motionSocialPolicyEu.html)

# Exit/Entry selection from 1990

## Generate the Motion Chart and save it

```r
clistOlli <- c("Australia", "Austria", "Belgium", "Canada", "Denmark ", "Finland ", 
    "France", "Germany", "Ireland", "Italy", "Japan", "Netherlands", "New Zealand", 
    "Norway", "Sweden", "Switzerland", "United Kingdom", "United States")

# datSmot2 <- datSmot[datSmot$year >= 1990, ] datSmot3 <-
# datSmot2[datSmot2$cname %in% clistEu, ] library(googleVis)
# motionStandardEu <- gvisMotionChart(datSmot3, idvar='cname',
# timevar='year', xvar='mad_gdppc', yvar='undp_hdi', colorvar='fh_pr',
# sizevar='mad_pop', options=list(height=900, width=1100)) ## Save
# print(motionStandardEu, file='motionStandardEu.html') plot
datSPmot2 <- datSPmot[datSPmot$year >= 1980, ]
datSPmot3 <- datSPmot2[datSPmot2$cname %in% clistOlli, ]
motionSocialPolicyExit <- gvisMotionChart(datSPmot3, idvar = "cname", timevar = "year", 
    xvar = "socx_hput", yvar = "wdi_lifexp", colorvar = "cname", sizevar = "wdi_pop", 
    options = list(height = 900, width = 1100))
## Save
print(motionSocialPolicyExit, file = "motionSocialPolicyExit.html")
```


- [Click here to browse the motion chart](http://muuankarski.github.io/QogGVis/motionStandardEu.html)
- [Click here to browse the motion chart](http://muuankarski.github.io/QogGVis/motionSocialPolicyEu.html)
