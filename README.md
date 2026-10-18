<h1 align="center">Dimitar Karaskakovski</h1>

<p align="center">
  <b>Founder &amp; AI Engineer</b> at <a href="https://usekaras.com">Karas</a> &nbsp;·&nbsp; B.Sc. Artificial Intelligence student at JKU Linz
</p>

<p align="center">
  <a href="https://usekaras.com"><img src="https://img.shields.io/badge/usekaras.com-live-1E3A5F?style=for-the-badge" alt="usekaras.com"/></a>
  <a href="https://www.linkedin.com/in/dimitar-karaskakovski"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/></a>
  <a href="mailto:dimitarkaraskakovski92@gmail.com"><img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"/></a>
  <img src="https://img.shields.io/badge/Linz,_Austria-555555?style=for-the-badge&logo=googlemaps&logoColor=white" alt="Linz, Austria"/>
</p>

---

I'm an Artificial Intelligence student at Johannes Kepler University Linz who builds machine-learning systems and measures them honestly.

I founded **Karas**, an AI support agent for e-commerce that is live in production, and designed its retrieval, evaluation and safety logic. I also build classical ML and deep-learning projects with leakage-free evaluation. The work I care most about is what decides whether a model can be trusted: how it's evaluated, where it fails, and what stops it from saying the wrong thing.

---

## Featured: Karas — AI customer support, grounded in your help centre

<p align="center">
  <a href="https://usekaras.com"><img src="assets/karas-cited-answer.png" width="480" alt="Karas answering a question with a citation to the source article"/></a>
</p>

