---
layout: page
title: AI Book Scanner Automation
permalink: /projects/ai-book-scanner/
---

## 1. Problem Statement
Manual data entry for tracking reading habits and cataloging personal libraries is friction-heavy. The goal of this system was to utilize visual AI and pipeline automation to automatically parse images of physical books, extract structured metadata (titles, authors, genres), and log this information completely hands-free into a centralized database.

## 2. Infrastructure & Tooling
- **Webhook Gateway**: Telegram Bot (receives real-time mobile uploads).
- **Orchestration**: Make.com (formerly Integromat) handles the workflow logic, JSON parsing, and HTTP requests.
- **Inference Layer**: Google Gemini Vision API (analyzes image pixels and returns structured inferences).
- **Data Persistence**: Google Sheets (serves as a cloud-based SQL-like database for the catalog).

## 3. Workflow Architecture

<div class="mermaid">
graph TD
    A[Mobile Client] -->|Image Upload| B[Telegram Bot Webhook]
    B --> C[Make.com Workflow Trigger]
    C --> D[Image Download & Base64 Endcoding]
    D --> E[HTTP POST - Gemini Vision API]
    
    subgraph Intelligence Layer
        E -->|Prompt: Extract Title, Author, Genre| F[Structured Prediction]
        F --> G[Constraint: Force JSON format]
    end
    
    G --> H[Make.com JSON Parser]
    H -->|Array Manipulation| I[Google Sheets Append Row]
    I --> J[Personal Library Dashboard]
</div>

<script type="module">
  import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
  mermaid.initialize({ startOnLoad: true, theme: 'dark' });
</script>

## 4. Engineering Solutions & Issue Resolution
- **Format Halucinations**: Initially, the Gemini model returned valid JSON but wrapped it in Markdown formatting (```json...```), severely breaking the downstream deterministic Node/Make parser. Fixed by injecting strict prompt constraints forcing raw object outputs over stylized conversational outputs.
- **Encoding Errors**: Resolved Base64 media transmission failures during API handshakes due to file-size constraints and character mappings.
- **Data Transformation**: Engineered Make expressions to intercept variable length arrays (such as multiple authors for one textbook) and correctly joined them into sanitized single strings before executing database insertions.

## 5. Potential Future Improvements
- **Batch Processing**: Enhance the computer vision prompt to implement bounding boxes and extract information for an entire bookshelf at once simultaneously, running batched bulk queries.
- **API Cross-Validation**: Integrate the Google Books API inside the Make pipeline to cross-reference the LLM's visual guesses against an official ISBN/Author registry, filtering out "hallucinated" authors.
