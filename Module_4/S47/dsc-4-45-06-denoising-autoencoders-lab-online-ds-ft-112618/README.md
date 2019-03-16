
# Denoising Autoencoders - Lab

## Introduction

In this lab, we will build a simple de-noising autoencoder using a shallow architecture. Following the approach in previously seen in the section, the simple architecture can be replaced by a deep network having multiple layers to learn the intermediate representation. The basic architecture remains the same here , however, the application area changes from data compression to data de-noising. Let's get on with it . 

## Objectives

You will be able to:

- Build a simple denoising Autoencoder architecture in Keras
- Add random Gaussian Noise to a given images dataset
- Predict a clean image from a (previously unseen) noisy image


## Load necessary libraries

We need to first load necessary libraries including numpy and keras for building our DAE model.


```python
# Import necessary libraries

# Your code here 
```

## Load data

This experiment can be performed with any small image database, to help us keep our focus on the architecture and the approach. You can try with MNIST, fashion-MNIST, CIFAR10 and CIFAR100 datasets. CIFAR datasets are colored images and carry RGB channels which can possibly increase the training times many folds. You are encouraged to try these and other larger datasets with this code and give it a few hours (maybe overnight) training time to run a bigger experiment. 

Let's perform following tasks first, similar to our previous labs

- Load MNIST/fashion-MNIST dataset in keras (both datasets contain images with similar dimensions). Create train and test datasets
- Neural networks only accepts row vectors as an input - Reshape train and test datasets from 2D array to 1D. 
- Scale the data in range [0,1] to allow us to use sigmoid activation function in output neurons.
- Print the shape of resulting datasets


```python
# Code here 
```

    MNIST
    
    60000 training samples
    10000 test samples


## Create a "Noisy" Dataset

Here we will introduce random Gaussian noise to the test and train data. The noiy dataset can be generated using following general formula, which will a add noise with mean 0 and standard deviation=1 :

$$NoisyDataset~=~OriginalDataset~+~NoiseFactor~*~np.random.normal(loc=0.0, scale=1.0, size=OriginalDataset.shape)$$

- Use a noise factor of 0.5
- Create a set of noise test and train datasets from original datasets using formula given above
- Use `np.clip()` to restrict the values between 0 and 1. 


> __numpy.clip(a, a_min, a_max, out=None)__ clips (limit) the values in an array.

*Given an interval, values outside the interval are clipped to the interval edges. For example, if an interval of [0, 1] is specified, values smaller than 0 become 0, and values larger than 1 become 1.*



```python
# Code here 
```

## Build the DAE

- Build the encoder model for creating a hidden representation of length 32 from input vector of length 784. 
- Use RELU activation for the encoder model
- Build the decoder model with signmoid activation 
- Show model summary


```python
# Code here 
```

    _________________________________________________________________
    Layer (type)                 Output Shape              Param #   
    =================================================================
    inputs (InputLayer)          (None, 784)               0         
    _________________________________________________________________
    dense_1 (Dense)              (None, 32)                25120     
    _________________________________________________________________
    dense_2 (Dense)              (None, 784)               25872     
    =================================================================
    Total params: 50,992
    Trainable params: 50,992
    Non-trainable params: 0
    _________________________________________________________________


## Compile and Predict 

- Use batch size = 128 and 30 epochs for training (increase epochs for better results)
- Use adam optimizer and binary cross entropy as the loss measure to compile DAE model
- Fit DAE with noisy dataset as the input and original dataset as the output. We are trying to teach the network to learn how a clean version compares to the noisy version of data - for all images. 
- Set `shuffle=True` for shuffling batches of data. 
- Make predictions with the noise test dataset


