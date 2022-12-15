## Continuous control

This project solves the Unity ML-Agents Reacher environment using the Deep Deterministic Policy Gradient (DDPG). The code is written in PyTorch.

### Environment

In the Reacher environment, a double-jointed arm can move to target locations. At each time step, a reward of +0.1 was earned when the agent's hand is in the target location. The state space has 33 dimensions, while the action space has 4 continuous actions (from -1 to 1), corresponding to torque applicable to two joints. Twenty identical agents are present in the environment.

The problem is considered solved with an average score of +30 (over all 20 agents) over 100 consecutive episodes.

### Introduction

The dependencies are provided inside the folder `python`. This is adapted from the [ML-Agents repository](https://github.com/Unity-Technologies/ml-agents) but also includes additional pip packages needed. The Linux headless version of the Unity Environment used in this project is in the folder `Reacher_Linux_NoVis`. For other operating system, the environment files can be downloaded from:

- Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux.zip)
- Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher.app.zip)
- Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86.zip)
- Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86_64.zip)

The Jupyter notebook [`Continuous_Control.ipynb`](Continuous_Control.ipynb) contains all the codes to install dependencies, train agent using DDPG, save model weights, and generate report plot. Saved weights from one successful training can be found in [`actor_checkpoint.pth`](actor_checkpoint.pth) (actor/policy network) and [`critic_checkpoint.pth`](critic_checkpoint.pth) (critic/value network).

Details of the implementation and results can be found in the [report](Report.md).