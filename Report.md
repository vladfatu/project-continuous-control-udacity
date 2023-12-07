# Report

### Learning Algorithm

To solve this environment, I used a DDPG agent. I started from Udacity's [agent](https://github.com/udacity/deep-reinforcement-learning/blob/master/ddpg-pendulum/ddpg_agent.py) for the pendulum Gym environment based on this [paper](https://arxiv.org/pdf/1509.02971.pdf) by Google DeepMind. 
\
\
The pendulum Gym environment has a single agent while the Reacher environment I am trying to solve has 20 identical agents running at the same time. So I had to adjust the code from Udacity to support multiple agents. 
\
I changed it so that at each time step, all experiences from all agents are added to the replay buffer and the local Actor and Critic networks are updated once using a sample from the replay buffer.
\
Another change I needed to make was to the noise. In the Udacity agent, Ornsetein-Uhlenbeck noise is added to the actor policy as this helps with exploration in physical environments that have momentum. No complicated changes were required, I just needed to make sure noise was generated separately for each agent.

- #### Network architecture

DDPG contains 2 networks, an Actor and a Critic.
- actor:
The input to the actor network has 33 dimensions and contains the position, rotation, velocity, and angular velocities of the arm. This is followed by 2 hidden Linear Layers of size 128 activated by a RELU activation function. The output has a size of 4 and is activated by a tanh activation function.
- critic:
The input to the critic network has the same 33 dimensions as the Actor network. This is followed by a hidden Linear Layer of size 128 activated by a RELU activation function. Next, there is another hidden Linear Layer of size 132(128 from the previous layer + 4, the action provided by the Actor network). This layer is also activated by a relu activation function. Finally, the output has a size of 1.

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
