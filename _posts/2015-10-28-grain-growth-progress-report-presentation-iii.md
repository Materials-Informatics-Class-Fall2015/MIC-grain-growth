---
layout:     slide
title:     	Pinned Grain Growth Progress Report Presentation III
date:      	2015-10-28
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

#### {{ page.date | | date: "%I %M %p ,%a, %b %d %Y"}}

{{ page.horizontal }}

<!-- Start Writing Below in Markdown -->

## Outline

*

{{ page.horizontal }}

## So, Our Input PCA Data Matrix...

* Remember our data matrix from presentational II?
* Size: (n_simulations, 300^3) => (112, 27000000)

{{ page.vertical }}

## So, Our Input PCA Data Matrix...

* That's big (*really* big)
* We need a better way to work with this
	* Suggestions welcomed
	* Planning to talk to Ahmet about recent reduction work
	* 2pt statistics in 2D tappers off, expect similar feature in 3D

{{ page.horizontal }}

## Some Preliminary PCA Results 

* Main issue in 3D 2pt statistics of 300^3 microstructure is memory
* Original idea using personal computer not sufficient
* Use PACE: few example runs

{{ page.vertical }}

* 1 case (specific pin shape, pin percentage) for 10 time-steps
* Can already see converging to steady state by clustering of data points

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation3/pca-10ms-pace.png)

{{ page.vertical }}

* 3 cases varying pin shape for given percentage for 6 time-steps
* Can see path in PCA space as microstructure evolves

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation3/pca-3ms-pace-1.png)

{{ page.vertical }}

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation3/pca-3ms-pace-3.png)

{{ page.horizontal }}

## Attempt of PCA on Chord Length Distribution

* Example of what **not** to do
* PCA on chord length distribution without normalization

![Picture]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation3/pca-chord-wrong.png)

## Next Steps

1. Determine appropriate truncation of microstructure data to perform PCA without the need for large amounts of memory
	* Talking to Ahmet
2. Gather all chord length distribution data
	* Quick computation
3. Run PCA on normalized chord length data
4. Work with David Brough to use latest fitting code to create **process-structure model**

{{ page.horizontal }}

# Questions or Suggestions?


<!-- End Here -->


{{ page.horizontal }}

#[Print]({{ site.url }}{{ site.baseurl }}{{ page.url }}/?print-pdf#)

#[Back]({{ site.url }}{{ site.baseurl }})

</section></section>

