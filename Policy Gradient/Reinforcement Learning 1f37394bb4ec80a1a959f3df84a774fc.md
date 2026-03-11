# Reinforcement Learning:

## 🔴 Definition

**REINFORCE is a Monte-Carlo policy gradient algorithm that updates policy parameters using sampled trajectory rewards.**

Meaning:

👉 Learn by generating full sequence → compute reward → update probability.

---

# 🧠 Core Concepts

### 1️⃣ Policy

πθ(a∣s)\pi_\theta(a|s)

πθ(a∣s)

Meaning:

Probability of action **a** in state **s**.

LLM:

- s = prompt + previous tokens
- a = next token

So:

👉 policy = transformer.

---

### 2️⃣ Parameters

θ\theta

θ

Meaning:

Neural network weights.

Training = updating θ.

---

### 3️⃣ Trajectory

τ=(S1,A1,R2,S2,A2,...,ST)\tau = (S_1, A_1, R_2, S_2, A_2, ..., S_T)

τ=(S1,A1,R2,S2,A2,...,ST)

Meaning:

Sequence of:

state → action → reward.

LLM:

Prompt → reasoning → final answer.

---

### 4️⃣ Return

Gt=∑k=tTγk−tRkG_t = \sum_{k=t}^{T} \gamma^{k-t} R_k

Gt=k=t∑Tγk−tRk

Meaning:

Total future reward.

LLM:

Usually:

Gt=final rewardG_t = final\ reward

Gt=final reward

Because reward given at end.

---

### 5️⃣ Objective Function

J(θ)=Eτ∼πθ[G]J(\theta) = \mathbb{E}_{\tau \sim \pi_\theta}[G]

J(θ)=Eτ∼πθ[G]

Meaning:

Maximize expected reward.

LLM:

Make model solve more tasks correctly.

---

# ⭐ MOST IMPORTANT EQUATION (Policy Gradient)

∇θJ(θ)=E[Gt∇θlog⁡πθ(at∣st)]\nabla_\theta J(\theta) =
\mathbb{E}[G_t \nabla_\theta \log \pi_\theta(a_t|s_t)]

∇θJ(θ)=E[Gt∇θlogπθ(at∣st)]

### Meaning line-by-line

- ∇θJ(θ)\nabla_\theta J(\theta)∇θJ(θ) → how to change weights
- GtG_tGt → reward signal
- log⁡πθ\log \pi_\thetalogπθ → probability of chosen action

Interpretation:

👉 Increase probability of high-reward actions.

---

# ⭐ REINFORCE Update Rule

θ=θ+αGt∇θlog⁡πθ(at∣st)\theta = \theta + \alpha G_t \nabla_\theta \log \pi_\theta(a_t|s_t)

θ=θ+αGt∇θlogπθ(at∣st)

### Meaning

- α = learning rate
- reward scales gradient
- update pushes policy toward good actions

---

# 🧠 Example (LLM)

Prompt:

```
2 + 2 =
```

Model outputs:

```
5
```

Reward:

G=0G = 0

G=0

Update:

Δθ=0\Delta \theta = 0

Δθ=0

Next sample:

```
4
```

Reward:

G=1G = 1

G=1

Update:

👉 increase probability of tokens used in reasoning.

---

# ⭐ Baseline (Variance Reduction)

∇J=(Gt−b)∇log⁡π\nabla J =
(G_t - b) \nabla \log \pi

∇J=(Gt−b)∇logπ

Meaning:

Compare reward to average reward.

If:

- better than average → increase
- worse → decrease

This leads to:

👉 Advantage function.

---

# ⭐ Advantage Function

A(s,a)=Q(s,a)−V(s)A(s,a) = Q(s,a) - V(s)

A(s,a)=Q(s,a)−V(s)

Meaning:

How much better action is than expected.

LLM:

If reasoning unusually good → reinforce.

---

# 🔄 REINFORCE FLOWCHART (LLM Example)

```
Prompt (state)
     ↓
Model generates reasoning (trajectory)
     ↓
Final answer
     ↓
Reward model gives score
     ↓
Compute log probability of trajectory
     ↓
Multiply with reward
     ↓
Backpropagation
     ↓
Update θ (model weights)
     ↓
Improved policy
```

---

# 🧠 Why Monte Carlo?

Because:

- Uses full trajectory reward
- No step-wise prediction
- Pure sampling

# 

## 🔴 Why GAE Exists (Motivation)

In Reinforcement Learning, especially for **LLM reasoning training**, reward is often:

- Sparse (only at final step)
- Noisy
- Hard to assign to individual steps

Example:

```
Step1 → Step2 → Step3 → Final Answer → Reward
```

Problem:

We don’t know which step contributed most.

This is called:

⭐ **Credit Assignment Problem**

GAE solves this.

---

