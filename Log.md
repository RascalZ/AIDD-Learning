# AIDD 学习日志


## Day 1: 2026-01-12 环境搭建与起步

###  今日成果
-  **Git 环境配置**: 成功解决连接重置问题，建立 GitHub 仓库 `AIDD-Learning`。
-  **源码拉取**: 获取了 [BindCraft](https://github.com/martinpacesa/BindCraft) 的官方源码作为参考。
-  **Python 环境**: 
    - 安装 Miniconda。
    - 配置清华镜像源（Conda + Pip）。
    - 创建 `aidd` 虚拟环境 (Python 3.10)。
-  **依赖安装**: 安装了 RDKit, PyTorch, Jupyter 等核心库。


###  环境验证
在 Anaconda Prompt 中测试通过：

```python
import rdkit
from rdkit import Chem  # <--- 建议加上这一句
import torch
print("Environment is ready!")