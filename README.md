------------------------------------------Work in Progress------------------------------------------------------

# Master's Thesis: Determination of the Fractal Dimension of Curves Using a Convolutional Neural Network

**University of Turin**

**Supervisor**: prof. Guido Boffetta

**Co-Supervisor**: prof. Matteo Osella


## Abstract

In this project I created a CNN (Convolutional Neural Network) for the determination of the fractal dimension of curves.
The main aspect of this work is the use of the Schramm-Loewner Evolution to create a dataset of curves for the training of the CNN. 
Thanks to the property of this equation I can associate the theoretical fractal dimension with each curve generated. 
Similar works only used the box counting fractal dimension.
This allows me to compare the performance of the CNN with the one of the box counting technique.
The findings show an overall better result for the CNN.
I finally used the CNN and box counting to determine the fractal dimensions of portions of the West Coast of Great Britain.


## Files

Inside **Model** you will find the script CNN.ipynb for training a CNN.
In order to train mine I used the GPU available inside google Colab.
The two CNN I trained are under MainModel and No_Aug Model, with their respective training history.

Inside **CNN Estimate** you will find the script to evaluate the performance of the CNN in the three condition studied: 
- curves with gaps
- curves with noise
- -curves with limited number of points (portion)
