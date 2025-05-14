# 🌟 Retail Risk Monitoring using LLM Agents  
**GitHub Repository: `retail-risk-monitoring`**

This project builds an **end-to-end pipeline** using **LLM agents** to monitor and assess potential risks affecting retail products (starting with **sugar** and **tuna**) over a **3-month horizon**. The goal is to detect early signals from global news (e.g., supply chain disruptions, weather events, regulations) so businesses can act proactively.

---

## 🎯 Objective

- **Detect risks** for retail products using real-time news analysis.
- Build a **modular pipeline** that can scale to new products.


---

## 📦 Features

- Modular architecture (news collection → filtering → risk classification).
- Supports multiple LLMs (OpenAI, Anthropic, HuggingFace).
- Integrates with public news APIs.
- Evaluation metrics included.
- Extensible to new products (e.g., coffee, rice).

---

## 📁 Example Project Structure

```bash
retail-risk-monitoring/
├── README.md                      # This file
├── config/
│   └── api_keys.json              # Placeholder for API keys
├── data/
│   ├── raw/                       # Raw news data
│   ├── processed/                 # Filtered news per product
│   └── validation_set.json        # Manually labeled test set
├── src/
│   ├── news_collector.py          # Fetches and filters news
│   ├── llm_interface.py           # Unified LLM calling interface
│   ├── risk_classifier.py         # Main logic for classifying risk
│   ├── evaluator.py               # Evaluates model against validation set
│   └── utils.py                   # Helper functions
├── notebooks/
│   └── sample_analysis.ipynb      # Example workflow
└── tests/
    └── test_pipeline.py           # Basic tests
```

---

## 📥 Input Data Format

Each input item should contain:

```json
{
  "product": "tuna",
  "news_title": "Fish stocks decline due to overfishing in South Pacific",
  "news_body": "New report shows tuna populations have dropped...",
  "source": "BBC",
  "date": "2025-04-01"
}
```

---

## 📤 Output Data Format

Each output should be:

```json
{
  "product": "tuna",
  "risk_detected": true,
  "confidence_score": 0.87,
  "reasoning": "News mentions declining fish stocks and overfishing which directly impacts tuna supply.",
  "risk_type": "supply_chain_disruption",
  "date": "2025-04-01"
}
```

---

## 📰 Suggested News APIs

| API | Description | Free Tier? |
|-----|-------------|------------|
| [NewsAPI](https://newsapi.org/) | General news feed; topic filtering | ✅ Yes |
| [GDELT Project](https://www.gdeltproject.org/) | Global news monitoring | ✅ Yes |
| [MediaStack](https://mediastack.com/) | Lightweight news API | ✅ Yes |
| [Google News RSS](https://news.google.com/rss) | Public RSS feeds by topic | ✅ Yes |

> **Recommended**: Start with **NewsAPI** for simplicity.

---

## 🧠 Suggested LLM Models

| Model | Use Case | Notes |
|-------|----------|-------|
| **OpenAI GPT-4o** | High accuracy | Paid API |
| **Anthropic Claude 3** | Strong reasoning | Paid API |
| **Llama 3 (HuggingFace)** | Open-source alternative | Run locally |
| **Mistral Large** | Speed-quality balance | HuggingFace |

> Wrap LLM calls in `llm_interface.py` for modularity.

---

## 📊 Evaluation Metrics

Use these metrics on a manually labeled validation set:

| Metric | Definition |
|--------|------------|
| **Accuracy** | % of correct predictions |
| **Precision** | % of predicted risks that are actual risks |
| **Recall** | % of actual risks identified |
| **F1 Score** | Harmonic mean of precision and recall |
| **Confidence Calibration** | Alignment of scores with correctness |

---

## 🛠️ Tools & Libraries

- `requests` – API calls
- `transformers`, `openai`, `anthropic` – LLM interaction
- `pandas` – Data processing
- `pytest` – Testing
- `dotenv` – API key security

---

## 📚 Validation Dataset

Create a labeled dataset (~100–200 samples) with:

- Product name
- News title/body
- Risk label (`true`/`false`)
- Risk type (e.g., `supply_chain_disruption`)
- Confidence score

**Example Prompt for Dataset Generation**:
> "You are a risk analyst. Given the following news article about tuna, would you consider it a potential business risk in the next 3 months? Explain your reasoning and rate your confidence from 0 to 1."

---

## 🧪 Sample Usage

```bash
python src/risk_classifier.py --product tuna --title "Overfishing threatens tuna stocks"
```

**Output**:
```json
{
  "risk_detected": true,
  "confidence_score": 0.92,
  ...
}
```

---

## 📝 Setup Instructions

1. Clone the repo:  
   ```bash
   git clone https://github.com/yourusername/retail-risk-monitoring.git
   ```
2. Install dependencies:  
   ```bash
   pip install -r requirements.txt
   ```
3. Set up API keys:  
   Add keys to `config/api_keys.json`
4. Run the pipeline:  
   ```bash
   python src/risk_classifier.py
   ```

---

## 🔗 Related Links

- [NewsAPI](https://newsapi.org/)
- [HuggingFace Transformers](https://huggingface.co/)
- [OpenAI API Docs](https://platform.openai.com/docs/)
- [Anthropic API Docs](https://docs.anthropic.com/en/api)

---

## 🙋 Contributors

Feel free to submit PRs or open issues. This project is designed to grow beyond the summer school!

---

## 🏷 License

MIT License

---

## ✅ Next Steps

1. Create a GitHub repo named `retail-risk-monitoring`.
2. Add this `README.md`.
3. Initialize the folder structure and placeholder scripts.
4. Add a sample validation dataset (even synthetic).
5. Fill out the Google Sheet provided by the organizers.

Let me know if you want a `requirements.txt`, sample dataset, or script templates!