**[usekaras.com](https://usekaras.com)** · Aug 2026 – present. Karas answers customer questions from a store's help centre and links the article behind each answer. It refuses rather than guesses, and it hands off to a human when it can't help. Clients install it with one `<script>` tag, and the demo on the landing page is the live product.

I designed the retrieval, evaluation and safety logic. I built the widget, servers and deployment working with a coding agent (Claude Code).

<div align="center">

<table>
<tr>
<td align="center"><b>0.85</b><br/><sub>answer factuality on a<br/>6,221-article benchmark</sub></td>
<td align="center"><b>52% → 83%</b><br/><sub>right article in the top 5,<br/>keyword-only vs. vector-only</sub></td>
<td align="center"><b>4×</b><br/><sub>faster retrieval, with<br/>no loss in accuracy</sub></td>
<td align="center"><b>6.3 s → 1.8 s</b><br/><sub>reranking time with<br/>parallel batches</sub></td>
</tr>
</table>

</div>

**What I designed**

- **Hybrid retrieval.** Keyword (BM25) and vector search (Voyage AI embeddings) combined with weighted reciprocal rank fusion, plus LLM query rewriting and reranking. On their own, vector search found the right article in the top 5 results 83% of the time vs. 52% for keyword search; production runs a weighted hybrid of both. Moving the fusion step into the database made retrieval 4× faster with no loss in accuracy. Scoring rerank candidates in parallel batches cut reranking from 6.3 s to 1.8 s.
- **Evaluation.** Every change is measured on the 6,221-article [WixQA](https://huggingface.co/datasets/Wix/WixQA) benchmark (hit@k, MRR, LLM-as-judge factuality). I found that the LLM grader gave full marks to 189 of 200 answers, even when the right article was never retrieved. I fixed it by grading against reference answers only.
- **Safety checks.** Rule-based guardrails block answers without a source and stop the agent from promising refunds or claiming actions it can't take.

**What it ships with:** an embeddable widget, multi-tenant API keys bound to each client's website, per-client rate limiting, handoff to a human through the client's helpdesk, and CI/CD to a self-hosted server.

<p>
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white"/>
  <img src="https://img.shields.io/badge/OpenAI-412991?style=flat-square&logo=openai&logoColor=white"/>
  <img src="https://img.shields.io/badge/Voyage_AI-1E3A5F?style=flat-square"/>
  <img src="https://img.shields.io/badge/MongoDB_Vector_Search-47A248?style=flat-square&logo=mongodb&logoColor=white"/>
  <img src="https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white"/>
  <img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white"/>
  <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white"/>
</p>

<sub>The source is private because Karas is a commercial product. I'm happy to walk through the code and architecture in an interview.</sub>

---

## Machine Learning Projects

### [Satellite Terrain Classification](https://github.com/dimitar-sudo/satelite_image_classification)

<a href="https://github.com/dimitar-sudo/satelite_image_classification"><img src="https://raw.githubusercontent.com/dimitar-sudo/satelite_image_classification/HEAD/docs/app_screenshot.png" width="100%" alt="Satellite terrain classification web app"/></a>

A VGG-style CNN that I designed and trained **from scratch in PyTorch** (3.3M parameters, no pretrained weights). It classifies Sentinel-2 satellite tiles into 10 land-use classes and is served through an interactive Shiny web app.

- **96.93% test accuracy**, macro-F1 0.969, Cohen's κ 0.966 on a held-out split never used for training or model selection
- Flips and rotations as augmentation, since satellite images have no fixed "up". Most remaining errors are between similar-looking crop and vegetation types
- A Shiny web app classifies an uploaded tile in **about 3 ms on a CPU**

<img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white"/> <img src="https://img.shields.io/badge/Computer_Vision-5C3EE8?style=flat-square"/> <img src="https://img.shields.io/badge/Shiny-1A162D?style=flat-square"/> <img src="https://img.shields.io/badge/pytest_+_CI-0A9EDC?style=flat-square&logo=pytest&logoColor=white"/>

### [Sound Event Detection](https://github.com/dimitar-sudo/sound_event_detection_system)

<a href="https://github.com/dimitar-sudo/sound_event_detection_system"><img src="https://raw.githubusercontent.com/dimitar-sudo/sound_event_detection_system/HEAD/docs/figures/demo_timeline.png" width="100%" alt="Frame-level sound event detections on a test recording"/></a>

Detects 15 household sounds (running water, footsteps, a door closing) second by second in 3,656 recordings from 408 people. The model is evaluated on **people it has never heard**.

- **Test PR-AUC 0.62 against 0.06 for guessing** with gradient boosting (KNN 0.49, random forest 0.57), using per-class thresholds tuned on validation only
- Found and fixed mistakes in my first evaluation: the same person's recordings were in both training and test data, which inflated the scores. It is now split by person and scored with PR-AUC instead of an inflated macro-F1
- CLI package with resumable sweeps, cached intermediates, and a README generated from saved results

<img src="https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white"/> <img src="https://img.shields.io/badge/Audio_ML-6E40C9?style=flat-square"/> <img src="https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white"/> <img src="https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white"/> <img src="https://img.shields.io/badge/matplotlib-11557C?style=flat-square"/> <img src="https://img.shields.io/badge/pytest_+_CI-0A9EDC?style=flat-square&logo=pytest&logoColor=white"/>

---

## Tech Stack

| | |
|---|---|
| **Machine Learning** | <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white"/> <img src="https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white"/> <img src="https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white"/> <img src="https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white"/> <img src="https://img.shields.io/badge/matplotlib-11557C?style=flat-square"/> <img src="https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white"/> |
| **LLMs & Retrieval** | <img src="https://img.shields.io/badge/RAG-1E3A5F?style=flat-square"/> <img src="https://img.shields.io/badge/Hybrid_search_(BM25_+_vector)-1E3A5F?style=flat-square"/> <img src="https://img.shields.io/badge/Reranking-1E3A5F?style=flat-square"/> <img src="https://img.shields.io/badge/LLM--as--judge_eval-1E3A5F?style=flat-square"/> <img src="https://img.shields.io/badge/OpenAI_API-412991?style=flat-square&logo=openai&logoColor=white"/> <img src="https://img.shields.io/badge/Voyage_AI-1E3A5F?style=flat-square"/> |
| **Languages & Tools** | <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white"/> <img src="https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white"/> <img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white"/> <img src="https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black"/> <img src="https://img.shields.io/badge/Claude_Code-D97757?style=flat-square&logo=claude&logoColor=white"/> |
| **Familiar with** | <img src="https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white"/> <img src="https://img.shields.io/badge/Pydantic-E92063?style=flat-square&logo=pydantic&logoColor=white"/> <img src="https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white"/> <img src="https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white"/> <img src="https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white"/> <img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white"/> <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white"/> <img src="https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask&logoColor=white"/> |

---

## Education

**Johannes Kepler University Linz**: B.Sc. Artificial Intelligence · Oct 2025 – Jul 2028 (expected) · GPA 1.56 (1.0 = best)

<sub>Relevant coursework: Machine Learning &amp; Pattern Classification · Hands-on AI · Statistics for AI · Mathematics for AI I &amp; II · Algorithms &amp; Data Structures · Programming in Python I &amp; II</sub>

---

## Earlier Work

**Freelance Python Developer on Upwork** (Sep – Dec 2025). I wrote a tool that turns an MBOX email archive into one readable HTML page per thread. It removes repeated quoted text but keeps the quotes the sender was replying to. The client wrote that I have *"extremely rare skills as a programmer"*.

Smaller full-stack Python projects from when I started out:

| Project | What it does | Stack |
|---|---|---|
| [Smart Scheduler AI](https://github.com/dimitar-sudo/smart-scheduler-ai) | Conversational appointment booking: spaCy NER extracts names, dates and times from chat, with conflict detection and a FullCalendar UI | Flask, spaCy, pytest, CI |
| [eBay Product Finder](https://github.com/dimitar-sudo/e-commerce-app) | Searches the eBay Browse API (OAuth2) with filtering, currency conversion, caching, rate limiting, and CSV/Excel/JSON export | Flask, REST APIs, pandas |
| [S&P 500 Data Collector](https://github.com/dimitar-sudo/sp500-scraper-app) · [demo](https://sp500-scraper-app.onrender.com) | Scrapes and cleans live S&P 500 data, with CSV export | Flask, BeautifulSoup, pandas |
| [Task Master](https://github.com/dimitar-sudo/task-master) · [demo](https://task-master-demo.onrender.com) | Task manager with categories, deadlines, search/sort and dark/light themes | Flask, SQLAlchemy, SQLite |

---

## Certifications &amp; Languages

<a href="https://verify.openedg.org/?id=sJsS.1tT0.54WA"><img src="https://img.shields.io/badge/PCAP-Certified_Associate_in_Python_Programming-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="PCAP"/></a>
<a href="https://www.credly.com/badges/f28a7373-aeda-4561-84a6-fdf8e7e8198a"><img src="https://img.shields.io/badge/Credly-Verify-FF6B00?style=for-the-badge&logo=credly&logoColor=white" alt="Verify on Credly"/></a>

<img src="https://img.shields.io/badge/English-C1_(certified)-2E5C8A?style=for-the-badge" alt="English C1"/> <img src="https://img.shields.io/badge/German-A2-555555?style=for-the-badge" alt="German A2"/>

---

<p align="center">
  <b>Open to AI / ML internships and working-student roles.</b> Based in Linz, Austria; open to on-site, hybrid or remote work.<br/>
  <a href="mailto:dimitarkaraskakovski92@gmail.com">dimitarkaraskakovski92@gmail.com</a> &nbsp;·&nbsp; <a href="https://www.linkedin.com/in/dimitar-karaskakovski">LinkedIn</a> &nbsp;·&nbsp; <a href="https://usekaras.com">usekaras.com</a>
</p>
