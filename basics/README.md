# Reinforcement Learning (RL) — Semester Notes

## 1. What is Reinforcement Learning?

Reinforcement Learning is a learning paradigm where an agent interacts with an environment to maximize cumulative reward.

Unlike supervised learning:
- No labeled data
- Learning happens via trial and error

---

## 2. Basic Components

Agent → learner  
Environment → world  
State (S) → current situation  
Action (A) → decision taken  
Reward (R) → feedback signal  
Policy (π) → strategy  
Value Function → future reward expectation  

---

## 3. RL Interaction Loop

1. Observe state St  
2. Take action At  
3. Receive reward Rt  
4. Move to next state St+1  
5. Update policy  

---

## 4. Return (Cumulative Reward)

G(t) = Rt + γRt+1 + γ²Rt+2 + ...

Where:
γ = discount factor (0 to 1)

Meaning:
- γ close to 1 → future important  
- γ close to 0 → immediate reward important  

---

## 5. Value Function

State Value:

V(s) = Expected[ Rt + γ V(s') ]

Meaning:
How good is this state?

---

## 6. Q Function

Q(s,a) = Expected[ Rt + γ max Q(s',a') ]

Meaning:
How good is this action in this state?

This is core idea of Q Learning.

---

## 7. Bellman Equation Concept

Future value = immediate reward + discounted future value

This recursive structure makes RL work.

---

## 8. Exploration vs Exploitation

Exploration → try new actions  
Exploitation → use best known action  

Common strategy:
epsilon-greedy

---

## 9. Monte Carlo vs TD

Monte Carlo:
- Learn after episode ends
- High variance

Temporal Difference:
- Learn step by step
- Faster

Examples:
- TD(0)
- SARSA
- Q Learning

---

## 10. Policy Gradient Idea

Instead of learning value:

We optimize policy parameters:

grad J(theta)

Meaning:
Increase probability of good actions.

---

## 11. PPO (Important Modern RL)

Why PPO:

- Stable training
- Used in LLM RLHF
- Prevents large policy updates

Core idea:
Clipped objective function

---

## 12. RL vs Supervised vs Unsupervised

Supervised → labeled data  
Unsupervised → pattern finding  
RL → decision making

---

## 13. Applications

- Robotics  
- Games  
- Self driving  
- Finance  
- LLM alignment  

---

## 14. Modern RL in LLMs

Used in:

RLHF → human reward  
RLAIF → AI reward  
PPO → policy optimization  

---

## 15. Summary

Agent learns by interaction  
Goal → maximize long term reward  
Core tools → Bellman, Q Learning, Policy Gradient, PPO
