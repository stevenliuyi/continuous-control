## Report

### Algorithm

Deep Deterministic Policy Gradient (DDPG) is a actor-critic reinforcement learning algorithm that simultaneously learns the policy (actor) and the action-value Q function (critic).

For both actor and critic networks, there are a local network and a target network, where the target parameters are updated softly based on a hyperparameter $\tau$:

$$w^-\leftarrow (1-\tau)w^- + \tau w,$$

where $w$ and $w^-$ are the weights for the local and target networks, respectively.

The loss function for the critic network is derived from the Bellman equation:

$$\mathcal{L} = \mathbb{E}\left[\left(R+\gamma Q(S',\mu(S';\theta^-);w^-) - Q(S,A;w)\right)^2\right] $$

where $R$ is reward, $\gamma$ is the discount factor, $S$ and $S'$ are the current and next state, $A$ is the action, and $\mu(S;\theta^-)$ is the action based on the deterministic target policy.

Then, for the actor network, a deterministic policy $\mu(S;\theta)$ is learned to maximize the Q function:

$$\max_{\theta}\mathbb{E}[Q(S,\mu(S;\theta);w)].$$

Similar to DQN, DDPG also utilizes experience replay to stabilize the training process, where experiences $(S,A,R,S')$ are stored in a replay memory and randomly selected for training.

Both the actor and critic networks have the same architecture: fully connected neural networks with two hidden layers, and each hidden layer has 128 neurons.

### Hyperparameters

All hyperparamters used for training are listed below:

- `BUFFER_SIZE`: 100000 (experience replay buffer size)
- `BATCH_SIZE`: 128 (minibatch size)
- `GAMMA`: 0.99 (discount factor)
- `TAU`: 0.001 (soft update rate of the target network)
- `LR_ACTOR`: 0.0002 (learning rate for the actor network)
- `LR_CRITIC`: 0.0002 (learning rate for the critic network)
- `WEIGHT_DECAY`: 0 (L2 weight decay for the critic network)

### Scores


<img src="https://raw.githubusercontent.com/stevenliuyi/continuous-control/main/scores.png" width="400" />

The plot shows the score per episode during the training process. After 100 episodes, the network reaches an average score of +30 over 100 consecutive episodes. At the end of the training, the average score stabilizes at around +37.

### Future ideas
Some other policy gradient or actor-critic reinforcement learning algorithms can be used to solve this continuous control problem, such as:

- Proximal Policy Optimization (PPO)
- Trust Region Policy Optimization (TRPO)
- Asynchronous Advantage Actor-Critic (A3C)
- Distributed Distributional Deterministic Policy Gradients (D4PG)