---
layout:     slide
title:     	Pinned Grain Growth Progress Report Presentation IV
date:      	2015-11-23
author:     Fred Hohman, David Montes de Oca Zapiain

theme:		night # default/beige/blood/moon/night/serif/simple/sky/solarized
trans:		default # default/cube/page/concave/zoom/linear/fade/none

horizontal:	</section></section><section markdown="1" data-background="http://ahmetcecen.github.io/project-pages/img/slidebackground.png"><section markdown="1">
vertical:		</section><section markdown="1">
---
<section markdown="1" data-background="http://ahmetcecen.github.io/project-pages/img/slidebackground.png"><section markdown="1">
## {{ page.title }}

<hr>

#### {{ page.author }}

#### {{ page.date | | date: "%a, %b %d %Y"}}

{{ page.horizontal }}

<!-- Start Writing Below in Markdown -->

## Outline

* Updated Segmentation
* PCA Input Plots
* PCA Output Plots
* Preliminary Regression Results
* What's Next?

{{ page.horizontal}}

## David Stuff

{{ page.horizontal}}

## PCA Input

* PACE job using 64GB of memory
* Data matrix size (n_simulations,27000000) where n_simulations=220
* 220 is the total number of simulations we were able to perform during semester

{{ page.vertical}}

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation4/pca-in-1.png)

{{ page.vertical}}

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation4/pca-in-2.png)

{{ page.vertical}}

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation4/pca-in-3.png)

{{ page.horizontal}}

## PCA Input Screen Plot

* More than 95% variance captured in first 5 PC values

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation4/pca-in-scree.png)

{{ page.horizontal }}

## PCA Output

* Chord length distributions (in general) cleaned up after new segmentation code
* Data matrix size (n_simulations, 299) where n_simulations=220

{{ page.vertical}}

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation4/pca-out-1.png)

{{ page.vertical}}

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation4/pca-out-2.png)

{{ page.vertical}}

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation4/pca-out-3.png)

{{ page.horizontal}}

## PCA Output Screen Plot

* More than 95% variance captured in first 3 PC values

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation4/pca-out-scree.png)

{{ page.horizontal}}

## Preliminary Regression Info

* We now have two `.m` files containing our PC values for both the inputs and outputs of our model
* Used "hacked" Scikit-Learn/PyMKS module to perform linear regression on our PC values
* **Challenge**: we essentially have the first and final time-step in a time series evolution and we are trying to predict structure given a new input
* We can calculate the `R-square` value for a give combination of polynomial degree and number of PC values used
    * Can create plot showing all combinations of a given set of values in `degree` and `n_components`

(Thanks David Brough!)

{{ page.vertical }}

### Preliminary Regression I

* Using only random simulations (108)

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation4/gs-1.png)

{{ page.vertical }}

**Output Results**

```
Order of Polynomial 2
Number of Components 2
R-squared Value 0.888655863884
```

{{ page.vertical }}

### Preliminary Regression II

* Using all simulations (220)

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation4/gs-2.png)

{{ page.vertical }}

**Output Results**

```
Order of Polynomial 2
Number of Components 3
R-squared Value 0.708516065498
```

## Next Steps

1. Regression discussion
2. Build process-structure linkage
3. Decide where to stop for class and what to improve for Spring semester and Materials Data Challenge

{{ page.horizontal }}

# Questions or Suggestions?

<!-- End Here -->


{{ page.horizontal }}

#[Print]({{ site.url }}{{ site.baseurl }}{{ page.url }}/?print-pdf#)

#[Back]({{ site.url }}{{ site.baseurl }})

</section></section>

