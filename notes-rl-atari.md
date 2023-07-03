Useful Reminder Gists
- Off-policy, agent interacts using one policy but its goal is to improve another strategy (greedy or optimal). this allows exploration of different actions and states. 
  - Behavior distribution and the greedy/optimal policy are two different strategies 
      - behavior distribution refers to strategy that the agent follows **during exploration.** determines how actions are selected when interacting with an environment. 
      - greedy policy is what we ultimately want our agent to learn. It represents the best possible strategy for maximizing CUMULATIVE rewards in an environemnt. Goal is to converge to
Deep Learning 	RL

LEARN from large amounts of hand-labelled training data 	LEARN from a scalar reward signal that is frequently sparse, noisy, and delayed
Inputs and targets are directly related	Delay from actions and resulting rewards, which can be thousands of time steps long
Data samples are independent 	Sequences of highly correlated states
Assumes fixed at a distribution 	Data distribution changes as the algorithm learns new behavior 

Applied the approach of applying a convolutional neural network to alleviate the problems of non-stationary distributions, 
- They use an experience replay mechanism to randomly sample previous transition and thereby smoothing the training distribution over many past behaviors 

Goal: Single neural network agent that can play as many of the Atari 2600 games as possible. Te agent interacts with the emulator by selecting actions in a way that maximizes future rewards 
Range of Atari 2600 games (testbed, input is HD visual input RGB video) implemented in a special Arcade Learning Environment. Solely learned from the video input. Reward and terminal signals 


Environment is stochastic - follows a random distribution
Emulator - softwawre that allows the agent (neural network) to interact with the Atari games by receiving visual input(raw pixel values representing the current scree) and rewards, and selecting actions from a set of legal game actions. Internal state is modified by the actions taken by the agent.

1. Agent observes images of the current screen. This means that the task is only partially observed and it is hard to understand the current situation from only the current screen. We therefore consider sequences of actions and observations and learn game strategies that depend upon these 
sequences. All sequences are assumed to terminate in a finite number of time-steps. 
2. Agent selects an action from a set of legal game actions. We consider sequences of actions and observations. We then learn game strategies that depend upon these sequences. 
3. Action is passed to the emulator and modifies its internal state and the game score. Our goal is to increase the reward. 

Optimal action-value function 
- represents the expected value of taking a specific action in a given state. 
- this is achieved through iterative updates using the Bellman equation. 
- estimating the action-value function separetly for each sequence is impractical, so function approximators like linear or non-linear models, such as neural nets, are commonly used. these approximators, referred to as Q-networks, are trained y minimizing a sequence of loss functions that change at each iteration. 
-  Bellman equation. 

Q-networks are function approximators (or neural nets lol)
  - Q-learning is used to optimize the loss function of a Q-network  
    - algorithm is model-free, meaning it directly solves the RL task using samples from the emulator
    - off-policy, as it learns about the greedy strategy while folowing a behavior distribution that ensures exploration of the state space. 
  - Other loss functoins are typically like mean squared error (betwen predicted/targeted values) 
  - Big overall idea is that instead of computing the full expectations in the gradient, it is more computationally efficient to optimize the loss function using stochastic gradient descent. By updating the weights after every time-step,
  - nonlinear, can capture more complex dynamics 
    - typically linear functions can also be used!
  - estimate the action-value function in reinforcement learning 
  - input: rgb video of the actual game, raw pixel values. output: estimation of the expected future rewards for each possible action. 
  - sequence 
