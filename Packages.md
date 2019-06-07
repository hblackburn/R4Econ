----
# R Packages for Econs and Stata Emigrees

There are more R packages than stars in the sky. But many of them are written without economics in mind. There are also just some things you miss about Stata, and being able to do them in R would make things so much easier!

This page will not attempt to list every potentially useful package under the sun, but will try to cover things that econs may find useful. Please do not add packages to this list if you don't think there's a reasonable chance they could be used in an economics paper.

Note that some included packages are not on CRAN and must be installed with `devtools::install_github()`.

----
# Procuring Data

## APIs for common data sources:
* [wbstats](https://cran.r-project.org/web/packages/wbstats/wbstats.pdf) and [data360r](https://tcdata360.worldbank.org/tools/data360r) - World Bank. Also see [ITNr](https://github.com/MatthewSmith430/ITNr) for getting and cleaning World Bank WITS data for trade analysis
* [tidycensus](https://cran.r-project.org/web/packages/tidycensus/tidycensus.pdf) - US Census and ACS, plus US map shape files
* [tidyquant](https://cran.r-project.org/web/packages/tidyquant/index.html), [quantmod](https://cran.r-project.org/web/packages/quantmod/index.html), and [fredr](https://cran.r-project.org/web/packages/fredr/vignettes/fredr.html) - Finance data and everything on FRED. Tidyquant and quantmod have access to more sources, but fredr is easier to use. See [this StackExchange question](https://stackoverflow.com/questions/12590180/inflation-adjusted-prices-package) for code that will let you use these to very easily CPI-adjust any data you have
* [NHANES](https://cran.r-project.org/web/packages/NHANES/NHANES.pdf)
* [Urban Institute Education Data Package](https://github.com/UrbanInstitute/education-data-package-r) - IPEDS, CCD, and county-level poverty rates from SAIPE
* [psidR](https://cran.r-project.org/web/packages/psidR/psidR.pdf)
* [atus](https://cran.r-project.org/web/packages/atus/atus.pdf)
* [democracyData](https://xmarquez.github.io/democracyData/index.html) - Democratic institution indicators
* [politicaldata](https://cran.r-project.org/web/packages/politicaldata/politicaldata.pdf) - US Election results

## APIs for less-common data sources
* [gtrendsR](https://cran.r-project.org/web/packages/gtrendsR/gtrendsR.pdf) - Google Trends
* [twitteR](https://cran.r-project.org/web/packages/twitteR/index.html) - Twitter
* [rsunlight](https://cran.r-project.org/web/packages/rsunlight/rsunlight.pdf) - US bill text for text analysis. Who wants to be Gentzkow?
* [Guide to Client-Side APIs](https://raw.githack.com/uo-ec607/lectures/master/07-web-apis/07-web-apis.html) by Grant McDermott. Guide for using APIs that don't have their own R packages

## Also useful:
* [ipumsr](https://cran.r-project.org/web/packages/ipumsr/vignettes/ipums.html) - not an API, but once you have your own IPUMS extract this will import it

----
# Cleaning and Working with Data

* [dplyr](https://dplyr.tidyverse.org/) (by itself or as part of the tidyverse package) - If you are coming to R from pretty much any other statistics package, especially Stata, you will find this a vastly easier and more familiar way to manipulate and clean data than base R. Also see [tidyr](https://www.rdocumentation.org/packages/tidyr/versions/0.8.3) and [purrr](https://cran.r-project.org/web/packages/purrr/purrr.pdf) for more useful, linked, functions, and [dbplyr](https://cran.r-project.org/web/packages/dbplyr/index.html) for working with on-disk databases.
* [data.table](https://cran.r-project.org/web/packages/data.table/index.html) - Better performance on large data than `dplyr`, and has grouping naturally built in. Does require you to learn its rather-different syntax. See [this handy guide](https://atrebas.github.io/post/2019-03-03-datatable-dplyr/) comparing the two, and making the case for `data.table`
* [haven](https://cran.r-project.org/web/packages/haven/index.html) and [readxl](https://cran.r-project.org/web/packages/readxl/index.html) - Load in foreign data types from other main statistics packages (haven), or Excel (readxl). If those don't cover your types maybe try [foreign](https://cran.r-project.org/web/packages/foreign/foreign.pdf).
* [reshape2](https://cran.r-project.org/web/packages/reshape2/reshape2.pdf) - There are many different R reshape (wide-to-long and long-to-wide) functions. Base-`reshape`, `melt`/`cast`/`dcast`, `gather`/`spread`, I like the new `pivot_wider`/`pivot_longer` functions in the dev version of `tidyr`. Take your pick.
* [lubridate](https://cran.r-project.org/web/packages/lubridate/index.html) - Makes working with date variables easier
* [stringr](https://stringr.tidyverse.org/) - Makes working with string data easier
* [forcats](https://forcats.tidyverse.org/) - Makes working with factor variables easier
* [dummies](https://cran.r-project.org/web/packages/dummies/) - Easy creation of dummy variables. Note you can generally avoid *having* to make dummy variables by just doing `factor(variableyouwantdummiesof)` in your regression.
* [vtable](https://cran.r-project.org/package=vtable) - Restores the "Variable browser" functionality of Stata.

----
# Estimation

(alphabetized due to numerosity)

* [car](https://cran.r-project.org/web/packages/car/index.html) - Contains all kinds of useful features, perhaps most notably `linearHypothesis` which does joint F tests following a regression, one of those "why is this not easier to do" R head-scratchers.
* [censReg](https://cran.r-project.org/web/packages/censReg/index.html) - does anyone still do Tobit? 
* [dynlm](https://cran.r-project.org/web/packages/dynlm/dynlm.pdf) - Dynamic linear modeling for time series
* [estimatr](https://cran.r-project.org/web/packages/estimatr/estimatr.pdf) - Regressions the way that economists would expect them to be done. Easily tacks on robust or cluster-robust SEs, weights, fixed effects. There are other ways to do cluster/robust SEs (`coeftest` from the `lmtest` package, or the `sandwich` package), but they're all way harder. Downside: a little new so other packages don't always play well with the output; `stargazer` in particular - use `huxreg` from `huxtable` instead.
* [erer](https://cran.r-project.org/package=erer) - Support for AIDS model estimation, plus marginal effects for various nonlinear models, most notably ordered probit/logit
* [forecast](https://cran.r-project.org/web/packages/forecast/index.html) - Forecasting tools for time series
* [glmnet](https://cran.r-project.org/web/packages/glmnet/glmnet.pdf) - Regularized regression
* [gravity](https://cran.r-project.org/web/packages/gravity/index.html) - Estimation of gravity trade models
* [ivprobit](https://cran.r-project.org/web/packages/ivprobit/index.html) - Guess what this package does
* [lfe](https://cran.r-project.org/web/packages/lfe/lfe.pdf) - Focuses on complex fixed-effects models. Can be more powerful 
* [MCMCpack](https://cran.r-project.org/package=MCMCpack) - Package for estimating MCMC models
than `estimatr` in some contexts
* [mfx](https://cran.r-project.org/web/packages/mfx/vignettes/mfxarticle.pdf) - Marginal effects for nonlinear models
* [mlogit](https://cran.r-project.org/web/packages/mlogit/index.html) - Estimates multinomial logit models, including McFadden alternative-specific models
* [plm](https://cran.r-project.org/web/packages/plm/plm.pdf) - Standard panel data modeling options, including lags
* [quantreg](https://cran.r-project.org/web/packages/quantreg/index.html) - Quantile regression
* [randomForest](https://www.rdocumentation.org/packages/randomForest/versions/4.6-14) - For random forests, naturally. Note [this](http://philipppro.github.io/More_complete_list/) useful rundown comparing `randomForest` to other, potentially more modern, random forest packages.
* [tseries](https://cran.r-project.org/web/packages/tseries/index.html) - A number of useful estimators and tools for working with time series
* [zoo](https://cran.r-project.org/web/packages/zoo/index.html) - Even more useful time series tools

----
# Figures and Tables; Exporting Results

* [ggplot2](https://ggplot2.tidyverse.org/) (by itself or as a part of the tidyverse package) - It looks good, it's not as hard as it seems. Just use it, okay? It looks so, so good. Plus there are about a million extensions of it to make just about any kind of graphics you can imagine. 
* [rmarkdown](https://cran.r-project.org/web/packages/rmarkdown/index.html) - For creating reproducible notebooks and presentations with your results
* [stargazer](https://cran.r-project.org/web/packages/stargazer/stargazer.pdf) - Makes summary statistics tables and regression tables for text, HTML (which can be copy-pasted to Word), or LaTeX that look exactly like an economist would expect them to. 
* [huxtable](https://cran.r-project.org/web/packages/huxtable/index.html) - A little harder to use than `stargazer` and doesn't adhere to economics standards (you'll probably at least be changing the significance stars), but works with some of the modern data/regression types that `stargazer` won't.

## Maps
* [ggmap](https://cran.r-project.org/web/packages/ggmap/ggmap.pdf) - Mapping utility for use with `ggplot`.
* [mapdata](https://www.rdocumentation.org/packages/mapdata/versions/2.3.0) - What, were you going to draw the thing yourself?
* [fiftystater](https://github.com/cran/fiftystater) - This package exists just for the purpose of making fifty-state US maps, specifically for the purpose of moving Alaska and Hawaii where you can see them
