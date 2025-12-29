# Buffalo Accident Risk Prediction & Resource Allocation 🚒🚔🚑

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![RL](https://img.shields.io/badge/Reinforcement%20Learning-PPO-green.svg)](https://openai.com/blog/openai-baselines-ppo/)
[![Framework](https://img.shields.io/badge/Library-PyTorch-EE4C2C.svg)](https://pytorch.org/)

An intelligent system designed to optimize the placement of emergency resources (Police, EMS, Tow Trucks) across Buffalo, NY, using **Proximal Policy Optimization (PPO)** By bridging historical accident data with agentic reasoning, this system dynamically allocates resources to minimize response times and maximize coverage in high-risk zones.

---

## 📌 Project Overview
Urban emergency response is often static and slow to adapt to real-time risk. [cite_start]This project addresses approximately 10,000 annual traffic incidents in Buffalo by:
* **Analyzing Risk Patterns:** Identifying hotspots from historical data across 145 grid cells (500m × 500m each).
* **Dynamic Allocation:** Developing an RL framework that determines optimal placement for different accident types.
* **System Efficiency:** Significantly outperforming random allocation baselines in meeting city-wide safety needs.
* 
---

## 🛠️ Technical Architecture

### 1. Data Analysis & Preprocessing
* **Source:** Real-world "Received Traffic Incident Calls" from the City of Buffalo Open Data Portal.
* **Classification:** Incidents categorized into **Property Damage**, **Injury**, and **Skyway/High-speed** (Skyway/33/198) accidents.
* **Probability Mapping:** Calculated the probability of each accident type occurring per grid cell to define "need levels" (Low, Medium, High).

### 2. Reinforcement Learning Framework (MDP)
* **State Space:** A comprehensive vector representing accident probabilities, total available resources, current allocation status, and cell resource limits.
* **Action Space:** Three-part discrete actions: Action Type (allocate/deallocate), Resource Type index (Police, EMS, DOT), and Target Grid Cell index.
* **Algorithm:** **PPO (Proximal Policy Optimization)** was selected for its stability and performance on complex control tasks, utilizing an Actor-Critic architecture.

### 3. Resource Requirements
The agent learns to fulfill specific resource sets based on accident profiles:
* **Accident/Injury:** Requires Police and Ambulance (EMS).
* **Property Damage:** Requires Police and Tow Truck (DOT).
* **Skyway/33/198:** Requires Police, Ambulance (EMS), and Tow Truck (DOT).

---

## 📈 Reward Engineering
The agent's intelligence is driven by a sophisticated reward structure (Structure 2):
* **Met Need Reward:** High positive feedback (**1000.0 base**) for fulfilling medium/high-need grid requirements, scaled by a factor of 3.0 for high-need zones.
* **Unused Resource Penalty:** Incentivizes proactive deployment by penalizing idle units (**-5.0 per unit**).
* **Operational Penalties:** Costs for invalid actions like over-allocation (-2.0) or attempting to deploy units from an empty pool (-20.0).

---

## 📊 Results & Performance
The PPO agent achieved a massive performance gap over baseline models, demonstrating a strategic ability to cluster complementary resources in hotspots.

| Metric | PPO Agent | Random Baseline | DQN Agent |
| :--- | :--- | :--- | :--- |
| **Total Episode Reward** | **~793** | -8170 to -8230 | ~ -47,500 |
| **Behavior** | Strategic Clustering | Wasteful/Invalid | Hesitant/Incomplete |



---

## 🚀 Future Work
* **Temporal Variations:** Incorporating time-of-day, seasonal patterns, and traffic flow into risk probabilities.
* **Real-time Integration:** Using live traffic data to improve response time estimates.
* **Hierarchical RL:** Implementing hierarchical approaches to handle multiple resource types more effectively.

---

## 👥 Contributors
* **Meghna Trichur Saravana Shekhar**
* **Sahil Shivaji Sawant** 
* **Fagun Nirag Patel**

*Project developed at the Department of Computer Science Engineering, University at Buffalo*.
