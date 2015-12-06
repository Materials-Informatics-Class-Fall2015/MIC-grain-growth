---
layout:     slide
title:     	Pinned Grain Growth Progress Report Presentation II
date:      	2015-10-05
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

* Detailed Workflow and Data Pipeline
* Conditioning and Segmentation in Matlab (Step 1)
* 2 Point Statistics and PCA in Python (Steps 2, 3)
* Preliminary Results

{{ page.horizontal }}

## Matlab

![Picture 1]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation2/1.png)

{{ page.horizontal }}

## Image Segmentation

* Output from SPPARKS is a 27 million by one vector, reshape it to a 300X300X300 matrix.
* Each number corresponds to a grainID. Max value corresponds to a precipitate.
* We need to segment this data into our Microstructure Function.

![Picture 2]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation2/2.png)

{{ page.vertical}}

![Picture 3]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation2/3.png)

{{ page.horizontal }}

## Obtaining Grain Boundary and Precipitates

![Picture 4]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation2/4.png)

{{ page.horizontal }}

## Obtaining `.mat` files using PACE

* The issue is that the output from the filter are 3 images with 0 and 1.
* Which is desirable but we need it to change to one image with 3 distinct phases for us to input it to PyMKS.
* Made a for loop that will go through each `.dumpfile` and automatically segment it and save it as .mat file.

{{ page.horizontal }}

## Python 
 
Continuing where we left off in Matlab...

* Input: `.mat` files that only contain 0, 1, and 2 as values in an 300x300x300 array 
	* Greatly reduces memory:
	* `file.dump` (~500MB) -> `file.mat` (~3MB)

{{ page.horizontal }}

## 2 Point Statistics Conditioning

* Initial size: (300, 300, 300) per file
* Loop that pulls each 100 outputs per simulation
	* Concatenates to feed directly into PyMKS
	* (n_samples, x, y, z) = (100, 300, 300, 300) per simulation

{{ page.horizontal }}

## 2 Point Statistics Computation

* 3 phase material -> 6 correlations 
* Results in array of size (100, 300, 300, 300, 6)
	* Initially only care about one correlation: grain boundary and pins [1,2]
* After 2 point statistics computation: (100, 300, 300, 300, 1)

{{ page.horizontal }}

## 2 Point Statistics Plots

Shows 2 point statistics evolve over grain growth simulation

**Note**: Visualization issues:

1. Low volume fraction 
2. Color bar not scaled correctly by default

{{ page.vertical }}

![Picture 4]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation2/2pt1.png)

{{ page.vertical }}

![Picture 4]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation2/2pt2.png)

{{ page.vertical }}

![Picture 4]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation2/2pt3.png)

{{ page.horizontal }}

## PCA

* Forming the Data Matrix
	* Consider each 3D microstructure as long array 
	* Reshape (100, 300, 300, 300) to (100, 300^3) = (100, 27,000,000)
* SciKit Learn Randomized PCA 
	* Can specify number of PC values to output
	* Have tried: 2 and 3
		* Results in (100, 2) and (100, 3) matrix

{{ page.horizontal }}

## PCA Plots

* Final `.mat` files currently finishing on PACE
* Code pipeline is working but needs polishing
* Meaningless 2D and 3D example below

{{ page.vertical }}

![Picture 4]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation2/pca1.png)

{{ page.vertical }}

![Picture 4]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation2/pca2.png)

{{ page.horizontal }}

## Next Steps

Bring analysis and visualization into 3D.

***

1. 2 point statistics of 3D data (longer computation)
2. Visualize 3D 2 point statistics results
3. Compute 3D PCA and Plot to see a path per simulation
4. Work with David Brough to use latest fitting code to create model

<!-- End Here -->


{{ page.horizontal }}

#[Print]({{ site.url }}{{ site.baseurl }}{{ page.url }}/?print-pdf#)

#[Back]({{ site.url }}{{ site.baseurl }})

</section></section>

