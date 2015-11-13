---
layout:     post
title:      Meeting with the Domain Experts
date:       2015-11-11
author:     David Montes de Oca Zapiain
---

The purpose of this new blog post is to brief our readers regarding the meeting we had with the domain experts in this field.
The domain experts in the field of simulating grain growth with Kinetic Montecarlo equations are the scientist at ([SANDIA national lab] [SANDIA national lab]), we had the great opportunity to present our project and progress to ([John A. Mitchell] [John A. Mitchell]), he is a Computational Scientist in the area of Multiscale Modelling. 

He was deeply interested on our project and he gave some great insight on how to proceed as well as some advice on how to avoid some possible mistakes and on how to test the validity of our suggested surrogate model. 


The key outcomes of the meeting are summarized in the following list:


•	Suggested more classes to add to our model. Specifically one that could depict rolling, also he suggested to consider maybe a combination of the current classes to add more variety to the state space. 

•	Suggested using extreme cases to find the limitations of our model. He made a note specifically in the case of degeneracies. An example of those degeneracies are the precipitates of one voxel length, since he mentioned that probably those precipitates would not “pin” the grain growth that much. 


•	Suggested that for validation test a case were the answer is known and then extrapolate to one in which the answer is not known.

•	He also suggested some future work to consider for when we continue the project after the class ends. This suggestions include changing the Temperature at which the grain growth is simulated.

Taking its suggestion in mind we have started to modify some steps in our pipeline. 


The first modification made was that at this point we were able to generate a class that simulates the rolling condition. This was achieved by placing uniformly in the X-Y plane randomly selected pins, this simulates the elongation of the grains present during rolling. Also we placed this uniformly distributed planes randomly in the Z direction. This new class looks the following.




The second modification we did consisted in adding a random selection of precipitates shapes to the random distribution and perform more simulations with these new upgraded random distribution. It is important to mention that we will still take into account the ones we performed earlier, this step is performed to expand our state space and hence our calibration set.



Finally we started thinking of possible validation cases so please be on the lookout for those posts since we will be updating you regarding this issue.


[SANDIA national lab]:http://www.sandia.gov/
[John A. Mitchell]:https://cfwebprod.sandia.gov/cfdocs/CompResearch/templates/insert/profile.cfm?snl_id=13850
