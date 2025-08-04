# LICer 🕷️ — Local Intent Crawler & Extractor

**LICer** (Local Intent Crawler & Extractor) is a flexible, LLM-powered agent that:
- Searches the web based on natural language intent
- Crawls and parses websites without pre-defined selectors
- Extracts structured data (like job listings or apartment offers)
- Applies filters, deduplicates results, and exports clean CSVs

Designed to be modular and extensible, LICer can be used for:
- Job listings  
- Apartment or rental listings  
- Freelance gigs  
- Event or course discovery  
- Product data extraction  
…and more.

---

## 🔧 Features

- **Intent-based search:** You describe what you want — LICer finds where to look and what to extract.
- **LLM-powered HTML parsing:** Extracts key information from messy or unpredictable web structures.
- **Recursive crawling:** Follows pagination, “next” buttons, and nested links intelligently.
- **Keyword & rule filtering:** Exclude or prioritize listings based on configurable logic.
- **Deduplication engine:** Avoid repeated entries across sessions.
- **CSV output:** Easily analyze or reuse extracted data.
- **Local-first:** Designed to work with models like Mistral or LLaMA via `llama-cpp`, `ollama`, or others.

---

## 📦 Project Structure

LICer/
├── agent/
│ ├── planner.py # Uses LLM to determine where to look
│ ├── browser.py # Loads web pages (Playwright or Selenium)
│ ├── html_parser.py # Extracts structured data from HTML via LLM
│ └── filter_and_export.py # Filtering, deduplication, export
├── config/
│ └── user_query.yaml # User intent: fields, keywords, conditions
├── data/
│ └── output.csv # Extracted results
├── prompts/
│ ├── planner.txt # Prompt for search planning
│ └── parser.txt # Prompt for HTML parsing
├── run.py # Entrypoint for CLI runs
└── notebooks/
└── prototype.ipynb # Interactive test notebook
---

## 🚀 Example Usage

### 🧾 Define your search intent

### config/user_query.yaml
intent: "Find remote Python developer jobs in Indonesia"
fields:
  - Company
  - Salary
  - Location
  - Job Description
  - URL
exclude:
  - Internship
  - Jakarta
prioritize:
  - Remote
  - Junior
🕵️‍♂️ Run LICer from terminal
bash
Copy
Edit
python run.py --config config/user_query.yaml
Or run from notebook:

python
Copy
Edit
from agent.pipeline import run_pipeline
run_pipeline("config/user_query.yaml")
📤 Output
LICer will generate:

data/output.csv: Clean, filtered, deduplicated results

Preview in notebook or integrate into your app/API

## 🧠 Local LLM Support
LICer can run on your machine using:
llama-cpp-python
ollama
text-generation-webui

Preload models like Mistral 7B, LLaMA2, or quantized GGUF models.

## 🛣 Roadmap
 GUI/Web frontend (Streamlit or Gradio)

 Configurable pipelines per domain

 Integration with SQLite for persistent storage

 Chrome plugin to manually tag listings

 Dockerized runtime
---
## 📄 License
MIT License © 2025 Moreno Kristovan
Built with 🧠 local LLMs and 🕸️ flexible crawling logic.