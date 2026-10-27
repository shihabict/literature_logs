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
--- 
# Reinforcement learning and Collective Cooperation on higher-order networks
Authors: Yan Xu et al. <br>
Venue: Elsevier --- Knowledge-Based Systems <br>
GitHub: Not provided<br>
[Paper Link](https://www.sciencedirect.com/science/article/pii/S0950705124009602)

In this paper, they combined **Evolutionary Game Theory** with **RL** to investigate the influence of a dynamic environment on **Group Cooperation**. **Active agent** used social learning to update policy over time, whereas for **inactive agent** they introduced **varying reward*** to maintain cooperation. From their investigation, they found that **meduim sized** environment is favourable for collective cooperation.

### What is Evolutionary Game Theory?
Evolutionary Game Theory **(EGT)**, studies the games played by not a few rational, calculated player, but a large populations whose strategies spread  or die out over time based on their performance. 

**EGT ASK:** _If large numbers of individuals with different strategies keep meeting each other, which strategies will take over the population?_

### What is the Public Goods Game?
It is a **group game**, where each player decides how to contribute to a **shared pot**. After that, the pot is multiplied by a factor of $r$ (where $1 < r < N$) and split **equally** among all players. The condition of the multiplier factor is the **dilemma**: if you contribute and others do not, your return will be $\frac{\text{your contribution} \times r}{N}$, which will be less than your actual contribution.

## Proposed Model
Their framework consists of three integral parts: **Higher-order network constuction**, **Initialization**, and **Evolutionary process**.
### 1. Higher-order Network Construction
To generate the hypergraph,
- **Initialize**: Start with $g$ nodes; every hyperedge should have g nodes.
- **Hyperedge growth**: Added $m \in[1,g)$ new nodes and combine them with $(g-m)$ exisiting nodes.
- **Preferential Attachment**: Probability of selection node $i$ is proportional to  its hyperdegree $d_H(i)$
  $$\muld_H(i) = \frac{d_H(i)}{\sum_{j\inN}d_H(j)}$$. A node in many groups is more likely to be picked again.
- Repeat steps 2 and 3 until an N-node hypergraph is generated.
![Hypergraph Creation](images/hypergraph_creation.png)
---
### 2. Initialization
Nodes correspond to agents, and hyperedges correspond to connections among them. 
- Strategy (row) $S = \{C,D\}$, C means **Cooperation** and D means **Defection**(do noting).
- Actions (columns) $A = \{A,I\}$, A means **Active** (Stay in the game) and I means **Inactive** (Leave the game)
- Each agent has its own Q-table
- All entries are initialized to $0$

**Q-table of agent *i* at time *t* (Eq. 6)**

| State \ Action | A (active) | I (inactive) |
|---|---|---|
| **C** (cooperate) | Q<sup>i</sup><sub>C,A</sub>(t) | Q<sup>i</sup><sub>C,I</sub>(t) |
| **D** (defect) | Q<sup>i</sup><sub>D,A</sub>(t) | Q<sup>i</sup><sub>D,I</sub>(t) |



