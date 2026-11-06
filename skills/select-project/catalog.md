# Project catalog

Each project is one 12-week cycle: reproduce a recent paper, extend it, submit to a workshop. Mentors add projects from their own field. Compute numbers are for the reproduction scope listed, not the paper's full experiments.

---

## P1. Back to Basics: Let Denoising Generative Models Denoise (JiT)

- **Paper:** Li and He, CVPR 2026. https://arxiv.org/abs/2511.13720
- **Mentor:** Lyne Tchapmi (diffusion models, video generation, 3D vision)
- **Idea in one line:** diffusion models should predict the clean image, not the noise; noise prediction fails when the data is high-dimensional and the network is narrow.
- **Reproduction scope:** Section 3.3 toy experiment (2D data embedded in up to 512 dimensions, 5-layer MLP, 256 units).
- **Runs on:** any recent laptop. CPU only, 4 GB RAM, minutes per run.
- **Prerequisites:** Python, PyTorch basics, what a diffusion model is at a high level.
- **Difficulty:** Beginner-friendly.
- **Extension directions:** curved (nonlinear) data manifolds; width versus dimension phase diagram.

## P2. Mean Flows for One-step Generative Modeling (MeanFlow)

- **Paper:** Geng, Deng, Bai, Kolter, He, NeurIPS 2025.
- **Mentor:** Lyne Tchapmi
- **Idea in one line:** learn the average velocity over an interval instead of the instantaneous velocity, so samples can be generated in one step without distillation.
- **Reproduction scope:** 2D toy distributions, MeanFlow versus flow matching at 1, 2 and 10 sampling steps.
- **Runs on:** any recent laptop. CPU only, about 10 minutes per full run on a 2-core CPU (measured).
- **Prerequisites:** PyTorch, flow matching or diffusion basics, comfort with derivatives (uses a Jacobian-vector product).
- **Difficulty:** Intermediate.
- **Extension directions:** one-step versus multi-step trade-off as a function of the training mix.

## P3. Less is More: Recursive Reasoning with Tiny Networks (TRM)

- **Paper:** Jolicoeur-Martineau, 2025. https://arxiv.org/abs/2510.04871
- **Mentor:** [mentor name]
- **Idea in one line:** a 7M-parameter network that refines its answer recursively solves hard puzzles like Sudoku-Extreme.
- **Reproduction scope:** Sudoku-Extreme training and evaluation.
- **Runs on:** one NVIDIA data-center GPU. The paper trained Sudoku on an L40S-class GPU.
- **Prerequisites:** PyTorch, transformers, training loops on GPU.
- **Difficulty:** Intermediate.

## P4. RL with verifiable rewards: TinyZero (R1-Zero style)

- **Paper / code:** TinyZero, Berkeley, 2025. https://github.com/Jiayi-Pan/TinyZero
- **Mentor:** [mentor name]
- **Idea in one line:** reinforcement learning with a checkable reward (the Countdown game) teaches a small base language model to verify and search on its own.
- **Reproduction scope:** Countdown task with Qwen2.5 base models.
- **Runs on:** NVIDIA GPUs. One GPU works for models up to 1.5B; 3B needs two GPUs. The 0.5B model is reported not to learn reasoning.
- **Prerequisites:** PyTorch, LLM fine-tuning, comfort with distributed training tools.
- **Difficulty:** Advanced.
