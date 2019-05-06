# Report with results

## Introduction

We have implemented the multi agent version of the Deep Deterministic Policy Gradient (DDPG) algorithm described in [Multi-Agent Actor-Critic for Mixed Cooperative-Competitive Environments](https://arxiv.org/abs/1706.02275). The implementation has been done in PyTorch, in the Unity environment called [Tennis](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#tennis). For a description of the environment, see the `README.md` file

## Methodology

The methodology applied is the one described in the algorithm 1, of the appendix of the referred paper.

We used the Deep Deterministic Policy Gradients (DDPG), where the actor and critic has been modeled with a fully connected neural network with leaky RELU activations. To ensure that the output of each actor is bounded between -1 and 1 for each action, we employed the `tanh` function.

### Techniques

To help model convergence, we used the following techniques: 

(1) Experience replay, which breaks the sequential order of one experience and keeps track of a replay buffer of (State, Action, Rewards, Next state, Dones). When the model is trained it samples at random from the replay buffer, which will break the correlations happening from repeating always similar actions plus allows to train multiple times from different events, including rare events.

(2) Fixed Q-Targets, where the target used in the loss function is the same Q function that we are training but with a weighted average of previous learned parameters. This ensures that we don't shift the parameters chasing a constantly moving target. The target network was updated "softly", at every training step, with the function `θ_target = τ*θ_local + (1 - τ)*θ_target`.

(3) To ensure the exploration, we added to each action noise via an Ornstein-Uhlenbeck process.

(4) As we noticed that the gradients of the critics and the agents some times exploded, we clipped it to 1.

(5) We also implemented the prioritised experience replay as described in the following [paper](https://arxiv.org/abs/1511.05952). However, we couldn't find a set of parameters for alpha and beta that worked during our random hyperparameter search and finally did not use it.

### Hyper parameters

The replay buffer had a size of 100,000 experiences, and returned a batch of 256 experiences at every training step.

With respect to the training parameters, we used:

`LAYER_INIT_RANGE: 0.003
OU_SIGMA_START: 2
EPIS_SIGMA_END: 300
OU_THETA: 0.2
GAMMA: 0.99
TAU: 0.01
UPDATE_STEPS: 10
NUM_UPDATES: 12
LR_ACTOR: 0.0001
LR_CRITIC: 0.001
GRAD_CLIPPING: 1
HIDDEN UNITS: (768, 512)
PRIOR_EXP: False`

The neural network representing the actor and the critic are composed by 2 layers of 768 and 512 hidden neurons, with leaky RELU activations.

## Results

The model arrives to the result after 720 episodes and the score of the plot is:

![score plot](https://raw.githubusercontent.com/manuelsh/multi-agent-reinforcement-learning/master/images/results.png)

where the orange line represents the average over the previous 100 episodes (or less episodes if not available), and the blue line represents the score at that episode.

Note that the parameters of trained actors and critics can be found in the repo.

# Next steps

There are a few next steps that can be researched:

1. Use a shared representation for the critic and the actor, with different output.
2. Solve the soccer environment.

In a personal note, I have enjoyed this project very much, and also the fact that there is so much to learn and try.