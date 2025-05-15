# 🌟 Retail Risk Monitoring using LLM Agents  
**GitHub Repository: `retail-risk-monitoring`**

This project builds an **end-to-end pipeline** using **LLM agents** to monitor and assess potential risks affecting retail products (starting with **sugar** and **tuna**) over a **3-month horizon**. The goal is to detect early signals from global news (e.g., supply chain disruptions, weather events, regulations) so businesses can act proactively.

# Problem statement 
**Problem Statement**  
Global supply chains for retail commodities are increasingly vulnerable to disruptions caused by geopolitical, environmental, and regulatory shifts, which can escalate costs, delay deliveries, and destabilize markets. Products like sugar and tuna, which rely on geographically concentrated production and complex logistics, are particularly at risk. Traditional risk assessment methods often rely on retrospective analyses or siloed data, leaving businesses reactive to emerging threats. Manual monitoring of global news and events is time-consuming, error-prone, and ill-suited for detecting subtle early signals—such as localized weather anomalies, port strikes, or policy drafts—that may cascade into systemic risks. Consequently, decision-makers lack timely, actionable insights to mitigate disruptions within critical planning windows, such as the 3-month horizon pivotal for inventory and procurement strategies.  

To address this gap, we propose an automated, end-to-end pipeline leveraging large language model (LLM) agents to continuously analyze heterogeneous data streams—news articles, government reports, and social media—for early indicators of supply chain risks. By integrating real-time information extraction, causal reasoning, and probabilistic forecasting, the system aims to quantify risks and generate proactive alerts tailored to specific commodities. Focusing initially on sugar and tuna, this approach seeks to transform reactive risk management into a dynamic, predictive process. The pipeline’s adaptability to diverse products and scenarios offers a scalable solution to enhance supply chain resilience, enabling businesses to preempt disruptions rather than merely respond to them.



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

## 📁 Example Project Structure (it is not necessry, but perhaps some strucure is required based on integration needs)

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

An example input:

```json
{
  "product": "tuna",
  "use news pre filter": false
  "news_title": [a, list, of, news, sources],
  "strategy": "Chain of thought",
  "Extra information": Currently an average price for a tuna can is 5$ and our main supplier is in Thailand
}
```

---

## 📤 Output Data Format

An example output:

```json
{
  "product": "tuna",
  "risk_detected": true,
  "confidence_score": 0.87,
  "reasoning": "News mentions declining fish stocks and overfishing which directly impacts tuna supply.",
  "risk_type": "supply_chain_disruption",
  "supporting sources": [a, list, of, supporting, sources, on, the, internet]
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
| **QWen 3** | High accuracy | Run locally |
| **Llama 3 (HuggingFace)** | Open-source alternative | Run locally |
| **Mistral Large** | Speed-quality balance | HuggingFace or use free API |

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

Note, you will need to create a validation script which demonsrates performance report with metrics above. 
Instead of real news your framework will be using this dataset.

Create a labeled retro-dataset (~100–200 samples) with:

- Product name
- News title/body
- Risk label (`true`/`false`)
- Risk type (e.g., `supply_chain_disruption`)
- Confidence score



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

---

## 🙋 Contributors

Feel free to submit PRs or open issues. This project is designed to grow beyond the summer school!

---

## 🏷 License

MIT License

---

## ✅ Validation

1. We will install your framework - it should not have any errors during installation
2. We will run it in real time for current date and analyze response
3. We will run validation script using your validation dataset, at this time framework should use your dataset instead of real news.