## 🔴 Core Idea of GAE

GAE provides:

> A smoother and more informative signal about how good an action was compared to expectation.
> 

Instead of using:

- Only final reward (REINFORCE)
- Only one-step estimate (TD)

GAE uses:

⭐ **Weighted combination of multiple future signals**

---

## 🔴 Advantage Function

### Definition

A(s,a)=Q(s,a)−V(s)A(s,a) = Q(s,a) - V(s)

A(s,a)=Q(s,a)−V(s)

### Meaning

- Q(s,a)Q(s,a)Q(s,a): Actual return from taking action
- V(s)V(s)V(s): Expected return in that state

So:

👉 Advantage = How much better action was than expected.

---

## 🔴 TD Error (Building Block of GAE)

δt=rt+γV(st+1)−V(st)\delta_t = r_t + \gamma V(s_{t+1}) - V(s_t)

δt=rt+γV(st+1)−V(st)

### Meaning

- rtr_trt: immediate reward
- γ\gammaγ: discount factor
- V(s)V(s)V(s): value prediction

TD error = **surprise signal**

---

## 🔴 GAE Formula

AtGAE=δt+(γλ)δt+1+(γλ)2δt+2+...A_t^{GAE} =
\delta_t + (\gamma \lambda)\delta_{t+1}
+ (\gamma \lambda)^2 \delta_{t+2} + ...

AtGAE=δt+(γλ)δt+1+(γλ)2δt+2+...

### Meaning

Advantage is:

👉 Weighted sum of future TD errors.

---

## 🔴 Role of λ (Lambda)

λ controls:

- Bias vs Variance tradeoff

| λ value | Effect |
| --- | --- |
| λ = 0 | Low variance, high bias |
| λ = 1 | High variance, low bias |
| 0.9–0.97 | Practical sweet spot |

---

## 🔴 Numeric Example (LLM Reasoning)

Trajectory:

```
Step1 → Step2 → Step3 → Final Answer
```

Given:

```
Reward only at final step = 1
γ = 0.9
λ = 0.8
```

Value estimates:

```
V(s1) = 0.5
V(s2) = 0.6
V(s3) = 0.7
```

Rewards:

```
r1 = 0
r2 = 0
r3 = 1
```

---

### Step 1: TD Errors

δ1=0+0.9×0.6−0.5=0.04\delta_1 = 0 + 0.9 × 0.6 − 0.5 = 0.04

δ1=0+0.9×0.6−0.5=0.04

δ2=0+0.9×0.7−0.6=0.03\delta_2 = 0 + 0.9 × 0.7 − 0.6 = 0.03

δ2=0+0.9×0.7−0.6=0.03

δ3=1−0.7=0.3\delta_3 = 1 − 0.7 = 0.3

δ3=1−0.7=0.3

---

### Step 2: Compute GAE

γλ=0.72\gamma \lambda = 0.72

γλ=0.72

A1=0.04+0.72×0.03+0.722×0.3A_1 = 0.04 + 0.72 × 0.03 + 0.72^2 × 0.3

A1=0.04+0.72×0.03+0.722×0.3

A1≈0.217A_1 ≈ 0.217

A1≈0.217

A2=0.03+0.72×0.3=0.246A_2 = 0.03 + 0.72 × 0.3 = 0.246

A2=0.03+0.72×0.3=0.246

A3=0.3A_3 = 0.3

A3=0.3

---

## 🔴 Interpretation

GAE distributes credit:

| Step | Advantage |
| --- | --- |
| Step1 | 0.217 |
| Step2 | 0.246 |
| Step3 | 0.300 |

Later steps get more credit, but earlier steps also get some.

---

## 🔴 Compare with REINFORCE

REINFORCE would assign:

```
All steps = reward = 1
```

GAE assigns:

👉 Smooth credit distribution.

---

## 🔴 Why GAE Important for PPO & GRPO

Modern RL methods require:

- Stable gradients
- Low variance updates
- Better credit assignment

GAE enables:

⭐ PPO

⭐ RLHF

⭐ GRPO

⭐ Reasoning training

Without GAE:

Training unstable.

---

## 🔴 Key Intuition (Exam Ready)

GAE =

> Smarter way to distribute future reward signal across steps.
> 

---

## 🔴 Concept Flow

```
Trajectory → Reward
          ↓
Value prediction
          ↓
TD error
          ↓
GAE smoothing
          ↓
Advantage
          ↓
Policy Gradient Update
```

[](Reinforcement%20Learning/Untitled%203207394bb4ec80ba85a3f80bbc0911ba.md)

[BRIDGE](Reinforcement%20Learning/BRIDGE%203207394bb4ec8036b8f7c8d685a61cf8.md)

[](Reinforcement%20Learning/Untitled%203207394bb4ec8004b3b1ede8a42e4d3f.md)