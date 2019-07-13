
<!-- README.md is generated from README.Rmd. Please edit that file -->

# ymlthis: write YAML for R Markdown, bookdown, blogdown, and more

<!-- badges: start -->

[![Codecov test
coverage](https://codecov.io/gh/malcolmbarrett/ymlthis/branch/master/graph/badge.svg)](https://codecov.io/gh/malcolmbarrett/ymlthis?branch=master)
[![AppVeyor build
status](https://ci.appveyor.com/api/projects/status/github/malcolmbarrett/ymlthis?branch=master&svg=true)](https://ci.appveyor.com/project/malcolmbarrett/ymlthis)
<!-- badges: end -->

ymlthis makes it easy to write YAML front matter for R Markdown and
related documents. `yml_*()` functions write functions and `use_*()`
functions let you write the resulting YAML to your clipboard or to
`.yaml` files related to your project.

## Installation

You can install the development version of ymlthis from GitHub with:

``` r
# install.packages("remotes")
remotes::install_github("rstudio-education/ymlthis")
```

## Example

`yml()` creates a basic `yml` object returns simple YAML with the author
and date.

``` r
library(ymlthis)

yml()
#> ---
#> author: Malcolm Barrett
#> date: '`r format(Sys.Date())`'
#> ---
```

ymlthis supports many YAML arguments, with YAML-generating functions
prefixed with `yml_*()`:

``` r
yml() %>% 
  yml_author(c("Yihui Xie", "Hadley Wickham"), affiliation = "RStudio") %>% 
  yml_date(lubridate::today()) %>% 
  yml_output(
    pdf_document(keep_tex = TRUE, includes = includes2(after_body = "footer.tex")), 
    bookdown::html_document2()
  ) %>% 
  yml_latex_opts(biblio_style = "apa-like")
#> ---
#> author:
#> - name: Yihui Xie
#>   affiliation: RStudio
#>   '': Yihui Xie
#>   '': RStudio
#> - name: Hadley Wickham
#>   affiliation: RStudio
#>   '': Hadley Wickham
#>   '': RStudio
#> date: '2019-07-13'
#> output:
#>   pdf_document:
#>     keep_tex: true
#>     includes:
#>       after_body: footer.tex
#>   bookdown::html_document2: default
#> biblio-style: apa-like
#> ---
```
