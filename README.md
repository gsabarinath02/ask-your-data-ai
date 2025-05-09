# 🧠 Ask Your Data AI

An LLM-powered application where users can upload structured data (CSV, Excel, JSON, Parquet) and ask natural language questions to:

- Get insights & answers (via SQL)
- Generate visualizations (via Plotly)
- Clean data using AI instructions
- View profiling summaries
- Download results

The app runs locally using **open-source LLMs via Ollama** for full privacy and cost-free inference.

---

## 🚀 Features

- 📁 File upload (CSV, Excel, JSON, Parquet)
- 💬 Ask questions in natural language → SQL
- 📊 AI-generated charts using Plotly
- 🧹 AI-based data cleaning using Pandas
- 📋 Data profiling report
- 📥 Download outputs (CSV, plot, summary)
- 🧠 Session history
- 🔐 Optional login system

---

## ⚙️ Setup Instructions

### 1. Clone the repository

```bash
git clone https://github.com/gsabarinath02/ask-your-data-ai.git
cd ask-your-data-ai
```

### 2. Install Python dependencies

```bash
pip install -r requirements.txt
```

### 3. Pull required Ollama models

Make sure [Ollama](https://ollama.com) is installed.

```bash
ollama pull mixtral
ollama pull codellama:python
ollama pull wizardcoder
ollama pull llama3
```

### 4. Run the app

```bash
streamlit run app.py
```

---

## 🧱 Project Structure

```bash
ask-your-data-ai/
├── app.py                     # Main Streamlit app entry point
├── requirements.txt           # Python dependencies
├── README.md                  # Documentation
├── .streamlit/
│   └── config.toml            # Streamlit theme config
├── pages/                     # Multi-page Streamlit interface
│   ├── 1_🧠_Ask_Data.py        # Ask natural questions → SQL
│   ├── 2_📊_Generate_Charts.py # AI chart generation
│   ├── 3_🧹_Clean_Data.py      # Data cleaning instructions
│   ├── 4_📋_Data_Profiler.py   # Data profiling page
│   └── 5_📥_Download_Results.py# Export results
├── utils/                     # Backend logic
│   ├── llm_router.py          # Routes requests to correct Ollama LLM
│   ├── data_utils.py          # Upload, SQLite, data parsing
│   ├── viz_utils.py           # Plot generation + safe exec
│   ├── history.py             # Session tracking
│   └── auth.py                # (Optional) Login/auth system
└── assets/
    └── background.jpg         # Background image (optional)
```

---

## 📄 File-by-File Explanation

### 📌 `app.py`

Main launcher file. Initializes the Streamlit UI, loads uploaded data, and handles routing across pages.

### 📌 `.streamlit/config.toml`

Customizes the Streamlit app theme, fonts, primary colors.

---

### 📁 pages/

| File                         | Purpose                                                                            |
| ---------------------------- | ---------------------------------------------------------------------------------- |
| `1_🧠_Ask_Data.py`         | Uses `mixtral` to convert user questions into SQL, queries data, returns results |
| `2_📊_Generate_Charts.py`  | Uses `codellama:python` to convert text → Plotly chart                          |
| `3_🧹_Clean_Data.py`       | Uses `wizardcoder` to clean the data using pandas                                |
| `4_📋_Data_Profiler.py`    | Auto profiling with `ydata-profiling`, shows insights                            |
| `5_📥_Download_Results.py` | Lets users download cleaned data, charts, summaries                                |

---

### 📁 utils/

| File              | Purpose                                                               |
| ----------------- | --------------------------------------------------------------------- |
| `llm_router.py` | Calls specific Ollama model based on task: mixtral, wizardcoder, etc. |
| `data_utils.py` | File reading, SQLite table creation, date parsing                     |
| `viz_utils.py`  | Executes LLM-generated Plotly code safely                             |
| `history.py`    | Maintains session state for Q&A, charts, etc.                         |
| `auth.py`       | Enables login via `streamlit-authenticator` (optional)              |

---

### 📁 assets/

Contains static files like:

- `background.jpg` (used for background image)
- or css needed (will add later)

---

## 🤖 LLMs Used via Ollama

| Model                | Role                                   |
| -------------------- | -------------------------------------- |
| `mixtral`          | General purpose Q&A and SQL generation |
| `codellama:python` | Python/Plotly code generation          |
| `wizardcoder`      | Pandas-based data cleaning logic       |
| `llama3`           | Backup generalist model                |

---

## 🧠 Example Prompts

- **Q&A**: "What was the total revenue in 2022 for India?"
- **Chart**: "Plot average sales per month for each category"
- **Cleaning**: "Drop rows where `Price` is null and convert `Date` to datetime"

---

## 📤 Contributors

- [gsabarinath02](https://github.com/gsabarinath02)

---

## 📜 License

MIT License
