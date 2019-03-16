
# Convolutional Autoencoders - Lab

## Introduction

Earlier we saw the application of simple and deep fully connected auto encoders to image analysis. We ran a few very simple and limited experiments, producing output that was blurry, maintaining object shapes but lacking distinguishing features etc. Convolutional Networks can help overcome these issues as we will see in this lab. We will build a CAE for the same dataset we used earlier in order to produce improved results. 

*Notes: Refer back to section on Convolutional Networks for details of different layers and their specific functions*

## Objectives

You will be able to:
- Build a convolutional autoencoder in Keras
- Compare the output of convolutional vs. simple and deep autoencoders in terms of predictive performance


## Building a CAE

For image inputs, convolutional neural networks (convnets) as encoders and decoders are considered among the best analysis approaches. You would mostly find that autoencoders applied to images are always convolutional autoencoders as perform much better.

We will build a CAE in a stack of Conv2D and MaxPooling2D layers 
- Encoder will use max pooling for spatial down-sampling)
- The decoder will consist in a stack of Conv2D and UpSampling2D layers

### Implement following Conv-autoencoder network in Keras 

    ```
    Layer (type)                 Output Shape              Param #   
    =================================================================
    input_3 (InputLayer)         (None, 28, 28, 1)         0         
    _________________________________________________________________
    conv2d_15 (Conv2D)           (None, 28, 28, 16)        160       
    _________________________________________________________________
    max_pooling2d_7 (MaxPooling2 (None, 14, 14, 16)        0         
    _________________________________________________________________
    conv2d_16 (Conv2D)           (None, 14, 14, 8)         1160      
    _________________________________________________________________
    max_pooling2d_8 (MaxPooling2 (None, 7, 7, 8)           0         
    _________________________________________________________________
    conv2d_17 (Conv2D)           (None, 7, 7, 8)           584       
    _________________________________________________________________
    max_pooling2d_9 (MaxPooling2 (None, 4, 4, 8)           0         
    _________________________________________________________________
    conv2d_18 (Conv2D)           (None, 4, 4, 8)           584       
    _________________________________________________________________
    up_sampling2d_7 (UpSampling2 (None, 8, 8, 8)           0         
    _________________________________________________________________
    conv2d_19 (Conv2D)           (None, 8, 8, 8)           584       
    _________________________________________________________________
    up_sampling2d_8 (UpSampling2 (None, 16, 16, 8)         0         
    _________________________________________________________________
    conv2d_20 (Conv2D)           (None, 14, 14, 16)        1168      
    _________________________________________________________________
    up_sampling2d_9 (UpSampling2 (None, 28, 28, 16)        0         
    _________________________________________________________________
    conv2d_21 (Conv2D)           (None, 28, 28, 1)         145       
    =================================================================
    Total params: 4,385
    Trainable params: 4,385
    Non-trainable params: 0
    ```


