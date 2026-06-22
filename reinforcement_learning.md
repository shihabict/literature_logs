## Overview

This document provides foundational notes, literature logs, and algorithmic implementations for Reinforcement Learning. It serves as a living knowledge base to complement theoretical materials from standard texts, alongside applied research in Intelligent Transportation Systems. 


Each section below contains a conceptual breakdown of the mathematics, followed by practical implementations.

### Table of Contents

* [Introduction to RL and Planning](#intro-to-reinforcement-learning-and-planning)
* [Bellman Equations](#the-bellman-equation-the-mathematical-heartbeat-of-rl)
* [Model-Free Reinforcement Learning](#model-free-reinforcement-learning)
  * [Monte Carlo (MC) Methods](#monte-carlo-mc-methods-learning-at-the-end)
  * [Temporal-Difference (TD) Learning](#temporal-difference-td-learning-learning-every-step)
<!-- * [Dynamic Programming: Model-Based RL](#)
* [Monte Carlo Model-Free Prediction & Control](#)
* [Temporal Difference (TD) Learning](#)
* [Deep Reinforcement Learning (DQN, PPO)](#)
* [Explainable AI (XAI) in Reinforcement Learning](#)
* [Integration of Diffusion Policy Networks in RL](#) (WIP)

### List of Implemented Algorithms

**Tabular Methods**
* [Dynamic Programming: Policy Evaluation & Iteration](#)
* [Dynamic Programming: Value Iteration](#)
* [Monte Carlo Control with Epsilon-Greedy Policies](#)
* [SARSA (On-Policy TD Learning)](#)
* [Q-Learning (Off-Policy TD Learning)](#)

**Deep Reinforcement Learning & Applications**
* [Deep Q-Learning (DQN) with Prioritized Experience Replay](#)
* [Policy Gradient: REINFORCE with Baseline](#)
* [Minimalistic Intersection Controller (33-Dimension State Space)](#)
* [Explainable RL for Traffic Congestion Mitigation](#) 
* [Diffusion Policy Networks for Traffic Signal Control](#) (WIP)
-->












## Intro to Reinforcement Learning and Planning
Reinforcement Learning is all about learning by trial and error through interaction. It is a continuous and cyclic conversation between the agent and the environment.

Let's introduce the basic jargon of RL.
- **Agent**: Agent is the brain of RL, it is the controller or algorithm that interacts with the environment and makes decisions based on the interaction.
- **Environment**: It is the world where the agent interacts, and it executes the agent's decision and provides feedback. Based on the feedback, the agent takes the next steps.

Now we will learn about the Mathematical Vocabulary of RL.
- **State($S_t$)**: State is the snapshot of the environment at a specific moment, which is used by the agent to make a decision. In other words, states are being observed by the agent.
  - _For example, an Intersection Control Agent observes the **Queue Length** of lanes, **Waiting Time** of vehicles, etc., to efficiently change the signal phase;
 in that case **Queue Length**, **Waiting Time** are the states for this agent_.
- **Action($A_t$)**: Decision on control input chosen by the agent based on the states that it observed.
  - Action 0: Keep the current Green Phase on
  - Action 1: Switch to yellow/red phase.
- **Reward($R_t$)**: This is the single scalar number returned by the Environment after executing the action. It actually evaluates how good or bad the action was in that immediate short term.
  The ultimate goal is to maximise the total accumulation of the rewards.

## The RL Loop
The agent observes the states of the world and makes a decision or action. The environment executes that action in the environment and evaluates this action by calculating the reward.
Finally, the agent sends that reward and the next state ($S_{t+1}$) corresponding to the action that was made by the agent.

<img src="images/rl_loop.png" width="500" height="200">

*Figure 1: Reinforcement Learning Loop*
 - **Episode**: Episode is one complete sequence of the RL loop from the initial state $S_0$ to the designated **terminal state**. Once the agent reaches the terminal state, the environment resets to the initial state and starts a new episode.
   - For example, running a traffic simulation of the rush morning hour starts from 6 AM($S_0$) and terminates at 9 AM($S_{\tau}$).
 - **Episode Length($T$)**: Total number of states an agent took to reach to the terminal state in a particular episode. If the traffic simulator updates every 1 second, a 3-hour rush episode has an episode length $T=10800$ steps.

## The Policy ($\pi$): Brain
The policy is simply the agent's rulebook, mapping the current state of the world to the action it should take. If the State is the question the environment asks, the Policy is the answer the agent gives.

Plocies comes in two flavours:

1. **Deterministic Policy**: The agent follows a strict, non-random rule. For a specific state, the agent will always take the same action. For example, a Chase agent, for specific moves it will take the same steps.

$$a= \pi(s)$$

2. **Stochastic Policy**: Instead of a specific action, a policy returns a probability distribution of all actions. In other words, given a state, the agent will choose an action randomly based on the probability distribution. For example, in a poker game, the agent may not always choose the same action for the same state.

$$\pi(a|s) = \mathbb{P}[A_t = a | S_t = s]$$

## Discount Factor $(\gamma)$
Gamma is a number between $0$ and $1$. We multiply future rewards by $\gamma$, compounding it for every step into the future.
The Discounted Return Equation:

$$G_t = R_{t+1} + \gamma R_{t+2} + \gamma^2 R_{t+3} + \dots = \sum_{k=0}^{\infty} \gamma^k R_{t+k+1}$$

How $\gamma$ shapes the agent's personality:

  - If $\gamma = 0$: The agent is perfectly short-sighted. It only cares about the immediate next reward ($R_{t+1}$).
  - If $\gamma = 0.99$: The agent is deeply strategic, heavily weighting events that happen far into the future.

## The Value Function
The value function tells us how good it is to be in a certain state or to take a certain action.

1. **State Value Function $(V_{\pi}(s))$**: It evaluates how good it is to be in a specific state.

$$v_\pi(s) = \mathbb{E}_\pi [ G_t | S_t = s ]$$

Where,
- $V_{\pi}(s)$: Value to be in the state S under $\pi$
- $\mathbb{E}_\pi$: Expected Value, assuming that the agent behaves according to policy $\pi$
- $G_t$: Total discounted return
- $S_t=s$: Starting from policy state s.

2. **Action Value Function $(Q_{\pi}(s, a))$**: The Q-value evaluates how good it is to take a specific action $a$ in a specific state $s$, and then follow policy $\pi$ forever after.

   $$q_\pi(s,a) = \mathbb{E}_\pi [ G_t | S_t = s, A_t = a ]$$

## The Bellman Equation: The Mathematical Heartbeat of RL
The Bellman equation describes how to estimate future rewards and make optimal decisions. It breaks a massive, infinite problem into a two-part recursive loop: **The Immediate Reward + The Discounted Value of the Next State** 

The Bellman equation actually says, you do not need to look all the way to the end goal to know your current value. If you only know the immediate reward of your next step and the value of the place where you land.

$$Value(Current) = Immediate\_{Reward} + \gamma \times Value(Next)$$

### Mathematics: Bellman Expectation for $v_\pi(s)$
---
$$v_\pi(s) = \sum_a \pi(a|s) \sum_{s', r} p(s', r | s, a) \left[ r + \gamma v_\pi(s') \right]$$

Let's read out this equation loud, 

> The value of begin in this current state s is..... $\sum_a \pi(a|s)$: average of all the actions my policy might choose, multiply by the average of all possible next states ($s'$) with reward ($r$) of the immediate reward, plus the discounted value of wherever I ended up.


## Model-Free Reinforcement Learning
In model-free Reinforcement Learning, the agent learns from experience. The agent interacts with the world or environment and learns by making mistakes and adjusting. There are two fundamental ways to learn from experience: **Monte Carlo (MC) Methods** and **Temporal-Difference (TD) Learning**.

### Monte Carlo (MC) Methods: Learning at the End
---
The agent plays through an entire episode from start to finish using its current policy. Once the episode hits a terminal state, the agent looks back at the total Return ($G_t$) it actually received, and it takes an empirical average of the actual returns.

To update the value of a state after an episode, we use an incremental update rule:

$$V(S_t) \leftarrow V(S_t) + \alpha \left[ G_t - V(S_t) \right]$$

Where,

- $V(S_t)$: Our current guess for the value of the state.
- $\alpha$ (Alpha): The Learning Rate. It determines how much we trust this new experience versus our old memory. (Usually a small number like 0.01).
- $G_t$: The actual return we got from this state until the end of the episode.
- $[ G_t - V(S_t) ]$: The Error. The difference between what we actually got and what we thought we were going to get.

**Trade-offs**:
- Strength: It is unbiased. The agent uses actual, observed returns ($G_t$), not guesses.
- Weakness 1 (High Variance): A single bad random action near the end of the episode will mathematically penalise perfectly good actions taken at the beginning.
- Weakness 2 (Episodic Only): You must wait until the end of the episode to learn anything. It cannot be used for continuous, never-ending tasks.

### Temporal-Difference (TD) Learning: Learning Every Step
---
Temporal-Difference (TD) learning allows the agent to update its value estimates continuously, step-by-step, without waiting for the episode to end. It does this using the core concept of the Bellman Equation: Bootstrapping (updating a guess based on another guess).

The update rule looks almost identical to MC, but instead of using the full return ($G_t$), we use the TD Target.

$$V(S_t) \leftarrow V(S_t) + \alpha \left[ R_{t+1} + \gamma V(S_{t+1}) - V(S_t) \right]$$

- $R_{t+1} + \gamma V(S_{t+1})$: This is the TD Target. It is the immediate reward you just got, plus the discounted guess of the value of the next state you landed in.
- $\left[ R_{t+1} + \gamma V(S_{t+1}) - V(S_t) \right]$: This is the TD Error. It is the fundamental signal in modern reinforcement learning. It measures the surprise between what you expected and what actually happened on that single step.

**Trade-offs**:
- Strength 1 (Real-Time Learning): The agent learns at every single time step. It does not need to wait for the end of an episode.
- Strength 2 (Low Variance): Because it only looks one step ahead, it isn't derailed by a long chain of random events.
- Weakness (Biased): At the beginning of training, $V(S_{t+1})$ is totally wrong. You are updating your guess based on a terrible guess, which can cause the algorithm to temporarily learn the wrong things until it eventually self-corrects.
