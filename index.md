---
layout: home
title: Home
---

<div class="hero" style="text-align: center; padding: 6rem 1rem 4rem; max-width: 800px; margin: auto;">
  <h1 style="font-size: 3.5rem; line-height: 1.2; margin-bottom: 1.5rem;">Machine Learning Engineer with <span class="glow-text">Mathematical Foundations</span></h1>
  <p style="font-size: 1.25rem; color: var(--text-main); font-weight: 500; margin-bottom: 0.5rem;">I design machine learning systems grounded in mathematical principles such as optimization, probability, and dynamical systems.</p>
  <p style="font-size: 1.1rem; color: var(--text-muted); margin-bottom: 2.5rem;">PhD in Mathematics (Topological Dynamics & Ergodic Theory) from BITS Pilani.</p>
  
  <div style="display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap;">
    <a href="#projects" class="btn btn-primary" style="padding: 0.9rem 2rem; font-size: 1.05rem;">View Projects</a>
    <a href="{{ '/about/' | relative_url }}" class="btn" style="padding: 0.9rem 2rem; font-size: 1.05rem; border: 1px solid var(--glass-border); color: var(--text-main);">About Me</a>
  </div>
</div>

<div style="text-align: center; margin-bottom: 6rem;">
  <p style="text-transform: uppercase; font-size: 0.85rem; letter-spacing: 2px; color: var(--text-muted); margin-bottom: 1.5rem;">Core Tech Stack</p>
  <div style="display: flex; gap: 0.75rem; justify-content: center; flex-wrap: wrap; max-width: 600px; margin: auto;">
    <span class="tag" style="font-size: 0.95rem; padding: 0.5rem 1rem;">Python</span>
    <span class="tag" style="font-size: 0.95rem; padding: 0.5rem 1rem;">PyTorch</span>
    <span class="tag" style="font-size: 0.95rem; padding: 0.5rem 1rem;">TensorFlow</span>
    <span class="tag" style="font-size: 0.95rem; padding: 0.5rem 1rem;">Scikit-learn</span>
    <span class="tag" style="font-size: 0.95rem; padding: 0.5rem 1rem;">SQL</span>
    <span class="tag" style="font-size: 0.95rem; padding: 0.5rem 1rem;">Generative AI</span>
  </div>
</div>

<div id="projects" class="section-title">
  <h2 style="color: var(--accent-primary);">Key Projects</h2>
</div>

<div class="modern-grid" style="margin-bottom: 4rem;">
  <!-- Featured Project 1 -->
  <div class="modern-card">
    <h3 style="font-size: 1.25rem; margin-bottom: 0.5rem;">Placement Predictor ML System</h3>
    <div class="card-tags" style="margin-bottom: 1rem;">
      <span class="tag">Scikit-Learn</span>
      <span class="tag">Data Processing</span>
    </div>
    <ul style="font-size: 0.95rem; color: var(--text-muted); margin-bottom: 1.5rem; padding-left: 1.2rem; line-height: 1.6;">
      <li><strong>Problem statement:</strong> Predict student placement outcomes based on academic profiling metrics.</li>
      <li><strong>Dataset size:</strong> ~10,000 records</li>
      <li><strong>Models tested:</strong> Logistic Regression, Random Forest, XGBoost</li>
      <li><strong>Evaluation metrics:</strong> F1-Score, ROC-AUC</li>
      <li><strong>Final model performance:</strong> 94% accuracy with optimized Random Forest</li>
    </ul>
    <a href="https://github.com/anshid/placement-predictor-ml" target="_blank" class="glow-text" style="font-weight: 600; margin-top: auto; display: inline-block;">View on GitHub &rarr;</a>
  </div>

  <!-- Featured Project 2 -->
  <div class="modern-card">
    <h3 style="font-size: 1.25rem; margin-bottom: 0.5rem;">Predictive Modeling for Agriculture</h3>
    <div class="card-tags" style="margin-bottom: 1rem;">
      <span class="tag">Scikit-learn</span>
      <span class="tag">Feature Selection</span>
    </div>
    <ul style="font-size: 0.95rem; color: var(--text-muted); margin-bottom: 1.5rem; padding-left: 1.2rem; line-height: 1.6;">
      <li><strong>Problem statement:</strong> Identify the single soil feature that best predicts crop type due to testing cost constraints.</li>
      <li><strong>Dataset size:</strong> 2,200 soil samples across 22 crops</li>
      <li><strong>Models tested:</strong> Decision Trees, Gradient Boosting</li>
      <li><strong>Evaluation metrics:</strong> Precision, Recall</li>
      <li><strong>Final model performance:</strong> Maintained 85% accuracy using only 1 distinct feature</li>
    </ul>
    <a href="https://github.com/anshid" target="_blank" class="glow-text" style="font-weight: 600; margin-top: auto; display: inline-block;">View on GitHub &rarr;</a>
  </div>

  <!-- Featured Project 3 -->
  <div class="modern-card">
    <h3 style="font-size: 1.25rem; margin-bottom: 0.5rem;">OpenAI API Travel Assistant</h3>
    <div class="card-tags" style="margin-bottom: 1rem;">
      <span class="tag">OpenAI API</span>
      <span class="tag">Prompt Engineering</span>
    </div>
    <ul style="font-size: 0.95rem; color: var(--text-muted); margin-bottom: 1.5rem; padding-left: 1.2rem; line-height: 1.6;">
      <li><strong>Problem statement:</strong> Design deterministic structured responses for localized Parisian tourist queries.</li>
      <li><strong>Dataset size:</strong> Dynamic API-fed conversational queries</li>
      <li><strong>Models tested:</strong> GPT-3.5-Turbo, GPT-4</li>
      <li><strong>Evaluation metrics:</strong> Response latency, JSON Schema adherence</li>
      <li><strong>Final model performance:</strong> 100% successful schema adherence</li>
    </ul>
    <a href="https://github.com/anshid" target="_blank" class="glow-text" style="font-weight: 600; margin-top: auto; display: inline-block;">View on GitHub &rarr;</a>
  </div>
