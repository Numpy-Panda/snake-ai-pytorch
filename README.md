# Teach AI To Play Snake! Reinforcement Learning With PyTorch (will be finished before 17th March)

**I modified and ran the code locally, and the code changes and technical explanation for this repo will be available before 17th March 2023**

This is a repository based on PyTorch that utilizes reinforcement learning to train an AI to play the snake game. The purpose of this repository is to **document my journey of learning reinforcement learning**.

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

This repository utilizes the Deep Q-network (DQN) approach to train an AI to play the snake game. The network is implemented as a simple multi-layer perceptron, which takes the current state of the game as input and outputs the value corresponding to all admissible actions at the current state.





