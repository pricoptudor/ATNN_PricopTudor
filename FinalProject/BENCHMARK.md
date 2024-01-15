## Benchmark Performance - [Github Repository](https://github.com/pricoptudor/ATNN_PricopTudor/tree/main/FinalProject)

### The algorithms used for experiments and comparison:

- <b>PPO</b> (Proximal Policy Optimization): 
    - optimizes policies while ensuring small deviations from the previous policy. It’s simpler to implement, easier to tune and often performs as well as or better than other state-of-the-art methods.
- <b>TQC</b> (Truncated Quantile Critics):
    - designed to alleviate overestimation bias in continuous control settings. It combines three ideas: distributional representation of a critic, truncation of critics prediction and ensembling of multiple critics.
- <b>TD3</b> (Twin Delayed Deep Deterministic Policy Gradient):
    -  an actor-critic RL method that seeks an optimal policy maximizing expected cumulative long-term reward. It’s an extension of the DDPG algorithm, with modifications to reduce value function overestimation.
- <b>SAC</b> (Soft Actor-Critic):
    - an off-policy actor-critic deep RL algorithm based on the maximum entropy reinforcement learning framework. The actor aims to maximize expected reward while also maximizing entropy, balancing exploration and exploitation of the environment.
- <b>ARS</b> (Augmented Random Search):
    - a policy-based method that seeks to maximize reward through random perturbations in the policy’s parameter space. It’s simple, efficient, and performs comparably to more complex model-free methods.

### Evaluation metrics

1. Maximize total episodic reward while avoiding excessive energy consumption.
2. Huggingface score: mean_reward - std_dev_reward.
3. Human feedback - analyze agent video.
4. Learning speed: number of epochs until convergence to 300 reward.

### Analysis of the results

As described in the paper, the agents from BipedalWalker-v3 successfully solved the environment and obtained competitive and performant results, as described in the problem's definition and compared with others' solutions from Huggingface leaderboard. Furthermore, the ARS showcased a dramatic increase in the learning speed. 

However, with the hardcore version of the environment, BipedalWalkerHardcore-v3, the agents struggled, indicating a need of implementing more advanced techniques in order to solve the environment. Still, compared with stable-baselines3 pretrained models published on the Huggingface, they still obtained proficient results.

Visually, the agents fell into one of the 4 walking strategies: the optimal Double Balance, the fastest Double Balance and the Single Balance on one leg (front or rear).

### Agent behaviour

Watch how the agent behaves in the <i>Video Preview</i> section.

Simple version:
[PPO](https://huggingface.co/MadFritz/ppo-BipedalWalker-v3)
[ARS](https://huggingface.co/MadFritz/ars-BipedalWalker-v3)
[TQC](https://huggingface.co/MadFritz/tqc-BipedalWalker-v3)
[TD3](https://huggingface.co/MadFritz/td3-BipedalWalker-v3)
[SAC](https://huggingface.co/MadFritz/sac-BipedalWalker-v3)

Hardcore version:
[PPO](https://huggingface.co/MadFritz/ppo-BipedalWalkerHardcore-v3)
[ARS](https://huggingface.co/MadFritz/ars-BipedalWalkerHardcore-v3)
[TQC](https://huggingface.co/MadFritz/tqc-BipedalWalkerHardcore-v3)
[TD3](https://huggingface.co/MadFritz/td3-BipedalWalkerHardcore-v3)
[SAC](https://huggingface.co/MadFritz/sac-BipedalWalkerHardcore-v3)