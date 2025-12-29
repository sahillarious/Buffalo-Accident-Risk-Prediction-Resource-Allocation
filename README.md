# Buffalo Accident Risk Prediction & Resource Allocation 🚒🚔🚑

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![RL](https://img.shields.io/badge/Reinforcement%20Learning-PPO-green.svg)](https://openai.com/blog/openai-baselines-ppo/)
[![Framework](https://img.shields.io/badge/Library-PyTorch-EE4C2C.svg)](https://pytorch.org/)

[cite_start]An intelligent system designed to optimize the placement of emergency resources (Police, EMS, Tow Trucks) across Buffalo, NY, using **Proximal Policy Optimization (PPO)**[cite: 419, 424]. [cite_start]By bridging historical accident data with agentic reasoning, this system dynamically allocates resources to minimize response times and maximize coverage in high-risk zones[cite: 423, 429].

---

## 📌 Project Overview
Urban emergency response is often static and slow to adapt to real-time risk. [cite_start]This project addresses approximately 10,000 annual traffic incidents in Buffalo by[cite: 427, 429]:
* [cite_start]**Analyzing Risk Patterns:** Identifying hotspots from historical data across 145 grid cells (500m × 500m each)[cite: 431, 449, 452].
* [cite_start]**Dynamic Allocation:** Developing an RL framework that determines optimal placement for different accident types[cite: 432, 424].
* [cite_start]**System Efficiency:** Significantly outperforming random allocation baselines in meeting city-wide safety needs[cite: 425, 965].



---

## 🛠️ Technical Architecture

### 1. Data Analysis & Preprocessing
* [cite_start]**Source:** Real-world "Received Traffic Incident Calls" from the City of Buffalo Open Data Portal[cite: 437, 438].
* [cite_start]**Classification:** Incidents categorized into **Property Damage**, **Injury**, and **Skyway/High-speed** (Skyway/33/198) accidents[cite: 443, 446].
* [cite_start]**Probability Mapping:** Calculated the probability of each accident type occurring per grid cell to define "need levels" (Low, Medium, High)[cite: 450, 826, 840].

### 2. Reinforcement Learning Framework (MDP)
* [cite_start]**State Space:** A comprehensive vector representing accident probabilities, total available resources, current allocation status, and cell resource limits[cite: 809, 814].
* [cite_start]**Action Space:** Three-part discrete actions: Action Type (allocate/deallocate), Resource Type index (Police, EMS, DOT), and Target Grid Cell index[cite: 815, 819].
* [cite_start]**Algorithm:** **PPO (Proximal Policy Optimization)** was selected for its stability and performance on complex control tasks, utilizing an Actor-Critic architecture[cite: 827, 828, 945].

### 3. Resource Requirements
[cite_start]The agent learns to fulfill specific resource sets based on accident profiles[cite: 834, 953]:
* [cite_start]**Accident/Injury:** Requires Police and Ambulance (EMS)[cite: 835].
* [cite_start]**Property Damage:** Requires Police and Tow Truck (DOT)[cite: 838].
* [cite_start]**Skyway/33/198:** Requires Police, Ambulance (EMS), and Tow Truck (DOT)[cite: 839].

---

## 📈 Reward Engineering
[cite_start]The agent's intelligence is driven by a sophisticated reward structure (Structure 2)[cite: 849, 875]:
* [cite_start]**Met Need Reward:** High positive feedback (**1000.0 base**) for fulfilling medium/high-need grid requirements, scaled by a factor of 3.0 for high-need zones[cite: 878, 879, 894].
* [cite_start]**Unused Resource Penalty:** Incentivizes proactive deployment by penalizing idle units (**-5.0 per unit**)[cite: 887, 896].
* [cite_start]**Operational Penalties:** Costs for invalid actions like over-allocation (-2.0) or attempting to deploy units from an empty pool (-20.0)[cite: 889, 890, 898].

---

## 📊 Results & Performance
[cite_start]The PPO agent achieved a massive performance gap over baseline models, demonstrating a strategic ability to cluster complementary resources in hotspots[cite: 1022, 1038].

| Metric | PPO Agent | Random Baseline | DQN Agent |
| :--- | :--- | :--- | :--- |
| **Total Episode Reward** | [cite_start]**~793** [cite: 1003] | [cite_start]-8170 to -8230 [cite: 981] | [cite_start]~ -47,500 [cite: 966] |
| **Behavior** | [cite_start]Strategic Clustering [cite: 1038] | [cite_start]Wasteful/Invalid [cite: 1023] | [cite_start]Hesitant/Incomplete [cite: 980] |



---

## 🚀 Future Work
* [cite_start]**Temporal Variations:** Incorporating time-of-day, seasonal patterns, and traffic flow into risk probabilities[cite: 1176].
* [cite_start]**Real-time Integration:** Using live traffic data to improve response time estimates[cite: 1177].
* [cite_start]**Hierarchical RL:** Implementing hierarchical approaches to handle multiple resource types more effectively[cite: 1178].

---

## 👥 Contributors
* [cite_start]**Meghna Trichur Saravana Shekhar** [cite: 420]
* [cite_start]**Sahil Shivaji Sawant** [cite: 420]
* [cite_start]**Fagun Nirag Patel** [cite: 420]

[cite_start]*Project developed at the School of Engineering & Applied Sciences, University at Buffalo*[cite: 422].
