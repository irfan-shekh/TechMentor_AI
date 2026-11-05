# 🚀 TechMentor AI — Technical Q&A Assistant

Welcome to **TechMentor AI**, an interactive, multi-modal technical Q&A assistant built with **Gradio** for developers, engineers, and learners. 

TechMentor AI pairs cutting-edge cloud LLMs (Groq, OpenAI / OpenRouter) with local models (Ollama Llama 3.2), offering real-time streaming, interactive Python code execution, syntax inspection, and full voice-in / voice-out capabilities.

---

## ✨ Key Features

- **🌐 Multi-Model Switching**: Seamlessly toggle between:
  - **Groq**: OpenAI GPT-OSS 120B (ultra-fast inference) & Qwen 3.8 27B
  - **OpenAI / OpenRouter**: GPT-4o-mini
  - **Local Ollama**: Llama 3.2 running completely offline on your local machine
- **⚡ Real-Time Streaming**: Token-by-token response streaming for a fast, responsive conversational experience.
- **🛠️ Integrated Tool Calling**:
  - **Python Sandbox**: Safely executes Python code snippets in an isolated scope to verify logic, run calculations, and demonstrate outputs.
  - **AST Syntax Inspector**: Parses code into an Abstract Syntax Tree to inspect Python grammar, nodes, and syntax errors.
- **🎙️ Voice Multi-Modal (Audio In & Out)**:
  - **Speech-to-Text**: Record or upload audio queries transcribed using Whisper (`whisper-large-v3-turbo` or OpenAI `whisper-1`).
  - **Text-to-Speech**: Synthesizes spoken explanations via `gTTS` or OpenAI TTS (`tts-1`).
- **🎯 Customizable System Prompting**: Inject custom system prompts to tailor persona, seniority level (e.g., Principal Architect, Refactoring Specialist), and output constraints.

---

## 📁 Project Structure

```text
techmentorai/
├── app.py                # Main Gradio application script
├── Chatbot.ipynb         # Interactive Jupyter Notebook for development and experimentation
├── .env                  # Environment variables for API keys (ignored by git)
├── .gitignore            # Git ignore file for secrets and temporary files
└── README.md             # Project documentation
```

---

## 🚀 Getting Started

### 1. Prerequisites

- Python 3.10+ installed on your system.
- *(Optional, for local inference)* [Ollama](https://ollama.com/) installed.

### 2. Installation

Clone or open the repository, then install the required Python packages:

```bash
pip install gradio openai groq gTTS python-dotenv
```

### 3. Configure API Keys (`.env`)

Create a `.env` file in the root directory (if not already created) and add your keys:

```env
OPENAI_API_KEY=your_openai_api_key_here
GROQ_API_KEY=your_groq_api_key_here
```

> **Note:** If you only intend to use local models via Ollama, API keys are optional. The app will gracefully fall back to local models and gTTS.

---

## 🦙 Running Local Models with Ollama

To run **Llama 3.2** locally:

1. **Install Ollama**: Download from [ollama.com](https://ollama.com/) if you haven't already.
2. **Start the Ollama daemon**:
   - Launch the Ollama app from your Start Menu, or run in your terminal:
     ```powershell
     ollama serve
     ```
3. **Pull the Llama 3.2 model**:
   ```powershell
   ollama pull llama3.2
   ```
4. **Verify**: Ensure the model is available:
   ```powershell
   ollama list
   ```
   In the web interface, select **`Ollama: Llama 3.2 (Local Machine)`** from the model dropdown.

---

## 💻 Running the Web Application

Launch the Gradio interface:

```bash
python app.py
```

Once started, open your browser and navigate to:
```text
http://localhost:7865
```

---

## 💡 Quick Examples Included in UI

The interface includes one-click prompt templates to test the assistant:
- **System Design**: Scalable URL Shortener architecture and database choices.
- **Algorithms**: A* search pathfinding algorithm with custom heuristics.
- **Debugging**: Explaining why `0.1 + 0.2 != 0.3` with Python IEEE 754 precision analysis.
- **Security**: SQL injection vulnerability reproduction and parameterized query remediation.

---

## 🔧 Troubleshooting

| Issue | Cause | Solution |
| :--- | :--- | :--- |
| `Connection error / APIConnectionError` with Ollama | Ollama service is not running | Launch Ollama from Start Menu or run `ollama serve` in a terminal. |
| `ModuleNotFoundError: No module named 'gradio'` | Dependencies not installed in current Python env | Run `pip install gradio openai groq gTTS python-dotenv`. |
| `Audio transcription error` | No API key configured for Whisper | Add a `GROQ_API_KEY` or `OPENAI_API_KEY` in `.env`. |
| `Port 7865 already in use` | Another instance of `app.py` is running | Stop the other instance or change `server_port` in `app.py`. |

---

## 📜 License

Created as part of the LLM Engineering course capstone project.
