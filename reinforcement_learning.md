## Intro to Reinforcement Learning and Planning
Reinforcement Learning is all about learning by trial and error through interaction. It is a continuous and cyclic conversation between the agent and the environment.

Let's introduce the basic jargon of RL.
- **Agent**: Agent is the brain of RL, it is the controller or algorithm that interacts with the environment and makes decisions based on the interaction.
- **Environment**: It is the world where the agent interacts, and it executes the agent's decision and provides feedback. Based on the feedback, the agent takes next steps.

Now we will learn about the Mathematical Vocabulary of RL.
- **State($S_t$)**: State is the snapshot of the environment at a specific moment, which is used by the agent to make a decision. In other words, states are being observed by the agent.
  - _For example, an Intersection Control Agent observes the **Queue Length** of lanes, **Waiting Time** of vehicles, etc., to efficiently change the signal phase;
 in that case **Queue Length**, **Waiting Time** are the states for this agent_.
- **Action($A_t$)**: Decision on control input chosen by the agent based on the states that it observed.
  - Action 0: Keep the current Green Phase on
  - Action 1: Switch to yellow/red phase.
- **Reward($R_t$)**: This is the single scalar number returned by the Environment after executing the action. It actually evaluates how good or bad the action was in that immediate short term.
  The ultimate goal is to maximize the total accumulation of the rewards.

## The RL Loop
The agent observes the states of the world and makes a decision or action. The environment executes that action in the environment and evaluates this action by calculating the reward.
Finally, the agent sends that reward and the next state ($S_{t+1}$) corresponding to the action that was made by the agent.
