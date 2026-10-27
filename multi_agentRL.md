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
 - Implemented three parameter sharing DQN, DRQN, A2C and found DQN perform best in their setting.

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
  - Centralized Training Decentralized Execution (CTDE)
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
