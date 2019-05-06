# Multiple Agents Reinforcement Learning
# (DDPG algorithm)

## Introduction

This repository contains an implementation of the multiple agent version of the Deep Deterministic Policy Gradient (DDPG) algorithm described in [Multi-Agent Actor-Critic for Mixed Cooperative-Competitive Environments](https://arxiv.org/abs/1706.02275). The implementation has been done in PyTorch, in the Unity environment called [Tennis](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#tennis), where two agents try to pass the ball over the net.

![tennis](https://raw.githubusercontent.com/manuelsh/multi-agent-reinforcement-learning/master/images/tennis_unity.gif)

See more information about the environment in the section **Environment details**.

The agent is implemented and trained in the notebook `multi-agent-reinforcement-learning/muti-agent-tennis-grid-search-minimal.ipynb`.

To see a comprehensive results report, see the `report.md` file in this repository.


## Environment details

The agent will interact with a version of the [Tennis Unity environment](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#tennis).

### Rewards

A reward of +0.1 is provided to each agent for each time it makes the ball pass over the net. If an agent lets the ball hit the ground or get out of bounds, it will have a reward of -0.01.


### State space

The observation space consists of 8 variables corresponding to position and velocity of the raquet and the ball.

### Action space

Each action is a vector with two numbers per agent, corresponding to moving horizontally or vertically.

## Goal of the task

In order to solve the environment, the agents must have an average score of +0.5 over 100 consecutive episodes.

# Requirements installation

To be able to run the notebooks, one needs to prepare the environment and download the Unity environment.

## Preparing the environment

As described in the [Udacity github repo](https://github.com/udacity/deep-reinforcement-learning#dependencies), to set up your python environment, follow the instructions below.

1. Create (and activate) a new environment with Python 3.6.

	- __Linux__ or __Mac__: 
	```bash
	conda create --name drlnd python=3.6
	source activate drlnd
	```
	- __Windows__: 
	```bash
	conda create --name drlnd python=3.6 
	activate drlnd
	```
	
2. Follow the instructions in [this repository](https://github.com/openai/gym) to perform a minimal install of OpenAI gym.  
	- Next, install the **classic control** environment group by following the instructions [here](https://github.com/openai/gym#classic-control).
	- Then, install the **box2d** environment group by following the instructions [here](https://github.com/openai/gym#box2d).
	
3. Clone the repository (if you haven't already!), and navigate to the `python/` folder.  Then, install several dependencies.
```bash
git clone https://github.com/udacity/deep-reinforcement-learning.git
cd deep-reinforcement-learning/python
pip install .
```

4. Create an [IPython kernel](http://ipython.readthedocs.io/en/stable/install/kernel_install.html) for the `drlnd` environment.  
```bash
python -m ipykernel install --user --name drlnd --display-name "drlnd"
```

5. Before running code in a notebook, change the kernel to match the `drlnd` environment by using the drop-down `Kernel` menu. 

## Donwload the Unity Environment

Select and download the environment that matches your operating system:

Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux.zip)
Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis.app.zip)
Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86.zip)
Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86_64.zip)
Then, place the file in the `p3_collab-compet/` folder in the DRLND GitHub repository, and unzip (or decompress) the file.

(For Windows users) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

(For AWS) If you'd like to train the agent on AWS (and have not enabled a virtual screen), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux_NoVis.zip) to obtain the "headless" version of the environment. You will not be able to watch the agent without enabling a virtual screen, but you will be able to train the agent. (To watch the agent, you should follow the instructions to enable a virtual screen, and then download the environment for the Linux operating system above.)

# Instructions to train the agent

Once your environment is set-up, just run the notebook `multi-agent-reinforcement-learning/muti-agent-tennis-grid-search-minimal.ipynb`.

