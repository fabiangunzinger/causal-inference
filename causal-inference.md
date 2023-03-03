--- 
title: "A Minimal Book Example"
author: "Yihui Xie"
date: "2023-03-03"
site: bookdown::bookdown_site
output: bookdown::gitbook
documentclass: book
bibliography: [book.bib, packages.bib]
biblio-style: apalike
link-citations: yes
github-repo: rstudio/bookdown-demo
description: "This is a minimal example of using the bookdown package to write a book. The output format for this example is bookdown::gitbook."
---

# Prerequisites

This is a _sample_ book written in **Markdown**. You can use anything that Pandoc's Markdown supports, e.g., a math equation $a^2 + b^2 = c^2$.

The **bookdown** package can be installed from CRAN or Github:


```r
install.packages("bookdown")
# or the development version
# devtools::install_github("rstudio/bookdown")
```

Remember each Rmd file contains one and only one chapter, and a chapter is defined by the first-level heading `#`.

To compile this example to PDF, you need XeLaTeX. You are recommended to install TinyTeX (which includes XeLaTeX): <https://yihui.name/tinytex/>.



<!--chapter:end:index.Rmd-->

# Introduction {#intro}

You can label chapter and section titles using `{#label}` after them, e.g., we can reference Chapter \@ref(intro). If you do not manually label them, there will be automatic labels anyway, e.g., Chapter \@ref(methods).

A little test.

Figures and tables with captions will be placed in `figure` and `table` environments, respectively.


```r
par(mar = c(4, 4, .1, .1))
plot(pressure, type = 'b', pch = 19)
```

