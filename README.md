
<!-- README.md is generated from README.Rmd. Please edit that file -->

# parameterpal

<!-- badges: start -->

<!-- badges: end -->

Rather than knowing intrinsically what parameters are required for a
distribution, scientists tend to have a sense of what value they
*expect* a measure to take, *how many* observations should fall *within*
a certain distance of that value.

For the normal distribution, this is straightforward, as the parameters
reflect the expected value and variance. However, for the beta
distribtuion, the parameters are not so readily interpretable.

`parameterpal::` provides a means of obtaining the parameters required
for the beta distribution from interpretable conditions. \#\#
Installation

``` r
devtools::install_github("softloud/parameterpal")
```

## intended user

This package was developed for a friend and collaborator, computational
ecologist Dr Matthew Grainger, who previously used browser-based tools
to obtain beta parameters to inform his rstats workflow. I hope he finds
this package a useful augment to his codeflow.

# using `parameterpal::`

Load the package.

``` r
library(parameterpal)
```

Suppose we expect a value of 0.3, with 80 per cent of observations
falling within a distance of 0.2 from 0.3. That is, we expect 90 per
cent of observations to fall within (0.1, 0.5). Assuming data follow a
beta distribution, what are its parameters?

``` r

beta_pal(expected_value = 0.3,
         this_much = 0.8,
         within = 0.2)
#> $shape1
#> [1] 7.575
#> 
#> $shape2
#> [1] 17.675
```

We can plot this intuition to see the shape of the resulting beta
distribution.

``` r
beta_plot(
  expected_value = 0.3,
         this_much = 0.8,
         within = 0.2
)
```

<img src="man/figures/README-unnamed-chunk-5-1.png" width="100%" />

Escaping the ubiquitous tyranny of the arbitary bounds 90 or 95 per
cent, which don’t necessarily reflect our intuituion, suppose we thought
only 30 per cent of values fall within the interval.

``` r
beta_plot(
  expected_value = 0.3,
         this_much = 0.3,
         within = 0.2
)
```

<img src="man/figures/README-unnamed-chunk-6-1.png" width="100%" />

# vignette

See `vignette("beta_pal")` for more information, and the mathematical
derivations.

# other distributions

No reason the same math can’t be applied to other distributions. Open an
issue if you’d like me to provide parameters from interpretable
conditions for another distributions.
