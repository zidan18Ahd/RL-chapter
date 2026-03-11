# Policy Gradient Methods in Reinforcement Learning

## 1. Introduction

Policy Gradient methods directly optimize the policy instead of deriving it from value functions.

Goal: maximize expected cumulative reward.

---

## 2. Policy Representation

Policy:

πθ(a | s)

Meaning:

- s = state  
- a = action  
- θ = policy parameters  

Policy gives probability of taking action a in state s.

---

## 3. Trajectory

Trajectory:

τ = (s1, a1, r2, s2, a2, ..., sT)

Sequence of states, actions, rewards.

---

## 4. Return

Gt = Σ (k=t → T) γ^(k−t) rk

Where:

- γ = discount factor  
- rk = reward at step k  

Return = total future reward from time t.

---

## 5. Objective Function

J(θ) = Eτ~πθ [ G ]

Goal: maximize expected return.

---

## 6. Policy Gradient Theorem

∇θ J(θ) = E [ Gt ∇θ log πθ(at | st) ]

Meaning:

- ∇θ J(θ) → direction to change weights  
- Gt → reward signal  
- log πθ → probability of chosen action  

High reward → increase probability.

---

## 7. REINFORCE Algorithm

Update rule:

θ = θ + α Gt ∇θ log πθ(at | st)

Where:

- α = learning rate  
- Gt = return  

This increases probability of high-reward actions.

---

## 8. Monte Carlo Nature

REINFORCE is Monte Carlo because:

- Uses full trajectory  
- No bootstrapping  
- Update after episode ends  

---

## 9. Variance Issue

Policy gradient has high variance because:

- Returns vary across trajectories  
- Gradient becomes noisy  

This slows learning.

---

## 10. Baseline for Variance Reduction

Gradient with baseline:

∇J = (Gt − b(st)) ∇ log πθ(at | st)

Common baseline:

b(st) = V(st)

Effect:

- Reduces variance  
- Keeps estimator unbiased  

---

## 11. Advantage Interpretation

A(st, at) = Gt − V(st)

Meaning:

How much better action was than expected.

---

## 12. Training Flow

1. Sample trajectory  
2. Compute return  
3. Compute log probability  
4. Multiply with return  
5. Update parameters  
6. Repeat  
