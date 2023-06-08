# Defining-and-Solving-Reinforcement-Learning-Task


The primary objective of this repository is to gain hands-on experience in formulating and addressing reinforcement learning (RL) challenges by adhering to the standards set by the Gym library. The project encompasses three distinct components. 

Initially, we concentrate on designing an environment that conforms to the principles of a Markov decision process (MDP).

Subsequently, in the second phase, we employ the SARSA algorithm, a tabular RL method, to tackle a pre-defined environment. 

Lastly, we employ the Q-learning technique to resolve a grid-world environment. Through these progressive steps, we aim to enhance our understanding and proficiency in RL problem-solving.




# Environment details

The environment we defined is a grid world called LawnmowerGridWorld with a 4x4 grid. The agent starts at the top left corner and its objective is to reach the bottom right corner. 

The agent can move up, down, left, or right on the grid. The states in the environment are defined by the agent's position on the grid, which is represented as a tuple of two integers (x, y). The state space is discrete and contains 16 possible states.

The actions that the agent can take are moving up, down, left, or right on the grid. The action space is discrete and contains four possible actions.

The rewards in the environment are defined by a dictionary that maps each state to a reward. Some of the positions in the grid have a positive reward, which encourages the agent to move towards those positions. Other positions have a negative reward, which discourages the agent from moving towards those positions. The agent receives a reward only when it reaches the goal position.

The main objective of the agent is to maximize its cumulative reward by reaching the goal position as quickly as possible. The agent must also avoid the positions with negative rewards, as moving onto those positions will result in a penalty.

# Environment requirements:

• Min number of states: 12

• Min number of actions: 4

• Min number of rewards: 4

Red Grid: Agent
Grey Grid: Negative Rewards
Green Grid: Positive Rewards
White Grid: Goal


# SARSA
In SARSA, the algorithm learns the Q-values directly from interactions with the environment. It follows an on-policy approach, meaning it learns the Q-values while following the exploration policy.

• Initialize the Q-table with arbitrary values or zeros.
• Select an action based on the current state using an exploration-exploitation strategy.
• Take action, observe the next state and the reward.
• Update the Q-value of the current state-action pair using the SARSA update equation.
• Repeat steps 2-4 until the termination condition is met.
• Repeat the process for multiple episodes to improve the estimate of Q-values and learn the optimal policy.

Update Function: Q(s, a) <- Q(s, a) + learning_rate * (reward + discount_factor * Q(s', a') - Q(s, a))

Key Features:
• On-policy TD learning algorithm.
• Learns the Q-values directly from interactions with the environment.
• Selects actions based on an exploration-exploitation strategy (e.g., epsilon-greedy).
• Updates the Q-value of the current state-action pair using the observed reward and the Q-value of the next state-action pair.

Advantages:
• Converges to the optimal policy for both episodic and continuing tasks.
• Considers the actual actions taken during the learning process.
• Suitable for environments with a small state-action space.

Disadvantages:
• May be slower to converge compared to off-policy algorithms.
• Prone to being influenced by the exploration strategy and can get stuck in suboptimal policies.
• Not suitable for environments with large state-action spaces due to the need for a Qtable



# Q learning
Q-learning learns the Q-values through an iterative process of exploration and exploitation. The Q-values represent the expected return (or cumulative reward) an agent can obtain by taking a particular action in a specific state.

Update Function: Q(s, a) <- Q(s, a) + learning_rate * (reward + discount_factor * max(Q(s', a')) -Q(s, a))

Key features of Q-learning:
• Off-policy learning: Q-learning learns the optimal policy even if the agent follows a different exploration policy.
• Model-free: Q-learning does not require a model of the environment dynamics, making it suitable for environments with unknown transition probabilities.
• Convergence: Q-learning is guaranteed to converge to the optimal Q-values under certain conditions, such as exploring all state-action pairs infinitely.

Advantages of Q-learning:
• Flexibility: Q-learning can handle large state and action spaces by using a tabular representation.
• Model-free: Q-learning can learn directly from interaction with the environment without prior knowledge of the dynamics.
• Convergence: Q-learning is guaranteed to converge to the optimal Q-values with infinite exploration.

Disadvantages of Q-learning:
• Computational complexity: In environments with large state and action spaces, the size of the Q-table can become prohibitively large.
• Exploration-exploitation trade-off: Finding the right balance between exploration and exploitation can be challenging, especially in complex environments.
• Lack of generalization: Tabular Q-learning is specific to the states and actions encountered during training and may not generalize well to unseen states.
