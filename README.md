# 🎧 AI-Based Real-Time Interpretation System

**This is the repo for my bachelor thesis on the topic of:**
Development and Evaluation of an AI-Based Real-Time Interpretation System with Hardware Integration Feasibility

**Note:** Since tis Thesis contains more than what is illustrated here and was conducted over several months, it is highly recommended to refer to, or read the full thesis document, or relevant parts depending on your needs, which can be found <a href="https://github.com/AbdelrahmanMohamed54/Bachelor-Thesis/blob/main/complete_final_thesis.pdf">here</a>.

---

## 📌 Overview

This project implements a **real-time AI-based simultaneous interpretation system** that converts live speech into translated speech with low latency.

The system integrates:

* Streaming Automatic Speech Recognition (ASR)
* Stability-aware segmentation
* Neural Machine Translation (NMT)
* Neural Text-to-Speech (TTS)
* Professional audio hardware integration (Dante / Bosch Integrus)

Unlike many AI translation demos, this project focuses on **system-level orchestration, latency control, stability management, and deployability in professional conference environments**.

---

## 🎯 Objectives

The system was designed to:

1. Enable **real-time speech-to-speech interpretation**
2. Explicitly manage the **latency–stability trade-off**
3. Provide a **modular, provider-agnostic architecture**
4. Support **multi-language parallel output** (German, Arabic, English)
5. Validate **professional hardware integration feasibility**

---

## 🏗️ System Architecture

The system follows a cascaded, streaming pipeline:

```
Live Audio
   ↓
Streaming ASR
   ↓
Stability-Aware Segmentation
   ↓
Parallel NMT (Multi-Language)
   ↓
Neural TTS
   ↓
PCM Audio Output
   ↓
Dante / Professional Hardware Routing
```
<p align="center"> <img src="https://github.com/AbdelrahmanMohamed54/Bachelor-Thesis/blob/main/latex_source_code/img/figures/system_architecture_diagram.drawio.svg" alt="abdelrahmanmohamed54" /> </p>
```

### Key Architectural Features

* 🔄 Fully streaming and asynchronous pipeline
* 🧩 Modular abstraction layer for ASR, NMT, and TTS providers
* 🌍 Parallel multi-language translation
* 🎛 Hardware-compatible PCM output
* 📡 Low-latency WebSocket-based backend communication

---

## 🧠 Core Innovation: Stability-Aware Segmentation

Streaming ASR produces unstable partial hypotheses.
Direct translation would cause flicker and re-translations.

This project introduces a **segmentation control layer** that:

* Maintains a rolling buffer of ASR output
* Detects candidate boundaries using punctuation + pauses
* Applies a dynamic token threshold to bound latency
* Enforces a stability window before translation
* Minimizes output erasure and instability

<p align="center"> <img src="https://github.com/AbdelrahmanMohamed54/Bachelor-Thesis/blob/main/latex_source_code/img/figures/segment_flow.drawio.svg" alt="abdelrahmanmohamed54" /> </p>

This explicitly manages the **latency vs stability trade-off**, a critical challenge in real-time interpretation.

---

## 📊 Evaluation Framework

The system was evaluated using system-level latency and stability metrics:

All results are documented <a href="https://github.com/AbdelrahmanMohamed54/Bachelor-Thesis/blob/main/complete_final_thesis.pdf">here</a> respectively.

### Latency Metrics

* Average Lagging (AL)
* Length-Adaptive Average Lagging (LAAL)
* Real-Time Factor (RTF)
* First-Token Latency (FTL)
* Time to First Audio (TTFA)

### Stability Metrics

* Flicker Rate
* Normalized Erasure (NE)
* Consecutive Wait (CW)

Ablation studies were conducted to analyze:

* Stability window size
* Token threshold impact
* Component-level latency breakdown

---

## 🎛 Hardware Integration

**Traditional Hardware Integratiion:**

<p align="center"> <img src="https://github.com/AbdelrahmanMohamed54/Bachelor-Thesis/blob/main/latex_source_code/img/figures/signal_chain.drawio.svg" alt="abdelrahmanmohamed54" /> </p>

---

The system was experimentally validated with:

* **Bosch Integrus professional interpretation hardware**
* **Dante Virtual Soundcard**
* Up to **8 parallel language channels**

<p align="center"> <img src="https://github.com/AbdelrahmanMohamed54/Bachelor-Thesis/blob/main/latex_source_code/img/figures/dante_layer.drawio.svg" alt="abdelrahmanmohamed54" /> </p>

Key properties:

* Uncompressed PCM audio
* Low-latency Ethernet transmission
* Dedicated channel mapping per language
* Professional routing compatibility

This demonstrates feasibility beyond software-only prototypes.

---

## 🚀 Potential Applications

* International conferences
* Institutional meetings
* Hybrid events
* Accessibility services
* Cost-sensitive multilingual events

---

## 🔮 Future Work

* On-device / edge inference
* Adaptive latency control
* User-based quality evaluation
* Full duplex conversation support
* Extended professional audio ecosystem integration

---

# 🏆 Summary

This thesis investigated the design and evaluation of a real-time AI-based simultaneous interpretation system, focusing on system-level orchestration, latency control, and professional deployment feasibility. By integrating streaming Automatic Speech Recognition (ASR), Neural Machine Translation (NMT), and Neural Text-to-Speech (TTS) within a modular architecture, the system demonstrated that real-time speech-to-speech interpretation is technically achievable under practical constraints.

A central contribution of this work is the stability-aware segmentation strategy, which explicitly manages the latency–stability trade-off inherent in streaming ASR systems. The evaluation, conducted using latency metrics such as AL, LAAL, RTF, FTL, and TTFA, alongside stability metrics including Flicker Rate, Normalized Erasure, and Consecutive Wait, showed that controlled segmentation significantly improves output reliability without compromising responsiveness.

The results highlight that overall system performance depends more strongly on orchestration, buffering strategies, and latency management than on the specific choice of AI models. Additionally, the feasibility study confirmed that AI-generated PCM audio can be successfully integrated into professional interpretation environments using Dante and Bosch Integrus hardware without introducing significant additional latency.

Remaining challenges include dependency on cloud-based APIs, sensitivity to network conditions, and the absence of large-scale user perception studies. Future improvements may focus on adaptive latency control, edge deployment, and deeper hardware-level integration.

Overall, the findings demonstrate that AI-driven simultaneous interpretation systems can move beyond software prototypes toward deployable, conference-grade solutions when latency, stability, and system integration are addressed holistically.
