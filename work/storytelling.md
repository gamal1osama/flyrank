# Tell the Story — ML-12 Communication Companion

This document provides the three delivery cuts of the Capstone Research Paper (**Predictive Content Refresh: Client-Grouped Evaluation of an Organic Search Early-Warning Ranker**), adapting the same underlying empirical evidence for different audiences.

---

## 1. Case Study Framing: The FlyRank Content Problem

### The Operational Challenge
Enterprise content publishing portfolios host tens of thousands of indexed web pages. Over time, search ranking volatility and competitive displacement cause articles to experience organic traffic decay. Because human editorial teams operate under strictly bounded bandwidth—typically 20 to 50 comprehensive content refreshes per monthly sprint—editors face an acute triage problem: **Which specific articles should be refreshed first to protect organic traffic?**

### The Failure of Naive Rules
Traditional industry SEO relies on static calendar heuristics (such as flagging any article updated $>90$ days ago). In our empirical audit of 30,000 enterprise articles across 32 client domains, this heuristic baseline exhibited a **76.0% false-alarm rate**: only 24% of pages in the top-50 heuristic queue actually experienced traffic decline. In practice, content teams following naive staleness rules squander three out of every four rewrite hours on healthy or growing content while neglecting genuinely vulnerable pages.

### The Machine Learning Solution
By framing content refresh as an operational ranking task, we trained a Random Forest model on pre-decision search signals (impression frequency, SERP position volatility, query stability, and content depth) under a strict client-holdout validation design. The resulting composite **Action Playbook Priority Score** lifts review precision from **24.0% to 84.0%** at $K=50$ on held-out client domains—a **3.5× improvement** that catches 42 genuinely decaying pages per 50-article batch instead of only 12.

---

## 2. Five-Minute Live Showcase Demo Script

*Designed for the Week 8 Showcase presentation (1 minute per block, strictly timed).*

- **Minute 1: The Bottleneck & The Problem**
  - "In enterprise publishing, websites maintain 30,000+ indexed articles, but editors can only refresh 30 to 50 URLs a month. Common industry advice says: *'Update anything older than 90 days.'* On our enterprise dataset, that rule failed: 76% of flagged articles were actually stable or growing. Teams waste 3 out of 4 writer hours on the wrong pages."
- **Minute 2: Data Architecture & Leakage Defense**
  - "Our research utilized FlyRank's 78.8-million-row warehouse release spanning 104 domains, evaluating a 30,000-article panel across 32 enterprise clients. We enforced strict data integrity: target-defining metrics (`trend_direction`, `trend_pct`) were quarantined to eliminate target leakage, and evaluation was partitioned into a **Client-Holdout Split** so client domain authority never leaked across training and test sets."
- **Minute 3: The Model & The Evidence**
  - "We compared linear baselines, transparent decision trees, and a Random Forest ensemble against the heuristic rule. Evaluated strictly on 2,325 held-out URLs from unseen client domains, the Random Forest model achieved **90.0% Precision@20** and **84.0% Precision@50**, compared to the baseline's **24.0%**—an absolute improvement of +60 percentage points."
- **Minute 4: The Action Playbook & Guardrails**
  - "A probability score isn't enough for writers. We translated model probabilities into an actionable playbook with deterministic reason codes: `thin_visible_content` for expansion, `low_ctr_striking_distance` for snippet optimization, and `page_one_decay_risk` for factual refreshes. We established strict No-Go anti-patterns: never automate rewriting with unverified LLMs, and never modify content with active upward momentum."
- **Minute 5: Deployment & Honest Boundaries**
  - "The research paper and interactive playbook are live at [https://gamal1osama.github.io/flyrank/](https://gamal1osama.github.io/flyrank/). In adherence to honest scientific framing, we emphasize that this is a decision-support ranker predicting observational risk, not a causal guarantee of traffic recovery. Thank you."

---

## 3. Two Shareable Cuts

### Cut A: Social Media Post (LinkedIn / X / Tech Community)
> **Why "update content older than 90 days" wastes 76% of editorial effort.**
>
> In enterprise SEO, managing editors face an acute bottleneck: portfolios have 30,000+ articles, but teams can only refresh 30 to 50 URLs a month. The common rule—updating pages purely based on calendar age—fails because staleness alone does not cause ranking collapse.
>
> As my Capstone for the FlyRank Applied ML Internship, I built an early-warning organic search decay ranker across a 78.8M-row search warehouse. 
>
> 🔍 **Key Findings:**
> • Evaluated on held-out enterprise client domains (zero cross-domain leakage), a Random Forest ranker achieved **84.0% Precision@50** vs. the heuristic rule’s **24.0%** (a **3.5×** precision multiplier).
> • In a 50-article sprint, this means editors catch **42 genuinely decaying pages** instead of only 12.
> • Operationalized into an editorial playbook with deterministic reason codes (`thin_visible_content`, `low_ctr_striking_distance`) and strict automation guardrails (e.g. never touch growing content).
>
> 📄 Live interactive research paper: https://gamal1osama.github.io/flyrank/
> 💻 Full reproducible code & receipts: https://github.com/gamal1osama/flyrank
> 
> #MachineLearning #AppliedAI #SearchIntelligence #DataScience #SEO #Python

---

### Cut B: Three-Sentence Employer-Facing Summary
> *Engineered an end-to-end organic search decay early-warning ranker across a 78.8M-row search intelligence warehouse covering 104 enterprise domains.*  
> *Designed a leak-free client-holdout validation framework proving that Random Forest ensemble scoring achieves 84.0% Precision@50 on unseen client portfolios, out-predicting traditional heuristic baselines by 3.5×.*  
> *Translated continuous probabilistic outputs into an operational editorial action playbook with deterministic reason codes, volume noise floors, and strict automation guardrails.*
