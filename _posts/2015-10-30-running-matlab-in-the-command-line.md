---
layout:     post
title:      Running Matlab in the Command Line
date:       2015-10-30
author:     Fred Hohman
---

Our project has been making use of [PACE][pace], a supercomputer here on Tech's campus, to generate data. We now have a lot of it. I haven't really counted but it's well over dozens of GBs. Furthermore, we have been doing some data segmentation and processing in Matlab. We don't want to download all of our data to run these `.m` scripts, so we needed a way to run Matlab on PACE.

Ideally we could run a Matlab script and submit it as a job to PACE instead of running Matlab in an interactive shell, since many things can disrupt an interactive shell that would cancel the computation.

Turns out submitting a `.m` script as a job on PACE is much easier than expected. I don't know if any other group will ever need this, but I've never used Matlab in the command line before but have found it useful and helpful to do so, and I imagine I'll do it again sometime in the future.

Below is the full script I used. This file is called `mat-generation.pbs` and generated .mat files from our raw data files from the simulations. Feel free to adapt it to you needs, such as changing the name, amount of memory, and replacing my email address with yours so that you will be notified upon the start and end of the job being submitted. 

	# mat-generation
	#PBS -N mat-generation
	#PBS -l nodes=1:ppn=1
	#PBS -l pmem=8gb
	#PBS -l walltime=12:00:00
	#PBS -q iw-shared-6
	#PBS -j oe
	#PBS -o matlog
	#PBS -m abe
	#PBS -M fredhohman@gatech.edu

	cd /nv/hp22/fhohman3/scratch/Random/Random/rod1_2/
	module load matlab
	matlab -r "Obtainin_Grain_boundary_as_3phase"

So in general your script might look something more like this:

	# your-job-name
	#PBS -N your-job-name
	#PBS -l nodes=1:ppn=1
	#PBS -l pmem=8gb
	#PBS -l walltime=12:00:00
	#PBS -q iw-shared-6
	#PBS -j oe
	#PBS -o matlog
	#PBS -m abe
	#PBS -M your-username@gatech.edu

	cd /nv/hp22/username/your/script/destination/here/
	module load matlab
	matlab -r "your-matlab-script-name"

Then to submit the job all you do is type
	qsub mat-generation.pbs
or in your case
	qsub your-job-name.pbs
and you are good to go!

You'll get an email when it starts running and when it finishes. If something breaks inside the code the output and errors will be written to a file called `matlog` that you can read to see what went wrong.


[pace]: http://www.pace.gatech.edu