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

Our method consists of a convolutional auto encoder which takes in 64*64 RGB picture frames and generates a tensor of 50 float numbers. Then, a simple recurrent neural network is responsible for predicting next frame of the given frame by learning the sequence of the encoded frames representations. This RNN has a hidden layer with size of 200 and input and output size of 50.

# Experimental Results

The following figure shows how well our autoencoder is compressing our frames and reconstructs it afterwards. The first figure is the preprocessed image and the next one is the reconstructed image:

<a href=""><img src="https://github.com/AmirMohaddesi/LLTP/blob/master/Figures/ReconstructedImage1.png?raw=true" width="400" height="400" alt="FVCproductions"></a>

<a href=""><img src="https://github.com/AmirMohaddesi/LLTP/blob/master/Figures/ReconstructedImage2.png?raw=true" width="400" height="400" alt="FVCproductions"></a>

This figure demonstrates a random encoded frame which is 50 random floating numbers.

<a href=""><img src="https://github.com/AmirMohaddesi/LLTP/blob/master/Figures/RandomZDecoded.png?raw=true" width="400" height="400" alt="FVCproductions"></a>

These three figures are respectively, a reconstruction of a random frame, the next figure predicted by out method, and the original next frame which is actually the target. This figure show how well our method is working:

<a href=""><img src="https://github.com/AmirMohaddesi/LLTP/blob/master/Figures/NextFrame1.png?raw=true" width="400" height="400" alt="FVCproductions"></a>

<a href=""><img src="https://github.com/AmirMohaddesi/LLTP/blob/master/Figures/NextFrame2.png?raw=true" width="400" height="400" alt="FVCproductions"></a>

<a href=""><img src="https://github.com/AmirMohaddesi/LLTP/blob/master/Figures/NextFrame3.png?raw=true" width="400" height="400" alt="FVCproductions"></a>

And at last this figure shows several predictions of a single frame. Prediction is done repeatedly. As you can see after several steps the pictures show some kind of uncertainty due to random actions of the Lunar Lander:

<a href=""><img src="https://github.com/AmirMohaddesi/LLTP/blob/master/Figures/1S.png?raw=true" width="400" height="400" alt="FVCproductions"></a>
<a href=""><img src="https://github.com/AmirMohaddesi/LLTP/blob/master/Figures/2S.png?raw=true" width="400" height="400" alt="FVCproductions"></a>
<a href=""><img src="https://github.com/AmirMohaddesi/LLTP/blob/master/Figures/3S.png?raw=true" width="400" height="400" alt="FVCproductions"></a>
<a href=""><img src="https://github.com/AmirMohaddesi/LLTP/blob/master/Figures/4S.png?raw=true" width="400" height="400" alt="FVCproductions"></a>
<a href=""><img src="https://github.com/AmirMohaddesi/LLTP/blob/master/Figures/5S.png?raw=true" width="400" height="400" alt="FVCproductions"></a>
<a href=""><img src="https://github.com/AmirMohaddesi/LLTP/blob/master/Figures/6S.png?raw=true" width="400" height="400" alt="FVCproductions"></a>
<a href=""><img src="https://github.com/AmirMohaddesi/LLTP/blob/master/Figures/7S.png?raw=true" width="400" height="400" alt="FVCproductions"></a>
<a href=""><img src="https://github.com/AmirMohaddesi/LLTP/blob/master/Figures/8S.png?raw=true" width="400" height="400" alt="FVCproductions"></a>
<a href=""><img src="https://github.com/AmirMohaddesi/LLTP/blob/master/Figures/9S.png?raw=true" width="400" height="400" alt="FVCproductions"></a>


# Conclusion

We could show that a simple RNN is able to learn Newton laws of motion and predict the motion of an object as complex as a spaceship by just observing sequences of frames. 
It is possible to come up with a more sophisticated method to do prediction on more complex physics problems.
Also, another possible future work would be exploiting this predictor to obtain far more better action policies in  reinforcement learning methods.
