# AI Learning

这是一个用于长期记录人工智能与计算机视觉学习过程的个人仓库。

仓库主要服务于数据结构与算法、深度学习基础、PyTorch、计算机视觉论文阅读和项目复现等学习任务。目标不是简单堆积课程资料，而是通过持续记录、代码实践和实验复现，逐步形成较完整的 AI/CV 学习体系与项目能力。

## Repository Structure

```text
AI-learning/
├── notes/
├── papers/
├── projects/
└── README.md
```

### notes

用于存放基础知识与课程学习笔记，包括：

* 数据结构与算法
* Python
* D2L 深度学习基础
* PyTorch
* 计算机视觉基础
* 其他与 AI 工程相关的学习记录

部分笔记使用 Obsidian 编写，主要以 Markdown 格式保存。

### papers

用于存放计算机视觉论文相关内容，包括：

* 论文候选池
* 论文阅读笔记
* 模型结构梳理
* 复现计划
* 实验设计
* 消融实验记录
* 错误案例分析

### projects

用于存放具体的项目代码与复现实验，包括：

* 经典模型实现
* 论文复现
* 训练与验证代码
* 配置文件
* 实验日志
* 可视化结果
* 项目 README
* 结果分析与总结

项目将尽量按照真实机器学习工程结构组织，而不是仅保存零散 Notebook 或单个脚本。

## Current Learning Focus

当前主要学习内容：

1. 使用 Python 系统学习数据结构与算法；
2. 补充深度学习与 PyTorch 基础；
3. 熟悉计算机视觉模型的训练、验证和测试流程；
4. 阅读经典及代表性计算机视觉论文；
5. 复现规模适中的模型与实验；
6. 熟悉 Git 与 GitHub 项目管理工作流；
7. 将学习成果整理为可展示、可复现的项目仓库。

## Workflow

日常学习与项目更新采用以下流程：

```text
完成一次小任务
→ 检查修改内容
→ 添加到暂存区
→ 创建清晰的 commit
→ 推送到 GitHub
```

常用命令：

```bash
git status
git add <file-or-directory>
git diff --staged
git commit -m "type: describe the change"
git push
```

Commit message 示例：

```text
docs: add notes on Python list operations
docs: update repository README
feat: add ResNet baseline training pipeline
fix: correct dataset loading path
refactor: reorganize experiment configuration
```

## Long-term Goal

通过持续维护本仓库，逐步提升以下能力：

* 技术笔记整理
* 论文阅读与总结
* 开源代码理解
* PyTorch 项目组织
* 模型训练与调试
* 实验记录与复现
* Git 与 GitHub 工作流
* 技术成果展示与表达

本仓库将持续更新。
