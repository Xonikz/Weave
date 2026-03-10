# 🕸️ Cribellum
**A fully local, multi-modal RAG and TTS companion app for LM Studio**

![License: Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-blue.svg)
![Python 3.10+](https://img.shields.io/badge/Python-3.10%2B-blue)

Cribellum is a fully offline, one-click install Retrieval-Augmented Generation (RAG) companion application designed to run seamlessly alongside **LM Studio**. It provides an isolated workspace environment for ingesting diverse file types, chatting with your local LLMs, and generating high-fidelity audio synthesis.


---<img width="720" height="480" alt="Weave_GUI" src="https://github.com/user-attachments/assets/e9a32b4f-4b45-4b01-b91a-4761216caa24" />

## ✨ Core Features

* **One-Click Deployment:** Automated batch scripts handle the complex installation of PyTorch CUDA, Whisper, and IndexTTS 2, completely bypassing manual dependency management.
* **Multi-Modal Ingestion:** Process standard text and PDFs, transcribe audio notes using local Whisper, and utilize Vision LLMs to extract text from images and scanned documents. 
  > *Recommendation: Pair with a vision-capable model like Qwen3.5-VL in LM Studio for optimal optical processing.*
* **Isolated Workspaces:** Create dedicated project folders to organize reference documents. Each workspace maintains its own Chroma vector database and persistent chat history.
* **Transparent Reasoning:** Expandable UI elements allow you to view the exact step-by-step logic your LLM used to synthesize its answers.
* **On-Demand Voice Cloning:** Integrated IndexTTS 2 allows you to upload a short audio sample to clone a voice and generate high-quality `.wav` readouts of the AI's responses directly in the chat.
* **Export & Archive:** Download full conversation logs as cleanly formatted Markdown files for external use.

---

## 🛠️ Prerequisites

Before installing Cribellum, ensure you have the following ready:
1. **Python 3.10 or higher** installed on your system (ensure it is added to your system PATH).
2. **LM Studio** installed and running.
3. **LM Studio Local Server:** You must start the local inference server in LM Studio (running on the default `http://localhost:1234/v1`).

---

## 🚀 Installation & Setup

Cribellum uses a "fetch-and-build" architecture to automatically isolate its environment and download the necessary AI weights without cluttering your system.

1. Clone or download this repository to your local machine.
2. Double-click the `install.bat` file. 
3. Allow the terminal to run. It will automatically check for FFmpeg, build a Python virtual environment, install the CUDA drivers, and download the IndexTTS 2 voice models. *(Note: This process downloads several gigabytes of AI models and may take 10-15 minutes depending on your internet connection).*

---

## 💻 Usage

1. Open **LM Studio**, load your preferred LLM (and Vision model if processing images), and click **Start Server**.
2. Double-click `Start_Weave.bat` in your Cribellum folder.
3. Your browser will automatically open the Cribellum UI. 
4. Create a new workspace, upload your reference files into the Ingestion Bay, and begin chatting with your localized data!

---

## 📝 Version 1.0 Notes
This is an initial release. Further refinements, UI enhancements, and code optimizations will be added in future updates. Between Version 1.0 and Version 2.0, the architecture will be refined, and the focus will shift to responsiveness and efficiency. 

## 🗺️ Version 2.0 Roadmap

Cribellum is currently undergoing active development to evolve from a functional RAG script into a professional-grade Local ETL (Extract, Transform, Load) data manager. Version 2.0 updates will focus on UI immersion, data accountability, and automated multi-modal ingestion.

### 🎨 Phase 1: The "Studio Clean" UI Overhaul
* **Tabbed Sidebar Navigation:** Condensing the UI by separating Project, Ingestion, and Voice settings into clean, horizontal tabs to eliminate scrolling.
* **Workspace Theming:** Implementing custom CSS injection to allow workspaces to have distinct, visually branded identities (including a default "Amber Phosphor CRT" aesthetic).
* **Hover Tooltips:** Removing bulky instructional text in favor of clean `?` tooltips.
* **Custom Chat Avatars:** Replacing default Streamlit blocks with custom `.png` or emoji avatars for the User and the LLM.

### 🗃️ Phase 2: The Vault Data Manager
* **The Dossier Vault:** A central `st.dialog` overlay that acts as a searchable, sortable table of all indexed files, their token sizes, and file paths. 
* **Ledger Export:** A 1-click option to export the Workspace's memory footprint as a `.csv` for project accountability.
* **The Interactive Citation Engine:** Upgrading the chat UI so `[1]` citations become clickable `st.popover` menus. This will display the exact text/image snippet referenced, and include an OS-level command to open the *original* file directly on the user's machine (preventing shadow data duplication).

### ⚙️ Phase 3: The Automated ETL Pipeline
* **Decoupled Background Worker:** Moving the ingestion engine to an invisible Python thread, allowing the user to close the browser or navigate the UI while Cribellum processes data in the background.
* **Batch CSV Ingestion:** Allowing users to drop a CSV of file paths into Cribellum to automate massive data imports.
* **Modality Sorting (VRAM Optimization):** The engine will automatically sort batch queues to process all Text, then all Audio (Whisper), then all Images (Vision LLMs) to prevent memory thrashing and drastically speed up ingestion times.
* **Dual-Delete Architecture:** Giving users the option to "Soft Delete" (purge from AI memory but keep on disk) or "Hard Delete" (purge from both) via a `.weaveignore` blacklist system.
---
*Developed by Xonikz Independent Industries*