</div>

<div class="section-title">
  <h2 style="color: var(--accent-primary);">ML System Design</h2>
</div>

<div style="background: var(--bg-secondary, #1a1a2e); padding: 2rem; border-radius: 12px; margin-bottom: 4rem; border: 1px solid var(--glass-border); overflow-x: auto;">
  <p style="font-size: 1.05rem; color: var(--text-main); margin-bottom: 1.5rem; text-align: center;">
    My approach to building scalable Machine Learning solutions encompasses the entire lifecycle.
  </p>
  
  <div class="mermaid" style="display: flex; justify-content: center; margin: 2rem 0;">
    graph TD
    %% Data Pipeline
    subgraph DP [Data Pipeline]
      A[Raw Data] --> B[Data Validation]
      B --> C[Feature Engineering]
      C --> D[(Feature Store)]
    end
    
    %% Training Pipeline
    subgraph TP [Training Pipeline]
      D --> E[Model Experimentation]
      E --> F[Hyperparameter Tuning]
      F --> G[Distributed Training]
    end
    
    %% Evaluation
    subgraph EV [Evaluation]
      G --> H{Validation Gates}
      H -->|Pass| I[Model Registry]
      H -->|Fail/Retrain| E
    end
    
    %% Deployment Architecture
    subgraph DA [Deployment Architecture]
      I --> J[CI/CD Flow]
      J --> K[Container / Docker]
      K --> L[Inference Endpoint]
      L --> M[Monitoring / Drift]
    end
    
    %% Styling
    classDef default fill:#1e1e2f,stroke:#4a4e69,stroke-width:2px,color:#f8f9fa;
    classDef subgraphStyle fill:none,stroke:#9d4edd,stroke-width:2px,stroke-dasharray: 5 5;
    
    style DP fill:none,stroke:#00b4d8,stroke-width:2px,stroke-dasharray: 5 5,color:#fff;
    style TP fill:none,stroke:#fb8500,stroke-width:2px,stroke-dasharray: 5 5,color:#fff;
    style EV fill:none,stroke:#ef233c,stroke-width:2px,stroke-dasharray: 5 5,color:#fff;
    style DA fill:none,stroke:#06d6a0,stroke-width:2px,stroke-dasharray: 5 5,color:#fff;
  </div>
</div>
<!-- Initialize Mermaid -->
<script type="module">
  import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
  mermaid.initialize({ startOnLoad: true, theme: 'dark', securityLevel: 'loose' });
</script>

<div class="section-title">
  <h2 style="color: var(--accent-primary);">GitHub Activity</h2>
</div>

<div style="display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap; margin-bottom: 4rem;">
  <img src="https://github-readme-stats.vercel.app/api?username=anshid&show_icons=true&theme=radical&hide_border=true&bg_color=1a1a2e&hide_rank=true" alt="Anshid's GitHub Stats" style="border-radius: 8px; max-width: 100%;">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=anshid&layout=compact&theme=radical&hide_border=true&bg_color=1a1a2e&hide=jupyter%20notebook" alt="Top Languages" style="border-radius: 8px; max-width: 100%;">
</div>

<div class="section-title">
  <h2 style="color: var(--accent-primary);">Teaching & Mathematical Foundations</h2>
</div>

<div class="modern-card" style="margin-bottom: 4rem; text-align: center;">
  <h3 style="font-size: 1.25rem; margin-bottom: 1rem;">Academic Rigor & Mentorship</h3>
  <p style="font-size: 1.05rem; color: var(--text-muted); margin-bottom: 1.5rem; line-height: 1.6;">
    With a solid academic foundation in advanced mathematics and teaching experience across diverse university courses, I specialize in translating complex theoretical concepts into practical intuition. My background ensures my machine learning systems are mathematically robust, optimizable, and carefully evaluated.
  </p>
  <a href="{{ '/teaching/' | relative_url }}" class="btn" style="padding: 0.8rem 1.5rem; border: 1px solid var(--accent-primary); color: var(--text-main);">View Teaching Portfolio</a>
</div>

<div style="text-align: center; padding: 4rem 1rem; border-top: 1px solid var(--glass-border); margin-top: 4rem;">
  <p style="color: var(--accent-primary); font-weight: 600; text-transform: uppercase; letter-spacing: 2px; margin-bottom: 1rem; font-size: 0.9rem;">Let's Connect</p>
  <h2 style="font-size: 2.5rem; margin-bottom: 1rem;">Interested in building ML systems with mathematical rigor?</h2>
  <p style="color: var(--text-muted); margin-bottom: 2rem; font-size: 1.2rem;">Let's collaborate.</p>
  <a href="mailto:anshidaboobackerk@gmail.com" class="btn btn-primary" style="padding: 1rem 2.5rem; font-size: 1.1rem; border-radius: 50px; text-transform: uppercase; letter-spacing: 1px;">Start a Conversation</a>
</div>