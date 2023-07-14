# Video-Action-Recognition
Video Action Recognition- Limp or Not?

## Project Description
The purpose of this project is to compare a larger dataset of videos using video augmentation to a smaller, 
original set of videos.

### Augmentation Methods Used:

* Horizontal Flip using an augmentation package from: https://github.com/okankop/vidaug
* Object map and green background changes from: https://github.com/plemeri/transparent-background
* Optical Flow using the Farneback implementation with OpenCV

### Video files were obtained from:

YouTube scraping using Free YouTube Download by dvdvideosoft.com


## Project Summary

The original dataset containing roughly 30 videos per class looks deceptively better than the larger dataset with 
the original having a higher accuracy score for both test and validation. However, given the small sample size 
(i.e., the test split of 0.2 only affords 6 videos for testing and a further 0.2 split for validation only 5!) 
the results cannot be relied upon.

The augmented dataset, consisting of roughly 180 videos per class for training with the same split breakdowns, did not
perform well. Since there are many differences between the datasets, it would be difficult to say exactly why that 
would be. Some of these factors include:

1. The model as a whole really isn't good at predicting if a limp is present. The videos themselves, edited for length,
   were taken at different angles, on many different breeds (and even some horses thrown in for contrast), and in a 
   variety of settings leading to an overall lack of conformity. Limps in general are difficult for a human eye to 
   perceive, so it is not surprising that such a complex and ambitious task would not be easy to model.

2. Due to data leakage concerns, the videos were divided into train, test, and validation sets by hand. Several
   smaller sections of videos were made from longer videos as well as the augmented methods listed above,
   requiring the set to be divided manually to keep the same videos together. Although shuffling was added to 
   the training set to ensure better training, were there other issues introduced, such as reduced randomness 
   in the splits?

3. The data augmentation methods themselves may have hindered the learning process. The methods were chosen to, 
   in theory, help isolate the activity. Removing the background with just the animal in motion present (object map)
   or having a green screen replacement should have removed any distracting pixels from the target in question. 
   The optic flow process should have isolated just the motion to be evaluated, removing any differences in 
   background or even in size of the animal being evaluated. Did the video backgrounds add to the activity 
   recognition? Did the videos using optic flow remove target or reference points of interest?

There are several variables at work in this simple comparison, and a step-wise method isolating each variable would
have to be created to evaluate some of these effects, but it is interesting to see how this model performed given
such a subtle and complex problem.
