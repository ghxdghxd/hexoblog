---
title: meta Analysis
comments: true
date: 2018-02-26 17:17:46
description: meta analysis with metafor
categories: 统计
tags: R
---
# metafor document

+ An Overview of Functions in the metafor Package

{% pdf /documents/metafor_diagram.pdf %}

+ Viechtbauer gesis ma with metafor

{% pdf /documents/talks_2016_viechtbauer_gesis_ma_with_metafor.pdf %}

## meta-analysis from odds ratios and confidence intervals using metafor

```R
dm<-structure(list(or = c(1.6, 4.4, 1.14, 1.3, 4.5), cill = c(1.2, 2.9, 0.45, 0.6, 3.2), ciul = c(2, 6.9, 2.86, 2.7, 6.1)), .Names = c("or", "cill", "ciul"), class = "data.frame", row.names = c(NA, -5L))

dm$logor<-log(dm$or)
dm$se1<-(log(dm$ciul)-dm$logor)/1.96
dm$se2<-(dm$logor-log(dm$cill))/1.96
dm$se<-(dm$se1+dm$se2)/2

library(metafor)
dmres<-rma.uni(yi=logor, sei=se, data=dm)
pdf()
forest(dmres, atransf=exp, showweights = T, mlab = "rsid", slab = paste0("study", 1:5))
dev.off()
```