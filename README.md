# Brain-Tumor-Auto-segmentation



This project is one of my assignments related to https://www.coursera.org/ in AI for Medicine Specialization.
This specialization includes three different courses entitled AI for Medical Diagnosis, AI for Medical Prognosis and AI For Medical Treatment
Brain tumor auto segmentation is an assignemtn for the first course; i.e AI for Medical Diagnosis


## Table of Contents

1. [Learn](#learn)
2. [Dataset](#dataset)
3. [Preprocessing](#preprocessing)
4. [Loss Function](#loss-function)
5. [Contact](#contact)


## Learn

I learnt: 
* What is in an MR image
* Standard data preparation techniques for MRI datasets
* Metrics and loss functions for segmentation
* Visualizing and evaluating segmentation models



## Dataset

MR images often are in the [DICOM format](https://en.wikipedia.org/wiki/DICOM)

We used the data from the [Decathlon 10 challenge](https://decathlon-10.grand-challenge.org/). 
Our dataset is in the [NifTI-1 format](https://nifti.nimh.nih.gov/nifti-1/) and we should use the [NiBabel library](https://github.com/nipy/nibabel) to interact with the files.


One of our image files contains a 4D array of MR image in the shape of (240, 240, 155, 4)
The first 3 dimensions are the X, Y, and Z values for each point in the 3D volume, which is commonly called a voxel.
The 4th dimension is the values for 4 different sequences
* 0: FLAIR: "Fluid Attenuated Inversion Recovery" (FLAIR)
* 1: T1w: "T1-weighted"
* 2: t1gd: "T1-weighted with gadolinium contrast enhancement" (T1-Gd)
* 3: T2w: "T2-weighted"


The second file in each training example is a label file containing a 3D array with the shape of (240, 240, 155).
The integer values in this array indicate the "label" for each voxel in the corresponding image files:
* 0: background
* 1: edema
* 2: non-enhancing tumor
* 3: enhancing tumor





## Preprocessing

* We should generate "patches" of our data which you can think of as sub-volumes of the whole MR images.
* we should standardize the values to have a mean of zero and standard deviation of 1.



## Loss Function

Aside from the architecture, one of the most important elements of any deep learning method is the choice of our loss function.

A natural choice that you may be familiar with is the cross-entropy loss function.

However, this loss function is not ideal for segmentation tasks due to heavy class imbalance (there are typically not many positive regions).
A much more common loss for segmentation tasks is the Dice similarity coefficient, which is a measure of how well two contours overlap.

* The Dice index ranges from 0 (complete mismatch)
* To 1 (perfect match).

While the Dice Coefficient makes intuitive sense, it is not the best for training.

* This is because it takes in discrete values (zeros and ones).
* The model outputs probabilities that each pixel is, say, a tumor or not, and we want to be able to backpropagate through those outputs.
Therefore, we need an analogue of the Dice loss which takes real valued input. This is where the Soft Dice loss comes in.



## Contact

If you have any anything to tell, I will be glad to hear from you: my Email is Zahra1997khazaei@gmail.com
Also, I will be happy to visit my [website](https://el-ham.com/)