# Document Intelligence Retrieval System (RAG Pipeline)

## Problem Context
Developed during an **AI and Automation Externship at Outamation**. This project addresses the challenge of automated text extraction, classification, and context-aware semantic search over dense, unstructured corporate financial and mortgage documentation.

---

## System Architecture & Workflow

The architecture is built as a modular, high-throughput pipeline transitioning raw, multi-format PDFs into an indexable knowledge base:

1. **Optical Character Recognition (OCR):** Utilizes `PyMuPDF` for structural text layout parsing and a custom fallback OCR engine to extract character layers from scanned, image-only document pages safely.
2. **Context-Aware Semantic Chunking:** Splits unstructured text blocks hierarchically to guarantee that relevant header boundaries and sentence contexts remain bound together inside the embedding window.
3. **Indexing & Retrieval:** Built on top of `LlamaIndex` to structure vector index representations. The query pipeline leverages semantic similarity thresholds to surface optimal parent/child context blocks.
4. **Augmented Response Generation:** Feeds the context-aligned text segments directly into a grounded open-source LLM layer, executing precise information search while eliminating hallucination bounds.

---

## Tech Stack & Dependencies

- **Framework orchestration:** `LlamaIndex`
- **Data Preprocessing & Parsers:** Python, `PyMuPDF`, `Tesseract OCR`
- **Core Vector Math & Operations:** NumPy, Scikit-Learn
- **Execution Environment:** Interactive Jupyter Lab Workflow

---

## Key Engineering Engineering Trade-Offs

- **Chunk Window Optimization:** Balanced embedding precision vs. context fragmentation. The pipeline applies a sliding character chunk overlap window to preserve continuity without blowing past the upstream token constraints of the LLM.
- **Enterprise Data Compliance:** Designed with a zero-external-storage mindset. Document processing pipelines execute locally or within secure enterprise clusters to guarantee that sensitive consumer mortgage metrics remain completely uncompromised.
