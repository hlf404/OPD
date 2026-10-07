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
