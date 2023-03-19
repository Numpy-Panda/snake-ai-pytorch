# Teach AI To Play Snake! Reinforcement Learning With PyTorch (to be finished)



This is a repository based on PyTorch that utilizes reinforcement learning to train an AI to play the snake game. The purpose of this repository is to.

# Introduction

The game "Snake" involves controlling a growing line or snake as it moves around a game board, consuming food and avoiding obstacles. The goal is to achieve the highest score possible before the snake crashes into a wall or its own body.

Reinforcement learning (RL) is a type of machine learning that involves an **agent** interacting with an **environment** and learning to make decisions based on rewards or punishments received for its actions. Through trial-and-error, the agent develops a policy that maximizes its expected long-term **reward**s. Reinforcement learning has been applied to a wide range of domains, from playing games and controlling robots to managing financial portfolios and optimizing energy systems. 

## Explanation of used terms
In reinforcement learning:

**Environment**: is the agent’s world in which it lives and interacts.

**Agent**: is the learner or decision maker that takes actions and interacts with the environment.

**State**: is the representation of the situation or condition of the agent and the environment at a given time.

**Reward**: is a numerical feedback from the environment that tells the agent how good its action was.

**Value Function**: is a function that estimates how good a state or an action is for the agent in terms of expected future reward.

**Q-learning**: is a classical RL algorithm of learning value function.

**Deep Q-learning**: is an algorithm that uses a deep neural network to approximate the value function of taking an action in a state.

# Methods

## Q-network (DQN)

This repository utilizes the Deep Q-network (DQN) approach to train an AI to play the snake game. The network is implemented as a simple multi-layer perceptron, which takes the current state of the game as input and outputs the value corresponding to all admissible actions at the current state.

The multi-layer perceptron, also known as the DQN network, takes as input the game state, which comprises the positional information of the food and the critical information for the snake's survival (to avoid collisions with the snake's own body or the game boundary). After passing through this simple multi-layer perceptron, the input state is mapped into a three-dimensional vector. The values of this vector represent the quality of three possible actions, namely moving forward, leftward, or rightward, given the current game state input to the network. 

There are four inputs related to the food, namely whether the food is located above, below, to the left or to the right of the snake's head. If the condition holds true, the information is input into the network with a value of 1. Otherwise, the information is input as 0. The inputs relevant to whether the snake can survive is whether there is a snake's body or a boundary within a block range in front, left, and right directions of the snake's head, and whether there is a snake's body within a three-block range in seven directions behind and around the snake's head. If these conditions are met, the information is inputted into the network as a numerical value of 1. If not, the information is inputted as 0.

## Reward Function

In order to facilitate and instruct the agent to play the game effectively, we have devised a straightforward Reward Function that measures the agent's performance following each action taken. Specifically, if the snake successfully moves to get the food after the agent's action, a positive reward of +10 is assigned. Conversely, if the snake collides with the boundary or its own body as a result of the agent's action, a negative reward of -10 is assigned. Finally, if the snake neither obtains food nor dies as a result of the agent's action, a neutral reward of 0 is assigned by the Reward Function.

However, this simplistic Reward Function may result in the phenomenon of "Reward Hacking." This arises when the agent, engaged in playing the game of snake, is rewarded with a negative value of -10 for directing the snake to a distant location away from its initial position, which leads to a collision with the wall. At this stage, the agent is unaware that eating food will result in a positive value of +10 as a reward. Consequently, to avoid receiving a negative reward of -10, the agent may resort to employing the strategy of making the snake move in circles indefinitely, ensuring that each action yields a reward of 0. Therefore, we have incorporated a condition in our reward function to prevent the agent from making the snake move in circles indefinitely. This involves rewarding the agent with a penalty of -10 if the snake is not directed to consume food within a certain period of time.


## Experience Replay Mechanism and Target Network

In contrast to supervised learning with deep learning, which assumes that each training sample is independent, RL assumes that the training samples are highly correlated. This can lead to slow convergence of the RL model, necessitating the use of an experience replay mechanism to store the agent's experience, represented as et = (st, at, rt, st+1 ). During the training process, a small batch of experience samples is randomly extracted from the memory buffer D each time, and the network parameters are updated using the stochastic gradient descent algorithm. The experience replay mechanism breaks the correlations between the samples by randomly sampling historical data, while the reuse of experiences increases the efficiency of data usage.

To enhance the stability of the DQN algorithm, in addition to the Q-network that updates the neural network parameters, a target Q-network is employed to estimate the Q-value for the next state, which represents the expected cumulative long-term reward from that state.




