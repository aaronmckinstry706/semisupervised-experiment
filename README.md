# kaggle-invasive-species

This code is for the Kaggle competition [Invasive Species Monitoring](https://www.kaggle.com/c/invasive-species-monitoring). I'm attempting to build off of my previous attempt at a competition with a very small training dataset ([The Nature Conservancy Fisheries Monitoring](https://www.kaggle.com/c/the-nature-conservancy-fisheries-monitoring); the code for that is also on GitHub). 

In my previous competition, my main goal was to get used to using some tools:
* Keras (for data preprocessing),
* Theano (for constructing different neural nets),
* matplotlib (for graphing network performance and other metrics),
* gradient norm and training/validation performance for debugging the network,
* and multithreading/iterators in python. 
In addition, I attempted to develop a decent architecture from scratch in order to get a feel for debugging the network optimization process: was it overfitting, underfitting? Should it be deeper, shallower, wider? Etc., etc. For this reason, I never tried using some existing architectures from the latest literature, as the winners did. 

However, I could never get good validation performance, regardless of which architecture I attempted---nor very good training performance! My mistake was twofold:
1. my architectures were not deep enough, and
2. I didn't try using pre-trained networks or auxiliary data. 

In my architectures and training methods for this competition, I'll be attempting to fix those problems. 

## Pre-Training on Gaussian Labels

My first attempt will be as follows:
1. obtain auxiliary image data from [leafsnap](http://leafsnap.com/dataset/) and [LifeCLEF](http://www.imageclef.org/lifeclef/2016/plant);
2. choose an architecture which performed well on ImageNet (for simplicity, I'll be using a deep all-convolutional network here);
3. pre-train that architecture by providing gaussian-noise labels on each image in the auxiliary training data;
4. use the output of the pre-trained architecture (or its second-to-last-layer, more likely) as features for a linear classifier. 

I got this idea from a paper. I've searched like a madman for that paper, but could not find it. I'll update this if I find it. As for now, off to coding!
