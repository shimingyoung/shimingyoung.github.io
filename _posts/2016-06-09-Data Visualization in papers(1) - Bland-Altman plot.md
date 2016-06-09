---
layout: post
title: Data Visualization in papers(1) - Bland-Altman plot
subtitle: A post
---

---

This is from one of my previous posts. Just added a little more.

We often need to compare two sets of data for their agreement.

The [Bland-Altman plot](https://en.wikipedia.org/wiki/Bland%E2%80%93Altman_plot) is a tool to analyze the agreement between two different measurements. I used it in several of my papers (e.g. Fig.3 in [ICP estimation2015](../papers/ICP_estimation15.pdf), Fig.3 in [SpHb 2016](../papers/AA2015_manuscript.pdf), Figs.1-3 in [RespRate2016](RR_Manuscript.pdf) ). Sometimes, I feel the original B-A plot is not visually enough to show the distribution of dots (mean vs diff). Adding the density plots for the mean and diff may provide more information of how the two quantities located/shaped. So in most of my papers, I use B-A plot together with density plots of mean and diff (of the two measurements).

Also, in some studies, we have repeated measurements for each subject. Then the B-A plot should adjust to the repeated measurement. The MedCalc has a menu to do "B-A plot with multiple measurements per subject" Also see Bland JM, Altman DG(2007) Agreement between methods of measurement with multiple observations per individual. J. of Biopharmaceutical Statistics, 17:571-582.

MedCalc is a good tool. But I still hope to use R to draw a configurable (good-looking) graph. So, here are two R scripts for B-A plots (traditional, and for repeated measurements). Have to say, I just assembled the code (I used example code from [here](http://r.789695.n4.nabble.com/Bland-Altman-method-to-measure-agreement-with-repeated-measures-td862197.html) ). The R code is available [here](https://www.dropbox.com/s/eug4oaqq51eosbf/BA_repeated.R?dl=0).

To use it. assume in r workspace there are variables 'x' and 'y' as two measurements (same length vector), and a variable 'id' to indicate which subject each value belongs to. 

~~~~
>source('BA_repeated.R')
>library(ggplot2)
>library(gridExtra)
>Bland.Altman.re(x, y, rep.meas=TRUE, subject=id, xname='XMeas', yname='YMeas', addDensity=TRUE)
~~~~

---
