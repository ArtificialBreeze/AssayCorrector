# AssayCorrector
[![Build Status](https://travis-ci.org/bmazoure/AssayCorrector.svg?branch=master)](https://travis-ci.org/bmazoure/AssayCorrector)
### Description
This package uses partial mean polish and non-parametric statistical procedures to identify and correct spatial bias present in high-thoughput screening assays.
### Installation
You can install the ```AssayCorrector``` package by typing
```{r }
install.packages('devtools')
devtools::install_github('bmazoure/AssayCorrector')
```
If there is an error with the package `mixOmics`, run the following and re-try:
```{r }
install.packages("https://cran.r-project.org/src/contrib/Archive/mixOmics/mixOmics_6.3.2.tar.gz", repos=NULL, type="source")
```
### Usage
First, an ```assay``` object should be created by using 
```{r }
library(AssayCorrector)
# Fictive 8x12x5 assay
assay<-create_assay(m)
# Plate 7 taken from Carralot et al. 2012
assay<-create_assay(plate7)
```
Next, we can detect and correct the bias as follows:
```{r }
detected<-detect_bias(assay,type="P",alpha=0.01)
corrected<-correct_bias(detected,method=1,type="P") # Correct the bias assuming an additive model (method=1), plate-wise only
```
The S3 methods ```print.assay()``` and ```plot.assay()``` override the default functions. Consult the complete pdf documentation for examples
