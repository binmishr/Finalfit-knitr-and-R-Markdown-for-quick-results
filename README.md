# Finalfit-knitr-and-R-Markdown-for-quick-results

The details of the codeset and plots are included in the attached Microsoft Word Document (.docx) file in this repository. 
You need to view the file in "Read Mode" to see the contents properly after downloading the same.

Finalfit Package - A Brief Introduction
========================================

The finalfit package provides functions that help you quickly create elegant final results tables and plots when modelling in R. These can easily be exported as Word documents, PDFs, or html files.In addition, it provides functions for identifying and handling missing data, together with a number of functions to bootstrap simulate regression model results.

Installation
============
Library("finalfit")

It is recommended that this package is used together with dplyr which can be installed via:

install.packages("dplyr")

Documentation
==============

Examples
=========
See getting started and the All tables vignettes for extensive examples.
Crosstable / table 1

    # Crosstable 
    explanatory = c("age.factor", "sex.factor", "obstruct.factor")
    dependent = 'mort_5yr'
    colon_s %>%
      summary_factorlist(dependent, explanatory, 
      p=TRUE, add_dependent_label=TRUE) -> t1
    knitr::kable(t1, align=c("l", "l", "r", "r", "r"))
    
   
Regression table
================
    explanatory = c("age.factor", "sex.factor", 
      "obstruct.factor", "perfor.factor")
    dependent = 'mort_5yr'
    colon_s %>%
      finalfit(dependent, explanatory, metrics=TRUE) -> t2
    knitr::kable(t2[[1]], row.names=FALSE, align=c("l", "l", "r", "r", "r", "r"))
    knitr::kable(t2[[2]], row.names=FALSE, col.names="")
        
    
When exported to PDF:

Regression plots
=================
    explanatory = c("age.factor", "sex.factor", 
      "obstruct.factor", "perfor.factor")
    dependent = 'mort_5yr'
    colon_s %>%
      or_plot(dependent, explanatory)
