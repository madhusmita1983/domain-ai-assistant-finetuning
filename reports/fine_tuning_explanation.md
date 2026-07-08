# Fine-Tuning Concepts

## 1. Why Full Fine-Tuning is Expensive

Full fine-tuning updates **every parameter** of the pre-trained Large Language Model (LLM). Modern LLMs contain billions of parameters, making the process computationally intensive.

### Reasons:
- Requires storing gradients for all model parameters.
- Consumes a large amount of GPU memory (VRAM).
- Requires longer training time.
- Produces a full copy of the model after training, increasing storage requirements.
- Higher infrastructure and cloud computing costs.

**Example:**
Fine-tuning a 7B parameter model may require multiple high-memory GPUs (e.g., NVIDIA A100 80GB) when using standard full fine-tuning.

---

## 2. What LoRA Does

**LoRA (Low-Rank Adaptation)** is a Parameter-Efficient Fine-Tuning (PEFT) technique.

Instead of updating every weight in the model:

- The original model weights are **frozen**.
- Small trainable matrices (**A** and **B**) are inserted into selected layers.
- Only these adapter matrices are trained.

### Benefits

- Trains only a tiny percentage of parameters.
- Greatly reduces GPU memory usage.
- Faster training.
- Small adapter files (typically a few MBs instead of several GBs).

---

## 3. What QLoRA Does

**QLoRA (Quantized Low-Rank Adaptation)** combines:

- **4-bit model quantization**
- **LoRA adapters**

The base model is loaded in **4-bit precision**, while only the LoRA adapters are trained in higher precision.

### Benefits

- Extremely low memory usage.
- Similar performance to LoRA.
- Enables fine-tuning large models on consumer GPUs.

---

## 4. Why QLoRA is Useful on Limited GPU

QLoRA significantly reduces GPU memory requirements.

### Advantages

- Loads the base model in **4-bit precision**.
- Requires much less VRAM.
- Makes fine-tuning possible on GPUs with **12–24 GB VRAM**.
- Maintains performance close to full-precision training.

### Example

| Method | Approximate GPU Memory |
|---------|-----------------------:|
| Full Fine-Tuning | 60–80 GB+ |
| LoRA | 20–40 GB |
| QLoRA | 10–16 GB |

This makes QLoRA ideal for researchers, students, and developers with limited hardware.

---

## 5. What is Non-Instruction Fine-Tuning?

Non-instruction fine-tuning trains the model on **plain text** without explicit question-answer or instruction formatting.

### Example Dataset

```text
Windows Update fixes security vulnerabilities.

Restart your computer after installing updates.
```

The model learns language patterns and domain knowledge but not necessarily how to follow user instructions.

### Use Cases

- Domain adaptation
- Continued pretraining
- Language modeling
- Document understanding

---

## 6. What is Instruction Fine-Tuning?

Instruction fine-tuning teaches the model how to follow human instructions.

Training examples are formatted as **Instruction → Response** pairs.

### Example

```text
Instruction:
How do I reset my password?

Response:
Go to the password reset portal, verify your identity, and create a new password.
```

### Benefits

- Better conversational ability.
- Improved question answering.
- More helpful responses.
- Better alignment with user intent.

---

## 7. What is DPO?

**DPO (Direct Preference Optimization)** is an alignment technique that trains a model using **human preference data**.

Instead of learning from only the correct answer, DPO learns:

- Which answer is preferred.
- Which answer should be avoided.

Training data consists of:

- Prompt
- Preferred (Chosen) response
- Rejected response

The model learns to assign higher probability to preferred responses.

### Benefits

- Produces more helpful and natural responses.
- Avoids the complexity of Reinforcement Learning from Human Feedback (RLHF).
- Easier and more stable to train.

---

## 8. Difference Between SFT and DPO

| Feature | SFT (Supervised Fine-Tuning) | DPO (Direct Preference Optimization) |
|---------|-------------------------------|--------------------------------------|
| Training Data | Instruction–Response pairs | Prompt + Chosen + Rejected responses |
| Learning Objective | Learn the correct answer | Learn which answer humans prefer |
| Human Preferences | Not explicitly used | Directly incorporated |
| Training Complexity | Simple | Moderate |
| Typical Goal | Teach task completion | Improve response quality and alignment |
| Output Quality | Good | Generally more natural and better aligned |

---

## 9. Training Hyperparameters Used

The exact values depend on the experiment. A commonly used configuration for QLoRA fine-tuning is shown below.

| Hyperparameter | Typical Value |
|---------------|--------------:|
| **LoRA Rank (`r`)** | 16 |
| **LoRA Alpha (`α`)** | 32 |
| **LoRA Dropout** | 0.05 |
| **Learning Rate** | 2e-4 |
| **Batch Size** | 4 (or 8 with gradient accumulation) |

> **Note:** Replace these values with the actual hyperparameters used in your training run if they differ. These values are commonly recommended for QLoRA fine-tuning of 7B language models.

---

# Summary

| Concept | Key Takeaway |
|----------|--------------|
| Full Fine-Tuning | Updates all model parameters; expensive in memory and compute. |
| LoRA | Trains only small adapter matrices while freezing the base model. |
| QLoRA | Combines 4-bit quantization with LoRA for memory-efficient fine-tuning. |
| Why QLoRA | Enables fine-tuning of large models on limited-GPU hardware. |
| Non-Instruction Fine-Tuning | Learns from plain text without instruction-response formatting. |
| Instruction Fine-Tuning | Learns to follow user instructions using prompt-response examples. |
| DPO | Optimizes the model using human preference comparisons. |
| SFT vs DPO | SFT learns correct answers; DPO learns preferred answers. |
| Typical Hyperparameters | Rank = 16, Alpha = 32, Dropout = 0.05, Learning Rate = 2e-4, Batch Size = 4–8. |