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

* Meeting with domain experts outcome
* Image segmentation revisited
* Chord length distribution expanded

* PCA input plots
* PCA output plots
* Preliminary regression results
* What's next?

{{ page.horizontal}}

## Outcome from Meeting with Domain Experts

* Meeting with a computational scientist in the area of multiscale modeling @ Sandia National Lab. 

* Extremely useful meeting after which we added 2 more classes to the current simulation pool we had before. 

{{ page.horizontal}}

## Images of New Classes Added

**Rolling:**

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation4/david-1.png)

{{ page.vertical}}

## Images of New Classes Added

**Random Distribution with Random Shapes Class:**

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation4/david-2.png)

{{ page.horizontal}}

## Obtaining Grain Boundary and Precipitates Revisited

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation4/david-3.png)

{{ page.horizontal}}

## Obtaining Grain Boundary and Precipitates Revisited

* Image of old image segmentation algorithm

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation4/david-4.png)

{{ page.horizontal}}

## Obtaining Grain Boundary and Precipitates Revisited

* Image of new image segmentation algorithm

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation4/david-5.png)

{{ page.horizontal}}

## Chord Length Distribution Extraction Expanded

* First decided to not use the average Chord Length distribution. 
* We normalized the distribution such that the area under the curve is equal to 1. 
* At this point this chord length tells us the probability of finding a chord of length “X” within our MS, nevertheless it is not enough.
* We needed to add something that accounts, “weighs” more the chords of bigger size.

{{ page.horizontal}}

## Chord Length Distribution Extraction Expanded

* Thus by multiplying the frequency of each chord by its size and normalizing it again, the bigger chords now have a "bigger weight" in the distribution.

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation4/david-6.png)

## PCA Input Subset

* To start with, consider a data matrix of size (`n_simulations`,27000000) where `n_simulations`=108
    * Only looking at randomly distributed pins
    * 6 different percentages
    * 3 different shapes

{{ page.vertical}}

* Notice the distinct 3 paths of 6 points each in 6 point clusters

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation4/pca-in-sub-1.png)

{{ page.vertical}}

* Notice the distinct 3 paths of 6 points each in 6 point clusters

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation4/pca-in-sub-2.png)

{{ page.horizontal}}

## PCA Input

* PACE job using 64GB of memory
* Data matrix size (`n_simulations`,27000000) where `n_simulations`=220
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
* Data matrix size (`n_simulations`, 299) where `n_simulations`=220

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

### Output Results

* Order of Polynomial: 2
* Number of Components: 2
* R-squared Value: 0.888655863884

{{ page.vertical }}

### Preliminary Regression II

* Using all simulations (220)

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation4/gs-2.png)

{{ page.vertical }}

### Output Results

* Order of Polynomial: 2
* Number of Components: 3
*: R-squared Value: 0.708516065498

{{ page.horizontal }}

## Next Steps

1. Regression discussion
2. Improve process-structure linkage
3. Decide where to stop for class and what to improve for Spring semester and Materials Data Challenge

{{ page.horizontal }}

# Questions or Suggestions?

<!-- End Here -->


{{ page.horizontal }}

#[Print]({{ site.url }}{{ site.baseurl }}{{ page.url }}/?print-pdf#)

#[Back]({{ site.url }}{{ site.baseurl }})

</section></section>

