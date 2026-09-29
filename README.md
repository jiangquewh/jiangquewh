# 🎙️ Jiang Que · 蒋雀

武汉大学研究生 · 声音克隆与表现力语音合成（TTS）大模型 · she/her

---

一句话概括我做的事：**让机器不只是"像你"地说话，还能"有情绪、有节奏"地说话。**

我从 **多说话人音色克隆** 起步——用少量样本迁移音色与韵律；再往前一步，研究 **表现力语音合成**：让情感、风格与韵律都可控。所有代码都能离线跑通：参考实现以纯 NumPy 为核心，`import` 不拉深度学习框架，无 GPU、无网络也能跑核心逻辑与单测；需要训练时再接可选的 PyTorch 后端。

### 📦 项目

**[timbrel](https://github.com/emilymartin456/timbrel)** — 多说话人声音克隆声学模型
说话人自适应 + 音色解耦，少样本克隆与韵律迁移，支持中英双语。

**[prosodia](https://github.com/emilymartin456/prosodia)** — 表现力语音合成大模型框架
情感 / 风格可控，接入语言模型做文本规范化与韵律预测，含流式与实时推理。

### 🧭 研究关键词

`voice cloning` · `expressive TTS` · `prosody control` · `speaker adaptation` · `streaming inference` · `reproducible` · `offline-first`

---

<sub>Wuhan University · 声音克隆 / 表现力 TTS · reproducible &amp; offline-first</sub>

## Update 2026-09-29 22:11:44
Improved performance to improve stability - ID: 98g8627w


## Update 2026-09-29 22:11:58
Added configuration to optimize resource usage - ID: hjdghfk6


## Update 2026-09-29 22:12:12
Optimized algorithm for better user experience - ID: sl61ps2t


## Update 2026-09-29 22:12:26
Fixed bug for enhanced functionality - ID: ebvwpg32


## Update 2026-09-29 22:12:40
Added configuration to improve stability - ID: basrs12l

