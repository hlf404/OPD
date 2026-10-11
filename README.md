## 模型

### 学生模型
Qwen3-0.6B-Base

Qwen3-1.7B-Base

Qwen3-4B-Base

### 教师模型

Qwen3-8B

### 环境安装

```bash
conda create -n verl python==3.12
conda activate verl
cd verl/
USE_MEGATRON=0 bash scripts/install_vllm_sglang_mcore.sh
pip install math-verify
```

### OPD训练

RKL（传统OPD）训练

```bash
bash on_policy_distillation_rkl.sh
```

RKL+FKL训练需要将脚本on_policy_distillation_rkl.sh中的export USE_KL=${USE_KL:-False}改为True

```bash
bash on_policy_distillation_rkl.sh
```

Top_k token的OPD训练需要将脚本on_policy_distillation_rkl.sh中的export REVERSE_KL_TOP_K=${REVERSE_KL_TOP_K:-0}改为1，8，16，32，64中的一个

```bash
bash on_policy_distillation_rkl.sh
```

### EOPD训练设置复现

RKL（传统OPD）训练

```bash
bash on_policy_distillation_opd.sh
```

RKL+FKL训练需要将脚本on_policy_distillation_opd.sh中的export USE_KL=${USE_KL:-False}改为True

```bash
bash on_policy_distillation_opd.sh
```

FKL权重参数修改为1.0

```bash
bash on_policy_distillation_opd_1.0.sh
```

## 注意事项

- 环境安装可能会出现部分安装包版本错误或安装失败
- 运行需要登录swanlab

## 参考论文

### token OPD

[Entropy-Aware On-Policy Distillation of Language Models](https://arxiv.org/abs/2603.07079)

[Rethinking On-Policy Distillation of Large Language Models: Phenomenology, Mechanism, and Recipe](https://arxiv.org/abs/2604.13016)

[Decoupling KL and Trajectories: A Unified Perspective for SFT, DAgger, Offline RL, and OPD in LLM Distillation](https://arxiv.org/abs/2605.16826)

### embedding RL / OPD

[Guiding Cross-Modal Representations with MLLM Priors via Preference Alignment](https://proceedings.neurips.cc/paper_files/paper/2025/hash/61fe084a10444333b3da0c1f4434d51e-Abstract-Conference.html) ⭐

[Learning to Retrieve via Reinforcement Learning in Embedding Space](https://arxiv.org/abs/2610.07731) 

[Autoregressive Retriever: Improving Query Understanding from Item Feedback for Universal Multimodal Retrieval](https://arxiv.org/abs/2610.07731)

[Efficient Rationale-based Retrieval: On-policy Distillation from Generative Rerankers based on JEPA](https://arxiv.org/abs/2604.23336) ⭐

[OPRD: On-Policy Representation Distillation](https://arxiv.org/abs/2606.06021)
