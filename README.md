# LLTP: Lunar Lander Trajectory Prediction
OpenAI Gym Lunar Lander Trajectory Prediction using RNN and ConvAE

# Introduction

OpenAI Gym is a toolkit for developing and comparing reinforcement learning algorithms. Open AI Gym has an environment-agent arrangement. It simply means Gym gives you access to an “agent” which can perform specific actions in an “environment”. In return, it gets the observation and reward as a consequence of performing a particular action in the environment. 
Following are the available Environments in the Gym:
- Classic control and toy text
- Algorithmic
- Atari
- 2D and 3D robots
- Box2D

Lunar Lander is another interesting problem in Box2D environment in OpenAIGym. 

As you can see in the picture below, there is one space-ship. The task is to land the space-ship between the flags smoothly. The ship has 3 throttles in it. One throttle points downward and other 2 points in the left and right direction. With the help of these, you have to control the Ship.

<a href=""><img src="https://miro.medium.com/max/1346/1*i7lxpgt2K3Q8lgEPJu3_xA.png" title="FVCproductions" alt="FVCproductions"></a>

In this project we present a model to predict the Lunar Lander trajectory. The purpose of this prediction is to figure out next position of the lunar lander which is controlled using random actions from its action space. 

This model uses a convolutional auto encoder to generate a compressed representation of the Lunar Lander picture frames to feed it into a recurrent neural network. The recurrent neural network which has learned possible next positions of the object, will generate the next frame of this LunarLander trajectory.

# Method

Deploying a perfect deep learning approach to solve a problem obviously needs a considerable amount of training data. OpenAI Gym is a perfect tool to generate thousands of trials of real classical Newtonian problems.

We produce 50 episodes of a Lunar Lander and divide them into frames. A preprocessor will crop all of the 400\*600 pixels frames into center cropped and resized 64\*64 pixels pictures.

Our method consists of a convolutional auto encoder which takes in 64*64 RGB picture frames and generates a tensor of 50 float numbers. Then, a simple RNN is responsible for predicting next frame of the given frame by learning the sequence of the encoded frames representations. 

# Experimental Results

The following figure shows how well our autoencoder is compressing our frames and reconstructs it afterwards:

<a href=""><img src="https://github.com/AmirMohaddesi/LLTP/blob/master/Figures/ReconstructedImage1.png?raw=true" width="200" height="200" alt="FVCproductions"></a>

<a href=""><img src="https://github.com/AmirMohaddesi/LLTP/blob/master/Figures/ReconstructedImage2.png?raw=true" width="200" height="200" alt="FVCproductions"></a>

And this figure shows several predictions of my 

# Conclusion

We could show that a simple RNN is able to learn Newton laws of motion and predict the motion of an object as complex as a spaceship by just observing sequences of frames. 
It is possible to come up with a more sophisticated method to do prediction on more complex physics problems.
Also, another possible future work would be exploiting this predictor to obtain far more better action policies in  reinforcement learning methods.
