# Implementation

The training algorithm used here is DDPG. In addition to DDPG, several additional techniques were used:-
- PER(Prioritized Experience Replay) with annealing beta from 0.4 to 1 and alpha as 0.4
- Gaussian noise with standard deviation decay from 0.4 to 0.001. This should emulate epsilon decay in used in A2C or A3C.
- Dual Critic networks.
- Learning rate step decay.

## Hyperparameters

- Alpha=0.5
- Beta annealing from 0.4 to 1
- Gaussian noist std deviation decay from 0.4 to 0.001
- Replay Buffer size=50000
- Gamma=0.995
- Learning rate step decay of 0.5 every 100 episodes
- n-steps=4

## Training

Most of the training was done on single agent headless environment to optimize the hyperparameters iteratively. From the last single agent training, it was evident that even a single agent 
can achieve the benchmark in about 350 episodes. Following is the plot from test run

<img width="543" height="413" alt="image" src="https://github.com/user-attachments/assets/8e8581b7-c1f8-447c-9b4c-08f491e7cb3d" />

After enabling multi agent training with 20 parallel instances, we can see a dramatic reduction in training convergence time.

<img width="543" height="413" alt="image" src="https://github.com/user-attachments/assets/a07d97e8-a931-4624-9eae-f6004d19819b" />


