<p>This document provides the first required steps for getting everything ready to research in reinforcement learning using OpenAI gym simulation environments and PyBullet physics engines. The are a few things that should be noted:</p>
<ul>
<li>The aim of this repository is to save the initial time students spend to start working on reinforcement learning.</li>
<li>You can NOT learn reinforcement learning here, it has been assumed that you have some level of familiarity with&nbsp;reinforcement learning and want to use this document to start tools that require to implement algorithms quickly.</li>
</ul>
<p>This document has been provided as part of my teaching assistant responsibilities for the machine learning course at Lamar University, instructed by Prof. P. Doerschuk.</p>
<p>Please feel free to contact me (<a href="mailto:moazami.iut@gmail.com">moazami.iut@gmail.com</a>) if you have any questions.</p>
<p>&nbsp;</p>
<ul>
<li><strong>Python installation:</strong></li>
</ul>
<p>I highly recommend the installation of the latest python version using anaconda distribution:</p>
<p><a href="http://www.anaconda.com/distribution/">www.anaconda.com/distribution/</a></p>
<p>please make sure to download the correct version selecting the appropriate operating system and python 3.X version. You can go through installation steps using the instructed proved by anaconda:</p>
<p><a href="https://docs.anaconda.com/anaconda/install/">docs.anaconda.com/anaconda/install/</a></p>
<p>&nbsp;</p>
<p>Run jupyter notebook after installation. It will open a browser.</p>
<p>You also can see other installed tools through anaconda navigator installed on your system.</p>
<p>You can start writing your python cone in jupyter now. Direct to a directory and create a new python3 file.</p>
<p>&nbsp;</p>
<p>&nbsp;</p>

``` Python
# *******************************************************************************************
# Import required libraries.

import numpy as np
import gym

# *******************************************************************************************
# Create the gym environment.

env = gym.make('CartPole-v0')

state_size = env.observation_space.shape[0]
action_size = env.action_space.n

print("State space size: ",state_size)
print("Action space size: ", action_size,"\n")

n_episodes = 20

# *******************************************************************************************
# Define the agent class, Depending on the algrithm this can have many methods (functions)
# act() function is the policy that receives an observation and returns action. 

class Agent:
    
    def __init__(self, state_size, action_size):
        self.state_size    = state_size
        self.action_size   = action_size        
               
    def act(self, state):
        act = np.random.randint(self.action_size)
        return act

# *******************************************************************************************
# Instanciate an agent

agent = Agent(state_size, action_size)    

done = False                      # done is a boolean variable and is set to true when the algorithm terminates

for episode in range(n_episodes): # This is the total number of episodes loop
    
    state = env.reset()           # We should reset() the environment to start from an initial random ...
                                  # state at the beginning of every episode 
        
    for time_step in range(200):  # 200 is the maximum time step for CartPole problem
        
        action = agent.act(state) # The agent receives the observation (state) and takes actions accordingly
        
        env.render()              # Comment out to prevet rendering to save time.

        next_state, reward, done, _ = env.step(action) # step() receives action and returns next step, reward, done,
                                                       # info. it actually runs the dynamics of the env for one step
    
        state = next_state
        
        if done:                  # done indicates termination of an episode
            
            print("Episode: {}/{}, Score: {}".format(episode+1, n_episodes, time_step))
            
            break    
```

``` Shell
$ pip install gym
```

