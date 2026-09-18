# PraxaNew — RAG Prototype with Streamlit UI

**PraxaNew** is a prototype Retrieval-Augmented Generation (RAG) application featuring a clean, interactive Streamlit chat interface. Users can ask questions directly in the UI, and the app retrieves relevant context documents, queries an LLM to generate an accurate answer, and displays both the response and the source passages used.

---

## ✨ Features

- **Interactive UI:** Streamlit-based chat interface with session-based chat history (`st.session_state`).
- **Robust RAG Pipeline:** Automatically retrieves context and returns:
  - The generated answer.
  - The source/context passages used to produce the answer.

---

## 📂 Project Structure

```text
PraxaNew/
├── .streamlit/
│   └── config.toml        # Streamlit configuration (e.g., file watcher settings)
├── .env.example           # Example environment variable file
├── praxa_client.py        # Streamlit chat client (UI layer)
├── praxa_rag.py           # Core RAG logic and integration functions
├── context.py             # Context & document handling (loading, chunking, retrieval)
├── model.py               # Model/LLM interaction layer
├── requirements.txt       # Python dependencies
└── hello_world.py         # Basic Streamlit demo file from early setup
```

---

## 🛠️ Prerequisites & Requirements

- **Python 3.10+** (recommended)
- `pip` or other virtual environment management tools

---

## 🚀 Setup & Installation

### 1. Clone the repository
```bash
git clone https://github.com/OldSnakey/PraxaNew.git
cd PraxaNew
```

### 2. Create and activate a virtual environment

**Windows (PowerShell):**
```powershell
python -m venv env
.\env\Scripts\Activate.ps1
```

**macOS / Linux:**
```bash
python -m venv env
source env/bin/activate
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Configure environment variables
Copy the example configuration file and fill in your custom keys (API keys, endpoints, etc.):
```bash
cp .env.example .env
```
> ⚠️ **Important:** Never commit your local `.env` file to version control.

---

## 🖥️ Running the Application

Start the Streamlit interface using the command line:
```bash
streamlit run praxa_client.py
```

Once running, open the local URL provided by Streamlit in your browser (typically `http://localhost:8501`).

### 💡 Note on Streamlit File-Watcher (Windows / PyTorch)
If you encounter noisy tracebacks involving *"no running event loop"* or PyTorch classes, you can disable Streamlit's file watcher at runtime:
```bash
streamlit run praxa_client.py --server.fileWatcherType none
```
*(You can also configure this permanently inside `.streamlit/config.toml`)*.

---

## 🎮 Usage

1. Type a question into the chat input box.
2. Review the assistant's synthesized answer.
3. Check the expandable source/context section to verify the passages used for the most recent response.

---

## 📝 Development Notes

- The Streamlit UI manages chat history natively via `st.session_state`.
- The core RAG function exposed by `praxa_rag.py` returns a dictionary structured with distinct keys for both the answer text and source references.
