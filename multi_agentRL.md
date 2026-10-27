# MAgent: A Many-Agent Reinforcement Learning Platform for Artificial Collective Intelligence

Authors: Lianmin Zheng et al. <br>
Venue: NIPS 2017 and AAAI 2018 <br>
Github Link : [Github](https://github.com/geek-ai/MAgent) <br>
Demo Video: [Youtube](https://www.youtube.com/watch?v=HCSm0kVolqI) <br>

---

<p align="center">
  <a href="https://www.youtube.com/watch?v=HCSm0kVolqI">
    <img src="https://www.youtube.com" alt="Watch the video" width="70%">
  </a>
</p>


### Contribution
 - They proposed a highly scalable **Many Agent** platform that can host millions of agents on a GPU server.
 - MAgent provides environment, agent configurations, and a reward description language to enable flexible environment design.
 - Illustrate three running examples of **Many Agent** simulation of pursuitting, gathering, and battlefield agents.
 - Implemented three parameter-sharing DQN, DRQN, and A2C and found DQN performed best in their setting.

 ### Limitations
 - Not enough technical details about the environment, agent communications, reward design, states, and actions.
 - Not provided architectural details of the platform.

 Note: Maybe they shared it in another paper; I have to find that out to understand the internal mechanics.

 ---

 # Multi-Agent Deep Reinforcement Learning: A Survey
 Authors: Sven Gronauer and Klaus Diepold
<br>
Venue: AI Review, 2022. Springer <br>
GitHub: <br>

### Contribution
In this survey, they addressed
- Training Schemes of MARL
  - Centralized Training, Centralized Execution (CTCE)
  - Centralized Training, Decentralized Execution (CTDE)
  - Distributed training, decentralized execution (DTDE)
- Agent Behaviour Patterns
  - Cooperative
  - Competitve
  - Mixed Scenarios
- Kernel Challenges in MARL
  - Non-stationarity
  - Shadowed Equilibrium
  - Partially Observable Markov Games
  - Credit Assignment Problem
 
- Messaging between Agents
  - Broadcasting Communication, where an agent broadcasts information to all participants in the channel.
  - Networked Communication, where agents exchange information with their neighbourhood.
- Future Direction
  - **Multi-goal learning**. where each agent optimizes its own goal instead of joint action or reward.
  - **Multi-task Learning**, agent not only performs one task, but also other related tasks.
  - **Safe MADRL**
 
# Reinforcement learning and Collective Cooperation on higher-order networks
Authors: Yan Xu et al. <br>
Venue: Elsevier - Knowledge Based Systems <br>
GitHub: Not provided<br>

In this paper, they combined **Evolutionary Game Theory** with **RL** to investigate the influence of a dynamic environment on **Gruop Cooperation**. **Active agent** used social learning to update policy over time, whereas for **inactive agent** they introduced **varying reward*** to maintain cooperation. From their investigation, they found that **meduim sized** environment is favourable for collective cooperation.
