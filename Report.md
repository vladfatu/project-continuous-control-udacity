# Report

### Learning Algorithm

To solve this environment, I used a DDPG agent. I started from Udacity's [agent](https://github.com/udacity/deep-reinforcement-learning/blob/master/ddpg-pendulum/ddpg_agent.py) for the pendulum Gym environment.

- #### Network architecture

- #### Hyperparameters


<strong>BUFFER_SIZE = 1e5</strong> (this is size of the replay buffer used to store experiences)\
<strong>BATCH_SIZE = 128</strong> (this is the number of random samples chosen from the replay buffer when training)\
\
<strong>LR_ACTOR = 1e-3</strong> (actor network learning rate)\
<strong>LR_CRITIC = 1e-3</strong> (critic network learning rate)\
<strong>GAMMA = 0.99</strong> (discount factor)\
\
<strong>TAU = 1e-3</strong> (factor used when updating the target network)\
<strong>WEIGHT_DECAY = 0</strong> (L2 weight decay)


### Results

I was able to solve the environment in 43 episodes.

<img width="540" alt="Training Graph" src="https://github.com/vladfatu/project-continuous-control-udacity/assets/1000350/5c0f8db0-f6c1-4c3d-b7ce-32866787f39d">

### Future Improvements
