# Deep Atari
1-step Q Learning from  the paper "Asynchronous Methods for Deep Reinforcement Learning" 
Atari games are one of the coolest games out there and have gained widespread mainstream popularity. Breakout is one of my personal favorites. Pong, which was the first game ever developed by Atari Inc. was also one of the most influential video games ever created. In 2013, Deep Mind released its paper “[Playing Atari with Deep Reinforcement Learning](http://arxiv.org/abs/1312.5602)”. It's a very popular paper in literature. My project implements <span class="col-11 text-gray-dark mr-2">1-step Q Learning</span> from this paper.

## Environment:

Here, I've used OpenAI gym's [Atari environment](https://github.com/openai/gym#atari), which is a toolkit for developing and comparing RL algorithms.  Changing the environments is as simple as changing the value of a string variable.

## Q learning:

In Q-learning we define a function _Q(s, a)_ representing the maximum discounted future reward when we perform action <u>a</u> in state <u>s</u>, and continue optimally from that point on. ![Screen Shot 2015-12-21 at 11.09.47 AM](https://www.nervanasys.com/wp-content/uploads/2015/12/Screen-Shot-2015-12-21-at-11.09.47-AM.png) We can think of Q(s, a) as the best possible score at the end of the game after performing action <u>a</u> in state <u>s</u>**.** It is called Q-function, because it represents the “quality” of a certain action in a given state.

## Deep Q network:

We use a CNN which takes in the State S, and predicts the Q values for all the possible actions from that state S.  ![Screenshot from 2017-03-12 16:12:20](https://bhaktipriya96.files.wordpress.com/2017/03/screenshot-from-2017-03-12-161220.png)   The network architecture that DeepMind used is as follows: ![Screen Shot 2015-12-21 at 11.23.28 AM](https://www.nervanasys.com/wp-content/uploads/2015/12/Screen-Shot-2015-12-21-at-11.23.28-AM.png) This is a classical convolutional neural network with three convolutional layers, followed by two fully connected layers. There are no pooling layers since pooling layers buy us translation invariance, which is not something that we desire when we train our bots for games. Input to the network are four 84×84 grayscale game screens.  We use 4 recent screens as the environment state. Outputs of the network are Q-values for each possible action. This is a regression task, since Q-values can be any real values . The loss function of this network is a simple squared error loss. ![](https://www.nervanasys.com/wp-content/uploads/2015/12/formula.png)  

## Training the network:

  ![Screenshot from 2017-03-12 17:28:24.png](https://bhaktipriya96.files.wordpress.com/2017/03/screenshot-from-2017-03-12-172824.png)  

## Experience Replay:

During gameplay all the experiences <_ s, a, r, s’_ > are stored in a replay memory. We use these minibatches to train the network, which makes the training task similar to usual supervised learning.

## ![Screenshot from 2017-03-13 12:06:54](https://bhaktipriya96.files.wordpress.com/2017/03/screenshot-from-2017-03-13-120654.png)Exploitation vs Exploration:

![Screenshot from 2017-03-13 12:08:36](https://bhaktipriya96.files.wordpress.com/2017/03/screenshot-from-2017-03-13-120836.png)

## Results:

https://www.youtube.com/watch?v=0KRVL-VkMGw 
https://www.youtube.com/watch?v=0-ATaiFjzi8 
https://www.youtube.com/watch?v=48HNdmfGEjE
