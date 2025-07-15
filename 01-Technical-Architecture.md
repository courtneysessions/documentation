## Technical Architecture

**Virtual LLM Stack**

```
┌─────────────────────────────────────────┐
│ Judicial Domain-Specific Models         │
├─────────────────────────────────────────┤
│ Gemma 7B/9B Fine-tuned                  │
│ - Court Document Classification         │
│ - Legal Entity Recognition              │
│ - Jurisdiction-Specific Compliance      │
├─────────────────────────────────────────┤
│ Gemini Pro/Ultra (API)                  │
│ - Complex Document Summarization        │
│ - Multi-modal Analysis (PDF + Text)     │
│ - Agentic Workflow Orchestration        │
├─────────────────────────────────────────┤
│ Custom Embedding Models                 │
│ - Legal Document Similarity             │
│ - Case Law Retrieval                    │
│ - Precedent Matching                    │
└─────────────────────────────────────────┘
```
##  Gemini Integration Strategy: Prototype to MVP

- **Gemini Pro**: Complex document analysis requiring multi-step reasoning.
- **Gemini Vision**: OCR Processing scanned court documents and extracting structured data.
- **Function Calling**: Orchestrating specialized judicial workflows and external system integrations for legal precedent analysis.

Courtney Sessions's prototype used Google Generative AI SDK with Gemini 1.5 Flash to process uploaded documents, extracting key info and generating summaries via tailored prompts. The output was JSON, optionally XML. While effective for basic analysis, it needed extensive NLP for text extraction, section identification, and OCR edge cases.

For the core platform's backend, we switched to Gemini 2.0 Pro, which offered enhanced OCR for scanned documents. It better handled layout complexities (multi-column, skewed scans, overlapping text), providing more accurate, structured text and reducing post-processing.

With Gemini 2.5 Pro, we achieved high-accuracy document parsing @ 85%, including handwritten text. This variant improved analysis of scanned handwritten documents over 2.0 Pro and further reduced reliance on custom NLP for field extraction, data classification, and layout interpretation.