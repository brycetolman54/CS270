# Reinforcement Learning

- We have an agent.
- He has a state, then he can do some actions to change that.
- He learns to take good actions that lead him from one state to another.

- If we just make actions based on the state, this is Markovian.
- If we take into account past actions, that is not Markovian.
- We are going to do things in a Markovian fashion.

- We need some reward (positive for good things, negative for bad things)
- This reward is how we train.
- We can do discounted rewarding, looking to the future and taking that into account, but making that count less the further we go
    - We have some $\gamma$ that is between 0 and 1 that determines this discount

# Q Learning

- Just try an action, see what state you are in and what reward you got, update your policy
- Rather than find the value function of a state, find the Q-value (the s,a pair)
- You just try actions from a state and update the policy based on the reward
- Q(s,a) = sum of discounted reward for doing an action (a) from a state (s) and following the policy thereafter
    - $Q(s,a)=r(s,a)+\gamma max_{a'}Q(s',a')$
- So, we have to have a reward function for moving from state to state, that gives us our reward values.
- We also have a Q value for going from each state to each other state
    - We initialize these, but then they change as we traverse the map

- Exploitation is getting the best Q value.
- Exploration is trying out new states
- We tend to start with exploration and then move over to exploitation