```python
# Code here 
```

    Train on 60000 samples, validate on 10000 samples
    Epoch 1/30
    60000/60000 [==============================] - 3s 49us/step - loss: 0.3941 - val_loss: 0.3420
    Epoch 2/30
    60000/60000 [==============================] - 2s 37us/step - loss: 0.3322 - val_loss: 0.3284
    Epoch 3/30
    60000/60000 [==============================] - 2s 40us/step - loss: 0.3226 - val_loss: 0.3214
    Epoch 4/30
    60000/60000 [==============================] - 3s 46us/step - loss: 0.3169 - val_loss: 0.3171
    Epoch 5/30
    60000/60000 [==============================] - 3s 43us/step - loss: 0.3133 - val_loss: 0.3144
    Epoch 6/30
    60000/60000 [==============================] - 2s 42us/step - loss: 0.3108 - val_loss: 0.3124
    Epoch 7/30
    60000/60000 [==============================] - 3s 42us/step - loss: 0.3089 - val_loss: 0.3106
    Epoch 8/30
    60000/60000 [==============================] - 2s 40us/step - loss: 0.3075 - val_loss: 0.3095
    Epoch 9/30
    60000/60000 [==============================] - 2s 40us/step - loss: 0.3064 - val_loss: 0.3082
    Epoch 10/30
    60000/60000 [==============================] - 2s 40us/step - loss: 0.3054 - val_loss: 0.3077
    Epoch 11/30
    60000/60000 [==============================] - 2s 41us/step - loss: 0.3047 - val_loss: 0.3069
    Epoch 12/30
    60000/60000 [==============================] - 2s 41us/step - loss: 0.3042 - val_loss: 0.3066
    Epoch 13/30
    60000/60000 [==============================] - 2s 40us/step - loss: 0.3039 - val_loss: 0.3063
    Epoch 14/30
    60000/60000 [==============================] - 3s 42us/step - loss: 0.3036 - val_loss: 0.3062
    Epoch 15/30
    60000/60000 [==============================] - 2s 40us/step - loss: 0.3034 - val_loss: 0.3061
    Epoch 16/30
    60000/60000 [==============================] - 3s 43us/step - loss: 0.3033 - val_loss: 0.3060
    Epoch 17/30
    60000/60000 [==============================] - 3s 43us/step - loss: 0.3032 - val_loss: 0.3059
    Epoch 18/30
    60000/60000 [==============================] - 3s 43us/step - loss: 0.3031 - val_loss: 0.3058
    Epoch 19/30
    60000/60000 [==============================] - 2s 41us/step - loss: 0.3030 - val_loss: 0.3057
    Epoch 20/30
    60000/60000 [==============================] - 2s 39us/step - loss: 0.3029 - val_loss: 0.3056
    Epoch 21/30
    60000/60000 [==============================] - 2s 39us/step - loss: 0.3028 - val_loss: 0.3055
    Epoch 22/30
    60000/60000 [==============================] - 3s 44us/step - loss: 0.3028 - val_loss: 0.3056
    Epoch 23/30
    60000/60000 [==============================] - 3s 42us/step - loss: 0.3027 - val_loss: 0.3055
    Epoch 24/30
    60000/60000 [==============================] - 3s 42us/step - loss: 0.3026 - val_loss: 0.3056
    Epoch 25/30
    60000/60000 [==============================] - 3s 42us/step - loss: 0.3026 - val_loss: 0.3055
    Epoch 26/30
    60000/60000 [==============================] - 3s 42us/step - loss: 0.3025 - val_loss: 0.3053
    Epoch 27/30
    60000/60000 [==============================] - 3s 42us/step - loss: 0.3025 - val_loss: 0.3052
    Epoch 28/30
    60000/60000 [==============================] - 3s 43us/step - loss: 0.3025 - val_loss: 0.3052
    Epoch 29/30
    60000/60000 [==============================] - 3s 44us/step - loss: 0.3024 - val_loss: 0.3053
    Epoch 30/30
    60000/60000 [==============================] - 3s 47us/step - loss: 0.3023 - val_loss: 0.3052


## View the results 

- Show the first ten images from the clean dataset.  
- Show the images with added noise and images predicted by the DAE. 


```python
# display original - Clean dataset

```


![png](index_files/index_12_0.png)



```python
# Display noisy and  predicted clean images
```


![png](index_files/index_13_0.png)


Here we can see that the our model is actually performing very well. We do see some poor predictions above due to highly reduced dimensionality and high noise we have introduced in our dataset. We can further inspect the performance by checking the training and validation loss above. As always , a key takeaway here is the number of training examples and training time have a huge impact on the performance of a deep architecture. 

## Level up - Optional

- Increase the size of encoded representation / decrease the amount of noise to see if the performance improves. 
- See how training epochs effect the performance
- Import the faces dataset that we saw with PCA dimensionality reduction lab from scikit-learn, and repeat the above experiment. 
- Look for other interesting datasets/create your own noise datasets and train the network.
- Create a DEEP denoising autoencoder by modifying the code above. 

## Summary 

In this lab we looked at building a simple denoising autoencoder. We created noisy datasets by adding random Gaussian noise to the fashion MNIST dataset in keras. Our results show that the network is able to identify the shapes very well , but due to using a hugely oversimplified architecture , the accuracy remains questionable. Next we'll see how we can use convolutional network approach to simplify the task of image reconstruction.
