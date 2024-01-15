## Ablation Study - [Github Repository](https://github.com/pricoptudor/ATNN_PricopTudor/tree/main/FinalProject)

### Study components

1. <b>Abstract</b>: A concise overview of the study, which applies various reinforcement learning (RL) algorithms to solve the BipedalWalker environment from OpenAI Gym, a challenging benchmark for continuous control tasks. The paper compares the performance of five RL algorithms: Proximal Policy Optimization (PPO), Truncated Quantile Critics (TQC), Twin Delayed Deep Deterministic Policy Gradient (TD3), Soft Actor-Critic (SAC) and Augmented Random Search (ARS). It also analyzes the learning dynamics, strengths and limitations of each algorithm.
2. <b>Introduction</b>: A brief introduction to the problem of bipedal locomotion, the motivation for using RL techniques, the structure of the paper and the main contributions.
3. <b>Problem Description</b>: A detailed description of the BipedalWalker environment, including the action space, the observation space, the rewards, the starting state and the episode termination conditions. The paper also explains the different walking strategies that the agent can learn and describes the difficulty of the task.
4. <b>Algorithms</b>: A comprehensive explanation of the RL algorithms used in the study, including their pseudocode, their key features and their advantages and disadvantages. The paper covers the algorithms in the abstract, highlighting their differences and similarities.
5. <b>Experiments</b>: A description of the experimental design, including the hyperparameter tuning, the computational resources, the training pipeline and the performance metrics. The article also explains how to use the Hugging Face Hub to access the trained models and the evaluation results.
6. <b>Results and Interpretation</b>: A presentation and interpretation of the results of the experiments, including the learning curves, the scores, the videos and the statistics of the agents. The paper provides a comparative analysis of the RL algorithms, assessing their convergence rates, solution quality and computational efficiency. It also discusses the challenges and limitations of the algorithms and the variants of the environment.
7. <b>Conclusion and Future Directions</b>: A summary of the key findings of the study, their implications, the potential avenues for future research and the concluding remarks. It also lists the references cited throughout the paper.

### Agent behaviour

Watch how the agent behaves in the <i>Video Preview</i> section.

Simple version:
[PPO](https://huggingface.co/MadFritz/ppo-BipedalWalker-v3)
[ARS](https://huggingface.co/MadFritz/ars-BipedalWalker-v3)
[TQC](https://huggingface.co/MadFritz/tqc-BipedalWalker-v3)
[TD3](https://huggingface.co/MadFritz/td3-BipedalWalker-v3)
[SAC](https://huggingface.co/MadFritz/sac-BipedalWalker-v3)

![normal](https://github.com/pricoptudor/ATNN_PricopTudor/blob/main/FinalProject/Images/bipedal-normal.png)

It seems that all methods were able to reach a score of over 300, while not making more than 1600 steps per episode, meaning they successfully solved the environment.
While the ARS agent seems to learn the optimal strategy: the Knee Balance, the others try to hurry, learning to run as fast as they can: the Double Balance strategy. (see [documentation](https://github.com/pricoptudor/ATNN_PricopTudor/blob/main/FinalProject/ATNN_final.pdf) for details on walking strategies)

Hardcore version:
[PPO](https://huggingface.co/MadFritz/ppo-BipedalWalkerHardcore-v3)
[ARS](https://huggingface.co/MadFritz/ars-BipedalWalkerHardcore-v3)
[TQC](https://huggingface.co/MadFritz/tqc-BipedalWalkerHardcore-v3)
[TD3](https://huggingface.co/MadFritz/td3-BipedalWalkerHardcore-v3)
[SAC](https://huggingface.co/MadFritz/sac-BipedalWalkerHardcore-v3)

![hardcore](https://github.com/pricoptudor/ATNN_PricopTudor/blob/main/FinalProject/Images/bipedal-hardcore.png)

None of the agents were able to get to a score of 300, meaning they could not solve the environment. In fact, only one of them managed to understand a bit how to take over the obstacles: TQC.
Visually, ARS, TD3 and PPO are trying to double balance the agent (until it falls or gets stuck), while SAC and TQC found that the best balancing method is on the rear leg.

### Findings

As seen in the [documentation](https://github.com/pricoptudor/ATNN_PricopTudor/blob/main/FinalProject/ATNN_final.pdf), the best results in both variants of the environment are obtained using the <b>TQC</b> agent, due to its aim of improving off-policy learning in <i>continuous control</i> tasks.
It is worth mentioning the <b>ARS</b> algorithm, which proved to be highly efficient with sampling good policies in a short amount of time.

While some of the algorithms can benefit from a vectorized environment composed of stacking multiple instances, and also benefitting from GPU training: PPO, SAC and TQC, others are not suited for this, as they are built to work on a single instance of the environment at a time: ARS and TD3.

A relevant conclusion of this study is that the vanilla implementation of the state-of-the-art RL methods are enough to solve the simple version of the BipedalWalker environment, but more resources and more advanced methods (like <b>FORK</b> - Forward-Looking Actor for Model-free RL) are needed in order to solve the hardcore version of the BipedalWalker.