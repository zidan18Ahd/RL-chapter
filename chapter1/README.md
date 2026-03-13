# 📘 Reinforcement Learning — Chapter 1 (Introduction)

## 🔴 What is Reinforcement Learning?

Reinforcement Learning (RL) is a machine learning paradigm where an **agent learns optimal behavior by interacting with an environment to maximize cumulative reward.**

Unlike supervised learning:

* No labeled dataset
* Learning via trial and error
* Sequential decision making

---

## 🔴 RL Interaction Framework

At time step `t`:

* Agent observes state `s_t`
* Takes action `a_t`
* Receives reward `r_t`
* Moves to next state `s_{t+1}`

Interaction loop:

```
s_t → a_t → r_t → s_{t+1}
```

---

## 🔴 Objective of RL

Return:

```
G_t = r_t + γ r_{t+1} + γ² r_{t+2} + ...
```

Where:

* `G_t` = Total future reward
* `γ` = Discount factor

---

## 🔴 Discount Factor

```
0 ≤ γ ≤ 1
```

* γ = 0 → Only immediate reward matters
* γ → 1 → Future rewards matter

---

## 🔴 Core Components

**Agent** → Decision maker
**Environment** → External system
**State (s)** → Current situation
**Action (a)** → Decision taken
**Reward (r)** → Feedback signal

---

## 🔴 Policy

```
π(a | s) = Probability of taking action a in state s
```

Types:

* Deterministic
* Stochastic

---

## 🔴 Value Function

```
V^π(s) = Expected return starting from state s
```

Meaning: How good it is to be in state `s`.

---

## 🔴 Action Value Function (Q Function)

```
Q^π(s, a) = Expected return if action a is taken in state s
```

Meaning: How good action `a` is in state `s`.

---

## 🔴 Exploration vs Exploitation

**Exploration** → Try new actions
**Exploitation** → Use best known action

Balanced strategy is important.

---

## 🔴 Markov Property

```
P(s_{t+1} | s_t, history) = P(s_{t+1} | s_t)
```

Meaning: Future depends only on present state.

---

## 🔴 Markov Decision Process (MDP)

```
(S, A, P, R, γ)
```

Where:

* S → State space
* A → Action space
* P → Transition probability
* R → Reward function
* γ → Discount factor

---

## 🔴 Types of RL Tasks

**Episodic Tasks**

* Have terminal state
* Example: Games, Maze

**Continuing Tasks**

* No terminal state
* Example: Trading, Robot control

---

## 🔴 Example (Exam Important)

Robot navigation:

* State → Robot position
* Action → Move direction
* Reward → +10 goal, −1 wall

Goal: Learn shortest path.

---

## 🔴 RL vs Other Machine Learning

| Learning Type | Data          | Goal              |
| ------------- | ------------- | ----------------- |
| Supervised    | Labeled       | Prediction        |
| Unsupervised  | No labels     | Pattern discovery |
| Reinforcement | Reward signal | Maximize return   |

---

## 🔴 Key Characteristics

* Sequential decision making
* Delayed reward
* Trial-and-error learning
* Goal-oriented learning
* Environment interaction

---

## 🔴 Important Exam Questions

### ⭐ 2 Marks

* Define reinforcement learning
* What is policy?
* Define reward
* Define return
* What is discount factor?
* Define value function
* Define MDP

### ⭐ 5 Marks

* Explain RL interaction loop
* Exploration vs exploitation
* Episodic vs continuing tasks
* RL vs supervised learning

### ⭐ 10 Marks

* Explain Markov Decision Process
* Derive return equation
* Explain value function and Q-function

---

## 🔴 Applications

* Robotics
* Game AI
* Recommendation systems
* Autonomous driving
* LLM optimization

---
