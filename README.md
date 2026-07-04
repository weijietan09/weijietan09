<h1 align="center">Cheng Jiawei</h1>

<p align="center">
  <b>深圳大学研究生</b> · 声音克隆与 TTS 语音合成大模型<br/>
  从零样本音色克隆到可控情感 / 韵律语音生成 —— 偏好<b>可复现、离线优先</b>的开源实现
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Voice_Cloning-零样本-4c8bf5?style=flat-square" alt="voice cloning"/>
  <img src="https://img.shields.io/badge/Controllable_TTS-情感·韵律-8b5cf6?style=flat-square" alt="controllable tts"/>
  <img src="https://img.shields.io/badge/Reproducible-离线优先-16a34a?style=flat-square" alt="reproducible"/>
</p>

---

## 关于我

我是深圳大学的一名研究生，研究方向是**声音克隆与文本转语音（TTS）语音合成大模型**。我关注如何从少量参考音频克隆音色（零样本克隆），以及如何让合成语音的**情感与韵律可控、可解释**。

在工程实现上，我坚持两条原则：

- **可复现**：完整的推理链路、类型标注、单元测试与持续集成，代码可以「跑通、可训练、可替换」。
- **离线优先**：默认提供无需外部权重即可运行的后备实现（如 Griffin-Lim 声码器），在 CPU 上也能验证结构。

> 说明：下方项目目前处于研究早期阶段，随包权重为**随机初始化**——重点在于打通架构与推理链路、验证结构设计，而非展示音质。预训练权重与训练脚本仍在推进中。这一点在各仓库的 README 中均如实标注。

## 研究方向

| 方向 | 关注点 |
| --- | --- |
| 零样本声音克隆 | 说话人编码器（d-vector）、少样本音色迁移、中英双语 |
| 声学建模 | 流匹配（OT-CFM）与扩散模型、少步数 ODE 采样 |
| 可控语音合成 | 情感 / 韵律解耦、VAD 情感空间、分类器无关引导（CFG） |
| 推理系统 | 流式合成、逐块出声、首包延迟优化 |

## 开源项目

### 🌊 [voxflow](https://github.com/weijietan09/voxflow) · 零样本声音克隆 TTS 工具包

用少量参考音频克隆音色的研究工具包，支持中英双语。把「说话人编码器 + 流匹配 / 扩散声学模型 + 声码器」拆成清晰、可单独替换的模块：GE2E 风格 d-vector 说话人编码器、条件流匹配（OT-CFM）声学模型（附 DDPM 扩散实现作对照）、HiFi-GAN-lite 或免训练的 Griffin-Lim 声码器。强调可复现与离线优先，CPU 上即可跑通。

<sub>`Python` · `PyTorch` · `flow-matching` · `zero-shot` · `voice-cloning` · MIT</sub>

### 🎭 [prosodia](https://github.com/weijietan09/prosodia) · 提示可控的情感 / 韵律 TTS 框架

把「怎么读」从「读什么」中解耦：用一句自然语言提示描述语气，框架将其翻译成可解释的控制量（情感 / 语速 / 基频 / 能量）再合成语音。内置 8 类情感与连续 VAD 情感空间，支持强度调节与情感插值；韵律参数在推理期可乘性缩放并配合 CFG；支持**流式推理**——梅尔谱按帧切块、重叠相加消除边界咔哒、降低首包延迟。默认 Griffin-Lim 声码器，离线可跑。

<sub>`Python` · `PyTorch` · `controllable-tts` · `emotional-tts` · `prosody` · `streaming` · MIT</sub>

## 技术栈

<p>
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" alt="python"/>
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white" alt="pytorch"/>
  <img src="https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white" alt="numpy"/>
  <img src="https://img.shields.io/badge/Ruff-000000?style=flat-square&logo=ruff&logoColor=white" alt="ruff"/>
  <img src="https://img.shields.io/badge/mypy-2A6DB2?style=flat-square" alt="mypy"/>
  <img src="https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white" alt="pytest"/>
  <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white" alt="github actions"/>
</p>

## 目前在做

- 时长对齐（单调对齐搜索 MAS），打通端到端训练
- 在公开中英数据集上训练并发布权重
- 声码器对抗训练与更完善的流式推理

<sub>研究方向：<b>声音克隆与 TTS 语音合成大模型</b> · 可控情感 / 韵律语音生成 · 可复现、离线优先的开源实现</sub>