```python
# Code here 
```

    _________________________________________________________________
    Layer (type)                 Output Shape              Param #   
    =================================================================
    input_3 (InputLayer)         (None, 28, 28, 1)         0         
    _________________________________________________________________
    conv2d_15 (Conv2D)           (None, 28, 28, 16)        160       
    _________________________________________________________________
    max_pooling2d_7 (MaxPooling2 (None, 14, 14, 16)        0         
    _________________________________________________________________
    conv2d_16 (Conv2D)           (None, 14, 14, 8)         1160      
    _________________________________________________________________
    max_pooling2d_8 (MaxPooling2 (None, 7, 7, 8)           0         
    _________________________________________________________________
    conv2d_17 (Conv2D)           (None, 7, 7, 8)           584       
    _________________________________________________________________
    max_pooling2d_9 (MaxPooling2 (None, 4, 4, 8)           0         
    _________________________________________________________________
    conv2d_18 (Conv2D)           (None, 4, 4, 8)           584       
    _________________________________________________________________
    up_sampling2d_7 (UpSampling2 (None, 8, 8, 8)           0         
    _________________________________________________________________
    conv2d_19 (Conv2D)           (None, 8, 8, 8)           584       
    _________________________________________________________________
    up_sampling2d_8 (UpSampling2 (None, 16, 16, 8)         0         
    _________________________________________________________________
    conv2d_20 (Conv2D)           (None, 14, 14, 16)        1168      
    _________________________________________________________________
    up_sampling2d_9 (UpSampling2 (None, 28, 28, 16)        0         
    _________________________________________________________________
    conv2d_21 (Conv2D)           (None, 28, 28, 1)         145       
    =================================================================
    Total params: 4,385
    Trainable params: 4,385
    Non-trainable params: 0
    _________________________________________________________________


## Load the dataset

As in previous examples, we will stick with fashion-MNIST or MNIST datasets for convenience. Building a deep neural network with high definition-colored images would require a much higher computational cost with convolutional networks. We will use fashion MNIST digits with shape (samples, 3, 28, 28), and we will just normalize pixel values between 0 and 1. We will reshape the images as channel encoding i.e. (28 x 28 x 1) instead of using a vector in previous lessons. We are now presented an image as discrete 2D object. 

#### Load fashion-MNIST dataset as train and test sets. Scale the features and Reshape features using "Channel encoding".  


```python
# code here
```

## Train the CAE

We will now train our network just like we did with simple auto encoder. 

#### Use batch size = 128, epochs = 20, shuffle = True and using x_test for validation

*Note: this is a computationally expensive task due to the deep nature of our network. On a 2017 Macbook pro, the training will take about 20 min i.e. roughly 1 epoch/minute. For good results, you are required to train this , and previous networks to around 40 - 60 epochs.*


```python
# Code here
```

    Train on 60000 samples, validate on 10000 samples
    Epoch 1/20
    60000/60000 [==============================] - 52s 872us/step - loss: 0.3205 - val_loss: 0.3229
    Epoch 2/20
    60000/60000 [==============================] - 52s 872us/step - loss: 0.3093 - val_loss: 0.3100
    Epoch 3/20
    60000/60000 [==============================] - 51s 856us/step - loss: 0.3050 - val_loss: 0.3060
    Epoch 4/20
    60000/60000 [==============================] - 52s 874us/step - loss: 0.3024 - val_loss: 0.3044
    Epoch 5/20
    60000/60000 [==============================] - 53s 883us/step - loss: 0.3006 - val_loss: 0.3001
    Epoch 6/20
    60000/60000 [==============================] - 55s 920us/step - loss: 0.2989 - val_loss: 0.2985
    Epoch 7/20
    60000/60000 [==============================] - 53s 883us/step - loss: 0.2977 - val_loss: 0.3044
    Epoch 8/20
    60000/60000 [==============================] - 54s 903us/step - loss: 0.2966 - val_loss: 0.2969
    Epoch 9/20
    60000/60000 [==============================] - 58s 973us/step - loss: 0.2953 - val_loss: 0.2950
    Epoch 10/20
    60000/60000 [==============================] - 56s 931us/step - loss: 0.2949 - val_loss: 0.2958
    Epoch 11/20
    60000/60000 [==============================] - 54s 903us/step - loss: 0.2939 - val_loss: 0.2949
    Epoch 12/20
    60000/60000 [==============================] - 52s 870us/step - loss: 0.2929 - val_loss: 0.2956
    Epoch 13/20
    60000/60000 [==============================] - 55s 922us/step - loss: 0.2926 - val_loss: 0.2963
    Epoch 14/20
    60000/60000 [==============================] - 56s 934us/step - loss: 0.2922 - val_loss: 0.2927
    Epoch 15/20
    60000/60000 [==============================] - 52s 860us/step - loss: 0.2915 - val_loss: 0.2904
    Epoch 16/20
    60000/60000 [==============================] - 51s 844us/step - loss: 0.2911 - val_loss: 0.2950
    Epoch 17/20
    60000/60000 [==============================] - 51s 851us/step - loss: 0.2906 - val_loss: 0.2918
    Epoch 18/20
    60000/60000 [==============================] - 55s 909us/step - loss: 0.2903 - val_loss: 0.2932
    Epoch 19/20
    60000/60000 [==============================] - 52s 859us/step - loss: 0.2901 - val_loss: 0.2882
    Epoch 20/20
    60000/60000 [==============================] - 52s 873us/step - loss: 0.2893 - val_loss: 0.2894





    <keras.callbacks.History at 0x1a2dd80860>



## Plot the original Images and their reconstructions

Select and view first 10 images from the x_test and reconstructed images to check the quality of reconstruction. 


```python
# Code here
```


![png](index_files/index_8_0.png)


We see very poor results with 20 epochs of training here. Clearly the images and reconstruction are not comparable at this stage. Increase the epochs to around 50 to see improved results. 


## Level up - Optional

### Application to image denoising

We can use our convolutional autoencoder to work on an image denoising problem, similar to one seen earlier. Train the convolutional autoencoder to map noisy digits images to clean digits images. compare the quality of cleaned images (decoded) to those by simple /deep fully connected autoencoders.

## Additional Resources

- [Basics of Image Processing](https://www.codementor.io/isaib.cicourel/image-manipulation-in-python-du1089j1u)
- [Implementing PCA, Feedforward and Convolutional Autoencoders and using it for Image Reconstruction, Retrieval & Compression](https://blog.manash.me/implementing-pca-feedforward-and-convolutional-autoencoders-and-using-it-for-image-reconstruction-8ee44198ea55)

## Summary 

In this lesson , we looked at a deep convolutional autoencoder to achieve data compression and noise reduction , compared to how these tasks were performed in simple autoencoders. We saw image processing incurred a huge processing cost to our experiment, but with enough epochs and training examples, the output produced by CAEs looks much better than those by simple AEs. 
