---
name: deep-learning
description: Reference guide for neural network architectures, training, debugging, and model selection. Use when building ML models, choosing architectures, debugging training issues, or understanding deep learning concepts.
---

# Deep Learning Reference

## When to Use

- Choosing between CNN, RNN, Transformer, or other architectures
- Debugging training issues (loss not decreasing, NaN, overfitting)
- Understanding attention, backprop, normalization, or other concepts
- Tuning hyperparameters, regularization, or learning rate schedules
- Selecting loss functions, optimizers, or activation functions

## Architecture Selection

| Data Type | Recommended Architecture |
|-----------|-------------------------|
| Tabular | Gradient boosting, then MLP |
| Images | CNN (ResNet, EfficientNet) or ViT |
| Text | Transformer (BERT, GPT) |
| Sequences | Transformer or LSTM |
| Graphs | GNN (GCN, GAT) |
| Image generation | Diffusion models |
| Text generation | Autoregressive transformers |

## Core Building Blocks

### Activation Functions

| Function | Formula | Use Case |
|----------|---------|----------|
| ReLU | max(0, x) | Default for hidden layers |
| Sigmoid | 1/(1+e⁻ˣ) | Binary output, gates |
| Tanh | (eˣ-e⁻ˣ)/(eˣ+e⁻ˣ) | Centered output [-1,1] |
| Softmax | eˣⁱ/Σeˣʲ | Multi-class probabilities |
| GELU | x·Φ(x) | Transformers |
| SiLU/Swish | x·σ(x) | Modern architectures |

### Loss Functions

| Task | Loss | Formula |
|------|------|---------|
| Regression | MSE | L = (1/n)Σ(y - ŷ)² |
| Binary classification | Binary cross-entropy | L = -Σ[y·log(ŷ) + (1-y)·log(1-ŷ)] |
| Multi-class | Cross-entropy | L = -Σ y·log(ŷ) |

### Optimizers

| Optimizer | Key Idea | When to Use |
|-----------|----------|-------------|
| SGD + Momentum | Accumulate velocity | Still competitive, good generalization |
| Adam | Adaptive LR + momentum | Default choice |
| AdamW | Adam with decoupled weight decay | Large models, transformers |

## Transformers

The dominant architecture for sequences and increasingly everything else.

### Self-Attention

```
Attention(Q, K, V) = softmax(QK^T / √d_k) · V
```

- **Q (Query)**: What am I looking for?
- **K (Key)**: What do I contain?
- **V (Value)**: What do I provide?

### Multi-Head Attention

Multiple attention heads in parallel, each attending to different relationship types.

### Transformer Block

```
x → LayerNorm → Multi-Head Attention → + → LayerNorm → FFN → + → output
│                                      │ │                    │
└──────────────────────────────────────┘ └────────────────────┘
                (residual)                     (residual)
```

### Positional Encoding

- **Sinusoidal**: Fixed pattern of sines/cosines
- **Learned**: Trainable embedding per position
- **Rotary (RoPE)**: Encode relative positions through rotation

### Variants

- **Encoder** (bidirectional): BERT-style, sees all positions
- **Decoder** (causal): GPT-style, sees only previous positions
- **Encoder-Decoder**: T5-style, input→output

## CNNs

For grid-structured data (images, spectrograms).

```
INPUT → [Conv + ReLU + Pool] × N → Flatten → [Dense] × M → OUTPUT
        (feature extraction)                  (classification)
```

**Key innovation — Residual connections (ResNet):**
```
x ──────────────────┐
│                    │
└→ [Conv] → [Conv] ─┴→ x + F(x)
```

Gradients flow directly through skip connections, enabling 100+ layer networks.

## RNNs

For sequential data when transformers are too heavy.

- **LSTM**: Gated architecture with forget/input/output gates and cell state highway
- **GRU**: Simplified LSTM, two gates, fewer parameters, similar performance
- **Limitation**: Sequential processing (can't parallelize like transformers)

## Generative Models

| Model | Mechanism | State of Art For |
|-------|-----------|-----------------|
| VAE | Encode to distribution, sample, decode | Structured generation |
| GAN | Generator vs discriminator adversarial game | Was images, mostly replaced |
| Diffusion | Learn to reverse noise-adding process | Image generation (DALL-E, SD) |
| Autoregressive | Predict next token | Text generation (GPT) |

## Regularization Toolkit

| Technique | What It Does | When to Use |
|-----------|-------------|-------------|
| Weight decay (L2) | Penalizes large weights | Default, always |
| Dropout | Randomly zeros neurons (p=0.1-0.5) | Dense layers |
| Data augmentation | Creates training variations | Limited data |
| Early stopping | Stop when val loss plateaus | Always monitor |
| Batch normalization | Normalizes within mini-batch | CNNs |
| Layer normalization | Normalizes across features | Transformers, RNNs |

## Training Debugging

| Symptom | Likely Cause | Fix |
|---------|-------------|-----|
| Loss not decreasing | LR too low/high, bug | Check gradients, try different LR |
| Loss NaN/Inf | LR too high, numerical | Lower LR, gradient clipping |
| Overfitting | Model too big, data too small | Regularization, more data |
| Underfitting | Model too small, LR too low | Bigger model, higher LR |
| Slow convergence | LR too low | Increase LR, use scheduler |

### Hyperparameter Priority

1. **Learning rate** (most important)
2. **Batch size**
3. **Architecture (depth, width)**
4. **Regularization (dropout, weight decay)**
5. **Optimizer settings**

### Training Recipe

1. **Start simple**: Small model, verify it can overfit a small batch
2. **Scale up**: Gradually increase model size and data
3. **Tune LR**: Find highest stable learning rate
4. **Add regularization**: Only when overfitting
5. **Extend training**: More epochs if still improving

## Learning Rate Schedules

- **Warmup**: Start low, increase gradually (stability)
- **Cosine decay**: Smooth decrease following cosine curve
- **Step decay**: Drop by factor every N epochs
- **Cyclical**: Oscillate between bounds (escape local minima)

## Key Equations

| Concept | Equation |
|---------|----------|
| Linear layer | y = Wx + b |
| ReLU | f(x) = max(0, x) |
| Softmax | p_i = e^{x_i} / Σe^{x_j} |
| Cross-entropy | L = -Σ y_i log(ŷ_i) |
| SGD update | θ ← θ - η∇L |
| Attention | softmax(QK^T/√d)V |
| BatchNorm | (x - μ)/σ · γ + β |
