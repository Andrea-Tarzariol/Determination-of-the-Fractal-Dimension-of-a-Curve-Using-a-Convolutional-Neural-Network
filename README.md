------------------------------------------Work in Progress------------------------------------------------------

# Master's Thesis: Determination of the Fractal Dimension of Curves Using a Convolutional Neural Network

**University of Turin**

**Supervisor**: Prof. Guido Boffetta

**Co-Supervisor**: Prof. Matteo Osella

**External Examiner**: Dr. Filippo Valle


## Abstract

In this project I created a CNN (Convolutional Neural Network) for the determination of the fractal dimension of curves.
The main aspect of this work is the use of the Schramm-Loewner Evolution to create a dataset of curves for the training of the CNN. 
Thanks to the property of this equation I can associate the theoretical fractal dimension with each curve generated. 
Similar works only used the box counting fractal dimension.
This allows me to compare the performance of the CNN with the one of the box counting technique.
The findings show an overall better result for the CNN.
I finally used the CNN and box counting to determine the fractal dimensions of portions of the West Coast of Great Britain.


## Folders

Inside **Model** you will find the script CNN.ipynb for training a CNN.
In order to train mine I used the GPU available inside google Colab.
The two CNN I trained are under MainModel and No_Aug Model, with their respective training history.

Inside **CNN Estimate** you will find the script to evaluate the performance of the CNN in the three conditions studied: 
- curves with gaps
- curves with noise
- curves with limited number of points (portion)

The equivalent scripts for the box counting can be found inside the folder **Box Counting Estimates**.

The script for the creation of the curves can be found inside the folder **Dataset Creation**.

**Numerical Results** section contains the results, saved as .CSV files for both the CNN and the Box Counting in the three conditions studied.

**Results** holds the script used for comparing the performances.

Finally, inside **Coast Analysis** can be found the script used for the estimation of the fractal dimension of the West Coast of Great Britain.
Note that you need to downaload the .shp file of the UK from GADM (https://gadm.org/).

## Overview

I used the algorithm described in the article "A Fast Algorithm for Simulating the Chordal Schramm–Loewner Evolution", by Tom Kennedy, to create fractal curves. 
The Schramm-Loewner Evolution equation is:

$$
\frac{\partial g_t(z)}{\partial t}
= \frac{2}{g_t(z) - \sqrt{\kappa}\ B_t},
\qquad g_0(z) = z
$$

The parameter **K** is linked with the fractal dimension **D**, of the curve generated, by the equation:

$$
D = 1 + \frac{k}{8}
$$

I used this property to create a dataset of curves with labels given by the theoretical fractal dimension.
The curves are made of 20.000 points, and I store them as NumPy arrays.
The dataset is then used to train a CNN, with the aim of creating a model capable of outperforming the Box Counting technique.

The Box Counting suffers of some limitations:
- it can not work with discontinuos curves
- the image must contain only the curve and not element like noise
- with limited portion of curves it can underestimate the fractal dimension

These limitations are the reasons why I introduce three forms of data augmentations:
- curves with gaps
- images of curves with noise
- images of portion of curves

