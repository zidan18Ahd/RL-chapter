# Reinforcement Learning Foundations (Bridging Concepts)

This chapter builds the intuition required before studying core RL algorithms.

Think of this as:

Supervised Learning → Decision Making → Sequential Optimization → RL

---

## 1. Learning vs Decision Making

In traditional ML:

Model learns mapping:

input → output

Example:
Image → Label

But in real world:

We need:

state → action → future consequence

Example:
Robot → move → future position changes

This is decision making under uncertainty.

This motivates RL.

---

## 2. Sequential Nature of Problems

In supervised learning:
Each sample is independent.

In RL:
Current action affects future data distribution.

Example:

Game move now → affects all future moves.

This creates:

Temporal dependency

This is why RL is harder.

---

## 3. Delayed Reward Problem

In ML:
Loss is immediate.

In RL:
Reward may come much later.

Example:

Chess:
Good move now → win after 40 steps.

So agent must learn:

Which past action caused reward?

This is credit assignment problem.

---

## 4. Trial and Error Learning

RL agent does not know correct action initially.

It must:

Explore → observe reward → update belief

This mimics:

Human learning
Animal learning

This makes RL biologically inspired.

---

## 5. Optimization Objective Difference

Supervised Learning:

Minimize prediction error

RL:

Maximize cumulative reward

This changes:

Entire training paradigm.

---

## 6. Feedback Type Difference

Supervised → Correct label  
Unsupervised → No feedback  
RL → Scalar reward signal  

Reward is:

- Noisy
- Sparse
- Delayed

This makes learning unstable.

---

## 7. Environment Interaction Concept

In ML:
Dataset is fixed.

In RL:
Agent generates its own data.

This creates:

Distribution shift during training.

This is a major research challenge.

---

## 8. Policy Concept Intuition

Policy = behaviour rule

π(s) → action

This is equivalent to:

Brain decision function.

Learning policy = learning behaviour.

---

## 9. Value Concept Intuition

Value measures:

How good future will be.

Two types:

State value → goodness of situation  
Action value → goodness of decision  

This allows planning.

---

## 10. Planning vs Learning

Planning:
Environment model known

Learning:
Environment unknown

RL often mixes both.

Example:

Model based RL  
Model free RL

---

## 11. Why MDP is Needed

To mathematically formalize RL:

We need structure.

MDP provides:

- States
- Actions
- Transition probability
- Reward function

Without MDP → RL cannot be formalized.

---

## 12. Exploration Necessity

If agent only exploits:

It may get stuck in local optimum.

Exploration ensures:

Global optimal behaviour.

This creates:

Exploration-exploitation tradeoff.

---

## 13. Function Approximation Need

Real world state space is huge.

We cannot use tables.

So we use:

Neural Networks

This leads to:

Deep Reinforcement Learning.

---

## 14. RL Stability Difficulty

RL training unstable because:

- Bootstrapping
- Non stationary targets
- Correlated data
- Sparse reward

This motivates:

DQN tricks  
Replay buffer  
Target network  
PPO clipping  

---

## 15. Bridge to Advanced RL

After understanding this chapter:

Next concepts become natural:

→ MDP  
→ Bellman Equation  
→ Dynamic Programming  
→ TD Learning  
→ Policy Gradient  
→ Actor Critic  
→ PPO  

This chapter is the mental foundation.
