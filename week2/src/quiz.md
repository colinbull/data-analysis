Week2 Quiz
==========

Setup some common variables and the working directory
```
setwd("./week2")
url <- "https://spark-public.s3.amazonaws.com/dataanalysis/"
```

Question 2
----------
```
library(XML)
dataConnection = url("http://simplystatistics.tumblr.com/")
data = readLines(dataConnection, n = 150)
close(dataConnection)
lapply(data, nchar)[c(2,45,122)]
```
_Answer: 918,5,24_

Question 3
----------
```
download.file(paste(url,"PUMSDataDict06.pdf", sep=""),destfile="./data/housing.pdf",method="auto")
download.file(paste(url,"ss06hid.csv",sep=""),destfile="./data/housing.csv",method="auto")

housingData <- read.csv("./data/housing.csv")
head(housingData)
names(housingData)
?sum
sum(housingData$VAL == 24, na.rm = TRUE)
```
_Answer: 53_

Question 5
----------
```
f <- function(bds,rms) {
  sum(housingData$BDS == bds & housingData$RMS == rms, na.rm = TRUE)
}
f(3,4);f(2,5);f(2,7)
```
_Answer: 148,386,49_

Question 6
----------
```
agricultureLogical <- housingData$ACR == 3 & housingData$AGS == 6
which(agricultureLogical)[1:3]
```
_Answer: 125,238,262_

Question 7
----------
```
indexes <- which(agricultureLogical)
subFrame <- housingData[indexes,]
sum(is.na(subaFrame$MRGX))
```
_Answer: 8_

Question 8
----------
```
ncol(housingData)
names(housingData)
strsplit(names(housingData),"wgtp")[123]
```
_Answer: "" "15"_

Question 9
----------
```
quantile(housingData$YBL,na.rm=TRUE)
```
_Answer: -1,25, Something Wrong_

Question 10
-----------
```
download.file(paste(url,"ss06pid.csv", sep=""),destfile="./data/population.csv",method="auto")
populationData <- read.csv("./data/population.csv")
head(populationData)
mergedData <- merge(housingData,populationData,by.x="SERIALNO",by.y="SERIALNO",all=TRUE)
dim(mergedData) 
mergedData <- merge(housingData,populationData)
```
_Answer: 1451, 426_
