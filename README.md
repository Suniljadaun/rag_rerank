# RAG: Baseline vs. Re-Ranking

Compares two retrieval pipelines over the same chunked document:
- **Pipeline 1:** bi-encoder (`all-MiniLM-L6-v2`) + FAISS, top 10 → top 3 to the LLM
- **Pipeline 2:** same top 10, re-ranked by a cross-encoder (`ms-marco-MiniLM-L6-v2`) → top 3 to the LLM

Both pipelines use the same prompt and the same LLM (`gemini-2.5-flash`, temperature 0).

## Document
`document.pdf` is the GDPR, Regulation (EU) 2016/679, downloaded from
[EUR-Lex](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX:32016R0679). 88 pages, 419 chunks.

## Files
- `rag_rerank.ipynb`: the full notebook with outputs
- `failure_cases.csv`: the four case studies (questions, gold chunks, both answers)
- `requirements.txt`: Python packages

## How to run
1. `python -m venv venv`, activate it, then `pip install -r requirements.txt`
2. Create a `.env` file containing `GEMINI_API_KEY=your_key` (free key from Google AI Studio)
3. Open `rag_rerank.ipynb` and run all cells

Ran on CPU. The Gemini free tier allows 5 requests/minute and 20/day; one full run uses about 11.