# QueryMind

**Agentic Business Intelligence assistant — ask questions about CSV/Excel data in plain English.**

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-backend-009688?style=flat-square&logo=fastapi)](https://fastapi.tiangolo.com)
[![LangChain](https://img.shields.io/badge/LangChain-agent-1C3C3C?style=flat-square)](https://langchain.com)
[![Groq](https://img.shields.io/badge/Groq-LLaMA%203.3%2070B-F55036?style=flat-square)](https://groq.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

Upload a spreadsheet, ask in natural language, and QueryMind autonomously runs Pandas/SQL analysis, builds charts, and returns an explained answer. Built to demonstrate agentic tool use end to end.

---

## Highlights

- **Agentic workflow:** LangChain agent with analysis, SQL, charting, and column tools
- **No-code BI:** plain-English questions over uploaded CSV/Excel
- **Follow-up memory:** ask chart variants and drill-downs in the same session
- **Auto insights:** dataset summary, KPI strip, suggested questions
- **Polished UI:** dark glassmorphism frontend served by FastAPI

---

## How it works

```
Upload file → /upload → Pandas + SQLite + schema injected into LLM
Ask question → /chat  → agent picks tools → code execution → answer (+ optional chart)
```

---

## Tech stack

| Layer | Technology |
|---|---|
| Backend | FastAPI, Uvicorn |
| Agent | LangChain tool-calling agent |
| LLM | Groq LLaMA 3.3 70B |
| Data | Pandas, SQLite |
| Charts | Matplotlib |
| Frontend | HTML, CSS, Vanilla JS |

---

## Quick start

**Prerequisites:** Python 3.10+, free [Groq API key](https://console.groq.com)

```bash
git clone https://github.com/Znaxh/QueryMind.git
cd QueryMind

python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt

echo "GROQ_API_KEY=your_key_here" > .env
uvicorn api:app --reload --port 8000
```

Open http://localhost:8000

Optional legacy Streamlit UI:

```bash
streamlit run app.py
```

---

## Example questions

| Question | What happens |
|---|---|
| `Summarize this dataset` | Row/column/type overview |
| `Which category has the highest profit?` | Pandas groupby analysis |
| `Show a bar chart of sales by region` | Matplotlib chart output |
| `What are the top 5 products by revenue?` | SQL over SQLite |
| `Now show that as a pie chart` | Follow-up with conversation memory |

---

## API

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/` | Frontend UI |
| `POST` | `/upload` | Upload CSV/Excel and initialize agent |
| `POST` | `/chat` | Ask a question, get answer + optional chart |

---

## Project structure

```
QueryMind/
├── api.py              # FastAPI app
├── app.py              # Streamlit UI (legacy)
├── agent/
│   ├── core.py         # Agent + Groq setup
│   ├── tools.py        # Analysis / SQL / chart tools
│   └── prompts.py
├── utils/
│   └── data_loader.py
└── static/
    └── index.html
```

---

## Roadmap

- [ ] Multi-file joins
- [ ] PDF export of conversations
- [ ] Auth + saved sessions
- [ ] Live database connectors

---

## Author

**Anurag Pratap Singh** · [GitHub](https://github.com/Znaxh) · [Portfolio](https://znaxh.vercel.app/)

## License

MIT — see [LICENSE](LICENSE).
