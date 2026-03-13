# 📘 Reinforcement Learning — Chapter 1 (Introduction)

## 🔴 What is Reinforcement Learning?

**Reinforcement Learning (RL)** is a machine learning paradigm where an **agent learns optimal behavior by interacting with an environment to maximize cumulative reward.**

Unlike supervised learning:

* No labeled dataset
* Learning via trial and error
* Sequential decision making

---

## 🔴 RL Interaction Framework

At time step ( t ):

* Agent observes state ( s_t )
* Takes action ( a_t )
* Receives reward ( r_t )
* Moves to next state ( s_{t+1} )

This forms the loop:

[
s_t \rightarrow a_t \rightarrow r_t \rightarrow s_{t+1}
]

---

## 🔴 Objective of RL

The goal is to maximize **expected cumulative reward (Return):**

[
G_t = r_t + \gamma r_{t+1} + \gamma^2 r_{t+2} + \dots
]

Where:

* ( G_t ) → Return
* ( \gamma ) → Discount factor

---

## 🔴 Discount Factor

[
0 \le \gamma \le 1
]

* ( \gamma = 0 ) → Only immediate reward matters
* ( \gamma \approx 1 ) → Future rewards matter

---

## 🔴 Core Terminology

### 🟢 Agent

Decision maker (robot, AI model, player)

### 🟢 Environment

External system with which agent interacts

### 🟢 State ( s )

Current situation of the agent

### 🟢 Action ( a )

Decision taken by agent

### 🟢 Reward ( r )

Feedback signal from environment

---

## 🔴 Policy

Policy defines agent behaviour:

[
\pi(a|s) = P(a_t = a \mid s_t = s)
]

Types:

* Deterministic policy
* Stochastic policy

---

## 🔴 Value Function

Expected future reward from state ( s ):

[
V^\pi(s) = \mathbb{E}[G_t \mid s_t = s]
]

---

## 🔴 Action-Value Function (Q Function)

[
Q^\pi(s,a) = \mathbb{E}[G_t \mid s_t = s, a_t = a]
]

Meaning:

Expected reward if we take action ( a ) in state ( s )

---

## 🔴 Exploration vs Exploitation

### Exploration

Trying new actions to gain knowledge

### Exploitation

Using known best action

Balanced strategy is essential.

---

## 🔴 Markov Property

RL assumes:

[
P(s_{t+1} \mid s_t, s_{t-1}, \dots) = P(s_{t+1} \mid s_t)
]

Meaning:

Future depends only on present state.

---

## 🔴 Markov Decision Process (MDP)

RL problems are modeled as:

[
(S, A, P, R, \gamma)
]

Where:

* ( S ) → State space
* ( A ) → Action space
* ( P ) → Transition probability
* ( R ) → Reward function
* ( \gamma ) → Discount factor

---

## 🔴 Types of RL Tasks

### Episodic Tasks

Have terminal state
Examples: games, maze solving

### Continuing Tasks

No terminal state
Examples: stock trading, robot control

---

## 🔴 Example (Exam Important)

Robot navigation:

* State → Robot position
* Action → Move direction
* Reward → +10 (goal), −1 (wall)

Objective:

Learn shortest path.

---

## 🔴 RL vs Other Machine Learning

| Learning Type | Data          | Goal            |
| ------------- | ------------- | --------------- |
| Supervised    | Labeled       | Predict output  |
| Unsupervised  | No labels     | Find structure  |
| Reinforcement | Reward signal | Maximize return |

---

## 🔴 Key Characteristics

* Sequential decision making
* Delayed reward
* Trial-and-error learning
* Goal-oriented
* Environment interaction

---

## 🔴 Important Exam Questions

### ⭐ 2 Mark

* Define reinforcement learning
* What is policy?
* Define reward
* Define return
* What is discount factor
* Define value function
* Define MDP

### ⭐ 5 Mark

* Explain RL interaction loop
* Exploration vs exploitation
* Episodic vs continuing tasks
* RL vs supervised learning

### ⭐ 10 Mark

* Explain Markov Decision Process
* Derive return equation
* Explain value function and Q-function

---

## 🔴 Applications

* Robotics
* Game AI
* Recommendation systems
* Autonomous driving
* LLM reasoning optimization

---
