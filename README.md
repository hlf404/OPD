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

```bash
bash on_policy_distillation.sh
```

## 注意事项

- 环境安装可能会出现部分安装包版本错误或安装失败
- 运行需要登录swanlab
