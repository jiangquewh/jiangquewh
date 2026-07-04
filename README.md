<h1 align="center">Jiang Que · 雀江</h1>

<p align="center">
  <b>武汉大学研究生</b> · 声音克隆与表现力 TTS 语音合成大模型<br/>
  <sub>从多说话人音色克隆，到韵律与情感可控的语音生成 —— 偏好<b>可复现、离线优先</b>的开源实现</sub>
</p>

<p align="center">
  <img alt="Focus" src="https://img.shields.io/badge/研究方向-Voice%20Cloning%20%2F%20Expressive%20TTS-6f42c1">
  <img alt="Language" src="https://img.shields.io/badge/主力语言-Python-3776AB?logo=python&logoColor=white">
  <img alt="Framework" src="https://img.shields.io/badge/PyTorch-EE4C2C?logo=pytorch&logoColor=white">
  <img alt="Locale" src="https://img.shields.io/badge/双语前端-中文%20%2F%20English-0aa">
  <img alt="Reproducible" src="https://img.shields.io/badge/理念-Reproducible%20%26%20Offline--first-2ea44f">
</p>

---

## 👋 关于我

我是武汉大学的一名研究生，研究方向围绕**语音合成（TTS）与声音克隆**展开：

- **声音克隆**：多说话人音色建模、音色解耦、少样本（few-shot）克隆与韵律迁移。
- **表现力语音合成**：情感 / 风格可控的语音生成，重点放在文本前端与**韵律**建模上。
- **工程理念**：坚持**可复现、离线优先**——核心逻辑尽量少依赖、开箱即可离线跑通、可测试、可断言，让研究成果易于复现与二次开发。

我把这两条线索理解为一个连贯的整体：**先把「音色 / 说话人」建模清楚（声学模型层），再把「表现力 / 韵律」控制做扎实（框架层）**，两者构成一个完整的表现力 TTS 技术栈。

## 📌 主要项目

下面都是本账号已开源的真实仓库，欢迎查阅源码与文档。

| 项目 | 简介 | 关键词 |
| :-- | :-- | :-- |
| **[prosodia](https://github.com/emilymartin456/prosodia)** | 情感 / 风格可控的**表现力语音合成框架**：文本前端（规范化 + 拼音注音变调 + 韵律短语切分）→ 表现力控制 → 可插拔声学后端 → 流式输出。纯 Python、离线优先，自带参考声码器可开箱出声。 | `Expressive TTS` · `Prosody` · `Streaming` |
| **[timbrel](https://github.com/emilymartin456/timbrel)** | 面向研究的**多说话人声音克隆声学模型**：非自回归（FastSpeech2 风格）骨干，围绕音色解耦、说话人自适应、少样本克隆与韵律迁移展开，原生支持中英双语前端。 | `Voice Cloning` · `Disentanglement` · `zh/en` |

### 🎛️ prosodia — 表现力 TTS 框架
把一段中/英文文本经「**文本前端 → 表现力控制 → 声学后端 → 流式输出**」四阶段合成为带情感与风格的语音，难点集中在前端与韵律：

- **中文文本前端**：数字 / 日期 / 金额 / 单位规范化，`pypinyin` 注音（TONE3），三声连读与「不 / 一」变调。
- **韵律与表现力**：规则韵律短语切分（可插拔 `PhraseBreaker`），内置 8 种情感与命名风格预设，语速 / 音高 / 能量 / 停顿连续可调。
- **接入语言模型**：统一 `LLMAdapter` 接口做规范化与韵律预测，默认离线规则适配器，带磁盘缓存保证可复现。
- **流式实时**：按句 / 短语切块的流式引擎，附带实时率（RTF）与首包延迟指标；`AcousticBackend` 注册表预留神经后端接入点。

### 🧬 timbrel — 多说话人声音克隆声学模型
聚焦「**文本 + 参考音频 → 梅尔谱**」的声学建模阶段：

- **音色解耦**：内容编码器用实例归一化去除句级统计，配合梯度反转对抗分类器与 CLUB 互信息上界，抑制内容表征中的说话人信息。
- **说话人自适应**：解码器采用条件 LayerNorm（AdaSpeech 风格）注入音色，自适应时只微调该部分参数，天然适合少样本。
- **少样本克隆 & 韵律迁移**：对若干参考语音的 d-vector 取平均完成说话人注册；独立韵律编码器经对抗训练与说话人解耦，可将 A 的音色与 B 的韵律组合。
- **中英双语前端**：中文 `pypinyin` 转声母 / 韵母 + 声调，英文词典 + 规则回退，统一音素表并支持中英混排。

## 🧰 技术栈

<p>
  <img alt="Python" src="https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white">
  <img alt="PyTorch" src="https://img.shields.io/badge/PyTorch-EE4C2C?logo=pytorch&logoColor=white">
  <img alt="NumPy" src="https://img.shields.io/badge/NumPy-013243?logo=numpy&logoColor=white">
  <img alt="pypinyin" src="https://img.shields.io/badge/pypinyin-中文注音-0aa">
  <img alt="GitHub Actions" src="https://img.shields.io/badge/CI-GitHub%20Actions-2088FF?logo=githubactions&logoColor=white">
</p>

- **建模**：非自回归 TTS、说话人 / 内容解耦、条件归一化、对抗训练与互信息约束。
- **语音前端**：中英双语文本规范化、拼音注音与变调、韵律短语切分。
- **系统工程**：流式 / 实时推理、可插拔后端接口、离线优先、CI 与可复现测试。

## 🔭 近期在做

- 让 **timbrel**（声学模型）与 **prosodia**（表现力框架）的接口对齐，把真实神经声学后端接入 `AcousticBackend`。
- 打磨韵律迁移与情感强度控制的可控性与稳定性。
- 持续完善文档与可运行示例，保持「clone 下来就能离线跑通」的体验。

---

<p align="center"><sub>本页仅索引本账号已开源的真实仓库；内容力求与仓库源码及文档一致。</sub></p>
