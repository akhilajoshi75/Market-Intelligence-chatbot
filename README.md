Market Intelligence Chatbot
A modular, agentic chatbot for real-time market intelligence—designed for startup founders, investors, and competitive analysts. It combines LLM-powered intent detection and synthesis with social listening, sentiment analysis, and company enrichment using People Data Labs. All conversations are persisted to SQLite, and the architecture is fully containerized for easy deployment.
________________________________________
Features
•	Natural-Language Queries: Ask in plain English about market trends, competitor data, or social sentiment.
•	Real-Time Social Listening: Fetches live Reddit posts, analyzes sentiment with VADER, and visualizes results.
•	Company Enrichment: Retrieves company profiles (description, headcount, revenue, funding) via People Data Labs.
•	LLM-Powered Synthesis: Summarizes data and suggests actionable insights using your choice of LLM (OpenAI GPT‑4 or Perplexity).
•	Persistent Chat History: Stores all exchanges in SQLite; reload the app to view past conversations.
•	Modular Architecture: Easily extend with new agents (e.g. Twitter, News, Crunchbase) or swap out LLM backends.
•	Containerized Deployment: Simple Dockerfile for building and running anywhere.
________________________________________
Project Structure
market_intel_chatbot/
├── app.py               # Main Streamlit application
├── requirements.txt     # Python dependencies
├── Dockerfile           # Containerization
├── agents/              # Modular agent implementations
│   ├── intent_detector.py
│   ├── reddit_agent.py
│   ├── sentiment_agent.py
│   ├── synthesizer_agent.py
│   └── pdl_agent.py      # People Data Labs integration
├── db/                  # Chat storage
│   └── db.py            # SQLite helpers
└── utils/               # Configuration & environment
    └── config.py
________________________________________
Prerequisites
•	Python 3.9+
•	Streamlit for the UI
•	API Keys:
o	OPENAI_API_KEY or PERPLEXITY_API_KEY
o	REDDIT_CLIENT_ID & REDDIT_CLIENT_SECRET
o	PDL_API_KEY (People Data Labs)
•	.env file at project root (not committed to Git)
________________________________________
Installation & Setup
1.	Clone the repo:
 	git clone https://github.com/akhilajoshi75/Market-Intelligence-chatbot
cd market_intel_chatbot
2.	Create a virtual environment (optional but recommended):
 	python -m venv .venv
source .venv/bin/activate  # on Windows use `.venv\Scripts\activate`
3.	Install dependencies:
 	pip install --upgrade pip
pip install -r requirements.txt
4.	Download NLTK data:
 	python - <<EOF
import nltk
nltk.download('vader_lexicon')
EOF
5.	Create a ``** file** in the root:
 	OPENAI_API_KEY=sk-...
PERPLEXITY_API_KEY=pplx-...
REDDIT_CLIENT_ID=...
REDDIT_CLIENT_SECRET=...
PDL_API_KEY=sk-...
DB_PATH=chat_history.db
________________________________________
🚀 Running Locally
streamlit run app.py
The UI will launch at http://localhost:8501 by default.
________________________________________
🔧 Configuration & Secrets Management
•	Keep your `** out of version control** via.gitignore`.
•	For CI/CD or cloud deployments, configure these as environment variables or use your provider’s secret store.
