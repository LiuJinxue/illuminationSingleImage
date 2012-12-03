This code implements the single-image illumination estimation technique
introduced in 

J.-F. Lalonde, A. A. Efros, and S. G. Narasimhan, "Estimating the Natural 
Illumination Conditions from a Single Outdoor Image," International 
Journal of Computer Vision, vol. 98, no. 2, pp. 123--145, Jun. 2012.

Please cite this paper if you use this code in your work.

Getting started
===============

1.  First, make sure you download the required software packages described below.
2.  From the MATLAB command prompt in the `mycode` directory, run

        $ setPath
        $ demoEstimateIllumination

3.  Results should display automagically!


Requirements
============

* MATLAB's optimization toolbox

Requires some of my software packages (available on github):

* My [utils](http://www.github.com/jflalonde/utils) package;
* My [skyModel](http://www.github.com/jflalonde/skyModel) package;
* My [shadowDetection](http://www.github.com/jflalonde/shadowDetection) package;

Requires the following 3rd-party libs (included):

* [LibSVM](http://www.csie.ntu.edu.tw/~cjlin/libsvm), included in `3rd_party/libsvm-mat-3.0-1`;
* [Felzenszwalb et al. object detector](http://www.cs.uchicago.edu/~pff/latent) [1], included in `3rd_party/voc-release3.1`;
* [Piotr Dollar's image processing toolbox](http://vision.ucsd.edu/~pdollar/toolbox/doc/), included in `3rd_party/piotr_toolbox`.
* [Video Compass code from Derek Hoiem](http://www.cs.illinois.edu/homes/dhoiem/), included in `3rd_party/hoiemVideoCompass`;

For the paths to work "out of the box", create yourself a base directory 
(e.g. `projects`), and download all of the packages in that directory. For
example, `projects/utils`, `projects/skyModel`, `projects/illuminationSingleImage`...
The `setPath` function should be able to find them. 

Information needed 
------------------

* focal length (can be obtained from EXIF);
* geometric context results, code available from [Derek Hoiem's website](http://www.cs.illinois.edu/homes/dhoiem);
* detected ground shadow boundaries, code available from [my website](http://www.jflalonde.org/software.html).


Compilation
===========

Compile the object detector: 

* go to `3rd_party/voc-release3.1` from inside matlab, and run 'compile'

Compile the lib-svm

* go to `3rd_party/libsvm-mat-3.0-1` from inside matlab, and run 'make'


Notes
=====

1. By default, this code uses the ICCV'09 version to estimate the probability 
of the sun given the sky cue, my previous implementation seems to give better
results. 

2. If you experience problems with libsvm version 3.0.1, replace the `svm_model_matlab.c` file with the following: https://github.com/tomz/libsvm-ruby-swig/blob/master/libsvm-3.1/matlab/svm_model_matlab.c. Make sure that the `NUM_OF_RETURN_FIELD` macro is set to 10. Recompile libsvm after making this change. 
*Thanks heaps to Swaminathan Sankaranrayanan for pointing this out!*


References
==========

[1]	P. Felzenszwalb, D. McAllester, and D. Ramanan, "A discriminatively 
trained, multiscale, deformable part model," presented at the IEEE 
Conference on Computer Vision and Pattern Recognition, 2008.