<div class="figure" style="text-align: center">
<img src="01-intro_files/figure-html/nice-fig-1.png" alt="Here is a nice figure!" width="80%" />
<p class="caption">(\#fig:nice-fig)Here is a nice figure!</p>
</div>

Reference a figure by its code chunk label with the `fig:` prefix, e.g., see Figure \@ref(fig:nice-fig). Similarly, you can reference tables generated from `knitr::kable()`, e.g., see Table \@ref(tab:nice-tab).


```r
knitr::kable(
  head(iris, 20), caption = 'Here is a nice table!',
  booktabs = TRUE
)
```



Table: (\#tab:nice-tab)Here is a nice table!

| Sepal.Length| Sepal.Width| Petal.Length| Petal.Width|Species |
|------------:|-----------:|------------:|-----------:|:-------|
|          5.1|         3.5|          1.4|         0.2|setosa  |
|          4.9|         3.0|          1.4|         0.2|setosa  |
|          4.7|         3.2|          1.3|         0.2|setosa  |
|          4.6|         3.1|          1.5|         0.2|setosa  |
|          5.0|         3.6|          1.4|         0.2|setosa  |
|          5.4|         3.9|          1.7|         0.4|setosa  |
|          4.6|         3.4|          1.4|         0.3|setosa  |
|          5.0|         3.4|          1.5|         0.2|setosa  |
|          4.4|         2.9|          1.4|         0.2|setosa  |
|          4.9|         3.1|          1.5|         0.1|setosa  |
|          5.4|         3.7|          1.5|         0.2|setosa  |
|          4.8|         3.4|          1.6|         0.2|setosa  |
|          4.8|         3.0|          1.4|         0.1|setosa  |
|          4.3|         3.0|          1.1|         0.1|setosa  |
|          5.8|         4.0|          1.2|         0.2|setosa  |
|          5.7|         4.4|          1.5|         0.4|setosa  |
|          5.4|         3.9|          1.3|         0.4|setosa  |
|          5.1|         3.5|          1.4|         0.3|setosa  |
|          5.7|         3.8|          1.7|         0.3|setosa  |
|          5.1|         3.8|          1.5|         0.3|setosa  |


```r
library("reticulate")
Sys.which("python")
```

```
## python 
##     ""
```

```r
use_python("/Users/fabian.gunzinger/.pyenv/versions/bookdown/bin/python3.9")
Sys.which("python")
```

```
## python 
##     ""
```


```python
import pandas as pd

pd.DataFrame({'a': [1, 2, 3], 'b': [3, 4, 5]})
```

```
##    a  b
## 0  1  3
## 1  2  4
## 2  3  5
```


You can write citations, too. For example, we are using the **bookdown** package [@R-bookdown] in this sample book, which was built on top of R Markdown and **knitr** [@xie2015].

<!--chapter:end:01-intro.Rmd-->

# Literature

Here is a review of existing methods.

<!--chapter:end:02-literature.Rmd-->

# Methods

We describe our methods in this chapter.

Math can be added in body using usual syntax like this 

## math example

$p$ is unknown but expected to be around 1/3. Standard error will be approximated

$$
SE = \sqrt(\frac{p(1-p)}{n}) \approx \sqrt{\frac{1/3 (1 - 1/3)} {300}} = 0.027
$$
You can also use math in footnotes like this^[where we mention $p = \frac{a}{b}$].

We will approximate standard error to 0.027[^longnote]

[^longnote]: $p$ is unknown but expected to be around 1/3. Standard error will be approximated

    $$
    SE = \sqrt(\frac{p(1-p)}{n}) \approx \sqrt{\frac{1/3 (1 - 1/3)} {300}} = 0.027
    $$

<!--chapter:end:03-method.Rmd-->

# Applications

Some _significant_ applications are demonstrated in this chapter.

## Example one

## Example two

<!--chapter:end:04-application.Rmd-->

# Final Words

We have finished a nice book.

<!--chapter:end:05-summary.Rmd-->


# References {-}


<!--chapter:end:06-references.Rmd-->

# Causal Inference

## Sources of bias

From @king2006dangers, section 3.2 onwards

1. Omitted variable bias
2. Posttreatment bias (including variables in X that are result of T)
3. Interpolation bias ()
4. Extrapolation bias


## Regression discontinuity designs

### Use cases

- Identifiable forcing variable

### Considerations

- Functional form: use local linear methods

- Choice of bandwidth: use asymptotic expansion

- Assessing  (internal) validity: use suplementary analysis

- Assessing external validity: assess credibility of extrapolation to other subpopulations

Notes based on @athey2017state


## Synthetic control methods

### Use case

- The classic use case is a setting where a single aggregated unit (school district, city, region, country) has been treated and we have data on a relatively small number of possible comparison units. In such a case, synthetic control creates a control unit as a weighted average of the available comparison units, which can result in a better control group than if a single such unit were used as a control (as in a traditional DiD setting).

### Considerations

- Weighing function to create controls: @abadie2010synthetic use minimal distance, @doudchenko2016balancing use show that alternatives like best subset regression, LASSO, and elastic nets perform better in settings with a large number of potential control units.

- Functional form: @athey2006identificaiton provide non-linear alternative.


### R packages

- [Synth](https://dspace.mit.edu/handle/1721.1/71234) R implementation by Abadie and co-authors.

- [tidysynth](https://github.com/edunford/tidysynth) Nice looking improved implementation of Synth


## Matching

### Aim and use case

- Preprocess observational data such that it resembles more closely data that would have resulted from a perfectly blocked (and possibly randomised) experiment, and thus break the relationship between outcomes and pre-treatment controls.

### Considerations

- Balance checks: successful matching removes the relationship between outcomes and pre-treatment controls that's often inherent in non-experimental data. To check whetehr this succeeded, we need to check that the distribution of pre-treatment controls is the same within matched treatment and control units.

- Analysis: using difference in mean test is only appropriate if we performed exact matching, which is often not feasible. For all other forms of matching, use model with controls to estimate treatment effects.

### Software

- @stuart2011matchit


## Matching vs synthetic controls vs regression

Based on excellent discussion in introduction to @abadie2021penalized.

Synthetic control vs nearest-neighbour matching:

- Similarities: Weights for control units are positive, sum to one, and are often sparse. This allows for interpretability of the weights.

- Differences: synthetic control doesn't impose a fixed number of control units, and, instead of using a simple average of the control units with equal weights, it creates a control unit using a weighted average of all control units such as to minimise the discrepancy between treated and control units in the values of the matching variables.


Synthetic control vs regression:

  - Similarities: both effectively use weights

- Regression weights are implicit and much harder to interpret.

<!--chapter:end:09-causal-inference.Rmd-->

