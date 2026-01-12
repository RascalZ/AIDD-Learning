# AIDD 学习日志


## Day 1: 2026-01-12  环境搭建与起步、分子表示与图神经网络实战


###  今日成果
-  **Git 环境配置**: 建立 GitHub 仓库 `AIDD-Learning`。
-  **源码拉取**: 获取了 [BindCraft](https://github.com/martinpacesa/BindCraft) 的官方源码。
-  **Python 环境**: 
    - 安装 Miniconda。
    - 配置清华镜像源（Conda + Pip）。
    - 创建 `aidd` 虚拟环境 (Python 3.10)。
-  **依赖安装**: 安装了 RDKit, PyTorch, Jupyter 等核心库。


###  环境验证
在 Anaconda Prompt 中测试通过：

```python
import rdkit
from rdkit import Chem  
import torch
print("Environment is ready!")
```

### 理论突破

**分子表示 (Molecular Representations)**

1. Morgan Fingerprint (ECFP): 理解了基于半径（Radius）的哈希算法。它像“碎纸机”一样把分子切成子结构片段，映射到 0/1 向量。

    局限性: 丢失了拓扑结构（Topology），无法区分位置异构体，导致“结构袋子”问题；丢失长程链接；哈希碰撞

2. 图神经网络 (GNN)

    核心逻辑: 分子是图（Graph），原子是节点（Node），化学键是边（Edge）。

    消息传递 (Message Passing):  GCN 让原子“听取”邻居的信息来更新自己的特征。

    数据结构: 掌握了 PyG 的 edge_index (COO格式 [2, E]) 和 x (节点特征 [N, F])。

    维度变换:  [原子数, 1] -> GCN投影 -> [原子数, 64] -> Pooling -> [1, 64] -> Linear -> [1, 1] 

### ProteinMPNN 原理

逆向折叠 (Inverse Folding):  ProteinMPNN 是“固定骨架，猜氨基酸”。

1. 通过 PDB 数据集学习几何约束（空间位阻、亲疏水性）来预测序列。2021.8.2之前的X-ray和Cryo-EM、分辨率>3.5埃的高质量结构。

2. Attention 机制

### 代码实战
在 Jupyter Notebook 中完成了以下里程碑：

#### 01_Drug_Intro.ipynb:

- 使用 RDKit 生成分子的 Morgan 指纹。

- 解析了 Hash 碰撞与 Bit Vector 的映射关系。

- 手动构建 PyG 的 Data 对象（将 SMILES 转为 Graph）。

- 搭建了第一个 GCN 模型架构。

- 训练循环: 编写了完整的 Forward -> Loss -> Backward -> Optimizer 循环。

- 可视化: 成功画出了 Loss 下降曲线，见证模型从“随机猜测”到“精准预测”的过程。

- 验证: 成功预测阿司匹林的 LogP 值（误差 < 0.5）。



### 常用命令
```python
git add 文件名

git commit -m "备注"

git push

#增大 Git 的传输缓冲区
git config --global http.postBuffer 524288000

#手动告诉 Git 走代理
git config --global http.proxy http://127.0.0.1:7890
git config --global https.proxy http://127.0.0.1:7890
```

