---
layout: page
title: OpenAI API Travel Assistant
permalink: /projects/ai-chatbot/
---

## 1. Problem Statement
Generic Large Language Models often hallucinate distances, opening hours, or specific localized nuances when acting as tourist guides. This project creates a robust, deterministic AI Travel Assistant designed specifically for Parisian tourism, constraining an LLM using rigorous prompt engineering to guarantee precise, structured API JSON outputs without deviating into unstructured conversational tangents.

## 2. Dataset
- **Source**: Dynamic inference feed through the OpenAI API, relying on pre-trained model knowledge alongside few-shot context examples.
- **Dataset Size**: Evaluated locally using an internal set of 250 common synthetic tourist queries (e.g., "From Louvre to Eiffel Tower using Metro?").
- **Features**: Query length, entity extraction (origin, destination, time constraint), intent classification.
- **Preprocessing**: Raw user queries are parsed through an entity-recognition chain before being packaged into the final structured prompt template for the OpenAI endpoint.

## 3. Feature Engineering
- **Context Injection**: Pre-pended system instructions containing explicit constraints regarding response format, currency calculations (EUR), and strict transit modes.
- **Few-Shot Examples**: Appended three structured conversational pairs (User Query -> Expected JSON) directly into the prompt to anchor the deterministic style.

## 4. Models Tested

| Model | Schema Adherence | Latency (ms) |
|-------|------------------|--------------|
| GPT-3.5-Turbo (Zero-shot) | 0.65 | 450 |
| GPT-3.5-Turbo (Few-shot) | 0.94 | 600 |
| GPT-4 (Zero-shot) | 0.98 | 1250 |
| GPT-4 (Few-shot) | 1.00 | 1400 |

## 5. Final Model
**GPT-3.5-Turbo (Few-shot)** was selected for the final architecture. While GPT-4 achieved perfect schema adherence, the 1400ms latency significantly impacted the UX of a real-time chat interface. GPT-3.5-Turbo, when guided by robust few-shot prompting, successfully mitigated hallucinations and reached a 94% acceptable adherence rate at half the response latency.

## 6. Evaluation
- **JSON Validation**: Employed an automated Pydantic schema validation script to score every response in the 250 test suite.
- **Latency Tracking**: Tracked average, p90, and p99 response times to ensure production readiness.
- **Hallucination Rate**: Manually evaluated 50 random complex distance queries; the few-shot 3.5 model hallucinated incorrect transit lines on only 3 occasions (6%).

## 7. System Architecture
<div class="mermaid">
graph TD
    A[User Query Web Form] --> B[Sanitization & Entity Parsing]
    B --> C[Few-Shot Prompt Construction]
    
    subgraph OpenAI Communication Layer
        C --> D[POST Request GPT-3.5-Turbo]
        D --> E[JSON Response]
    end
    
    subgraph Output Validation
        E --> F{Pydantic Schema Check}
        F -->|Valid| G[Render UI Response]
        F -->|Invalid| H[Fallback Retry Logic]
        H --> C
    end
</div>

<script type="module">
  import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
  mermaid.initialize({ startOnLoad: true, theme: 'dark' });
</script>

## 8. Key Learnings
Prompting is fundamentally a software design problem. Transitioning from zero-shot to few-shot prompting yielded more stability than switching model generations completely. Furthermore, adding deterministic fallback parsing logic on the backend is mandatory, as APIs will inevitably timeout or fail schema adherence under load.

## 9. GitHub Repository
[Source Code: OpenAI Travel Assistant](https://github.com/anshid)

## 10. Future Improvements
- Integrate LangChain to allow the model to query an actual live mapping API like Google Maps internally, replacing LLM parameter knowledge with live routing data.
- Build up conversational memory logic to allow users to ask "how far is the previous location from here?"
