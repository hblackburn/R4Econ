----
## R Packages for Econs and Stata Emigrees

There are more R packages than stars in the sky. But many of them are written without economics in mind. There are also just some things you miss about Stata, and being able to do them in R would make things so much easier!

This page will not attempt to list every potentially useful package under the sun, but will try to cover things that econs may find useful. 

Note that some included packages are not on CRAN and must be installed with `devtools::install_github()`.

----
## Procuring Data

# APIs for common data sources:
* [Guide to Client-Side APIs] by Grant McDermott. Guide for using APIs that don't have their own R packages
* [wbstats](https://cran.r-project.org/web/packages/wbstats/wbstats.pdf) and [data360r](https://tcdata360.worldbank.org/tools/data360r) - World Bank
* [tidycensus](https://cran.r-project.org/web/packages/tidycensus/tidycensus.pdf) - US Census and ACS, plus US map shape files
* [tidyquant](https://cran.r-project.org/web/packages/tidyquant/index.html) and [fredr](https://cran.r-project.org/web/packages/fredr/vignettes/fredr.html) - Finance data. Tidyquant has access to more sources, but fredr is easier to use
* [NHANES](https://cran.r-project.org/web/packages/NHANES/NHANES.pdf)
* [Urban Institute Education Data Package](https://github.com/UrbanInstitute/education-data-package-r) - IPEDS, CCD, and county-level poverty rates from SAIPE
* [psidR](https://cran.r-project.org/web/packages/psidR/psidR.pdf)
* [atus](https://cran.r-project.org/web/packages/atus/atus.pdf)
* [democracyData](https://xmarquez.github.io/democracyData/index.html) - Democratic institution indicators
* [politicaldata](https://cran.r-project.org/web/packages/politicaldata/politicaldata.pdf] - US Election results

# APIs for less-common data sources
* [gtrendsR](https://cran.r-project.org/web/packages/gtrendsR/gtrendsR.pdf) - Google Trends
* [twitteR](https://cran.r-project.org/web/packages/twitteR/index.html) - Twitter
* [rsunlight](https://cran.r-project.org/web/packages/rsunlight/rsunlight.pdf) - US bill text for text analysis. Who wants to be Gentzkow?

# Also useful:
* [ipumsr](https://cran.r-project.org/web/packages/ipumsr/vignettes/ipums.html) - not an API, but once you have your own IPUMS extract this will import it

----
## Cleaning and Working with Data

* [dplyr](https://dplyr.tidyverse.org/) (by itself or as part of the tidyverse package) - If you are coming to R from pretty much any other statistics package, especially Stata, you will find this a vastly easier and more familiar way to manipulate and clean data than base R. Also see [tidyr](https://www.rdocumentation.org/packages/tidyr/versions/0.8.3) and [purrr](https://cran.r-project.org/web/packages/purrr/purrr.pdf).
* [data.table](https://cran.r-project.org/web/packages/data.table/index.html) - Better performance on large data, and works well with grouping. Does require you to learn different syntax for working with your data.
* [haven](https://cran.r-project.org/web/packages/haven/index.html) and [readxl](https://cran.r-project.org/web/packages/readxl/index.html) - Load in foreign data types of pretty much any kind you'd expect except Excel (haven), or Excel (readxl).
* [vtable](https://cran.r-project.org/package=vtable) - Restores the "Variable browser" functionality of Stata.

----
## Estimation

* [estimatr](https://cran.r-project.org/web/packages/estimatr/estimatr.pdf) - Regressions the way that economists would expect them to be done. Easily tacks on robust or cluster-robust SEs, weights, fixed effects. There are other ways to do cluster/robust SEs (`coeftest` from the `lmtest` package, or the `sandwich` package), but they're all way harder. Downside: a little new so other packages don't always play well with the output; `stargazer` in particular - use `huxreg` from `huxtable` instead.
* [car](https://cran.r-project.org/web/packages/car/index.html) - Contains all kinds of useful features, perhaps most notably `linearHypothesis` which does joint F tests following a regression, one of those "why is this not easier to do" R head-scratchers.

----
## Figures and Tables; Exporting Results
