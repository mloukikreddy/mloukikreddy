<h1 align="center">Hi 👋, I'm Loukik Reddy Mekala</h1>
<h3 align="center">Final-Year AI Student · Data Analyst · Data Scientist · AI Engineer · ML Developer</h3>
<h4 align="center"><i>Build. Analyze. Deploy.</i></h4>

<p align="center">
  <a href="linkedin.com/in/mekala-loukik-reddy" target="_blank">
    <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/>
  </a>
  <a href="https://github.com/mloukikreddy" target="_blank">
    <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white"/>
  </a>
  <a href="mailto:mloukikreddy@gmail.com">
    <img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white"/>
  </a>
</p>

---

## 👨‍💻 About Me

- 🎓 B.Tech **Artificial Intelligence** · Anurag University, Hyderabad (CGPA: 8.07 · Graduating 2026)
- 🔍 Open to: **Data Analyst · Data Scientist · AI Engineer · Python Developer · ML Developer**
- 🛠️ I build end-to-end data products — raw data → EDA → ML models → deployed apps
- 📧 mloukikreddy@gmail.com · 📍 Hyderabad, India

---

## 🚀 Featured Projects

---

### 🤖 DocChat — Multi-Model RAG Document Chatbot

> *Python · FastAPI · LangChain · FAISS · sentence-transformers · Llama 3.3 · Gemini 2.0 · Cohere · DuckDuckGo · Docker · HuggingFace Spaces*

Upload any PDF, DOCX, PPTX, or TXT and **chat with it using 3 AI models simultaneously**. Built a complete RAG pipeline from scratch — ingestion, vector embeddings, semantic retrieval, parallel multi-LLM inference, and response fusion.

**How it works:**

```
User Uploads Document (PDF / DOCX / PPTX / TXT)
           ↓
   Text Extraction (pypdf, python-docx)
           ↓
   Split into 500-token chunks (50-token overlap)
           ↓
   Embed via all-MiniLM-L6-v2 (~90MB, runs locally)
           ↓
   Store in FAISS vector database (per-session UUID)
           ↓
   User asks a question
           ↓
   Semantic search → Top 4 relevant chunks
         +
   DuckDuckGo web search → Top 3 results
           ↓
   Combined context → 3 LLMs in parallel (ThreadPoolExecutor)
   [Llama 3.3]  [Gemini 2.0 Flash]  [Cohere Command-R]
           ↓
   Groq/Llama merges all 3 → Final answer returned
```

**Key design decisions:**
- **Session isolation:** UUID per user → separate FAISS index → no cross-user data leakage
- **Chat history:** Last 5 turns injected into every prompt → follow-up questions work correctly
- **Lazy loading:** Models load on first request, not startup → fits within Render's 512MB RAM limit
- **$0 cost:** 100% free APIs + local embeddings — no OpenAI, no Pinecone

| Layer | Technology |
|---|---|
| Backend | FastAPI · Python |
| RAG Framework | LangChain |
| Vector Store | FAISS |
| Embeddings | sentence-transformers (all-MiniLM-L6-v2) |
| LLMs | Groq/Llama 3.3 · Gemini 2.0 Flash · Cohere Command-R |
| Web Search | DuckDuckGo |
| Frontend | HTML · CSS · Vanilla JS |
| Deployment | Docker · HuggingFace Spaces |

- 🔗 [GitHub Repository](https://github.com/mloukikreddy/docchat)
- 🌐 [Live Demo — HuggingFace Spaces](https://huggingface.co/spaces/loukikreddy22/docchat)

---

### 🩺 Multi-Modal Diabetic Retinopathy Detection

> *Python · DenseNet121 · Fusion Layer · LightGBM · TensorFlow/Keras · Jupyter*

Advanced multi-modal deep learning system for DR severity classification. Dual DenseNet streams process two image modalities independently, outputs fused via a custom fusion layer, then passed to a classical ML classifier for final prediction.

**How it works:**

```
Fundus Image  +  OCT Retinal Image
      ↓                  ↓
 DenseNet Stream A   DenseNet Stream B
 (spatial features)  (texture features)
      ↓                  ↓
      └──── Fusion Layer ────┘
                  ↓
       Combined feature vector
                  ↓
       ML Classifier (LightGBM)
                  ↓
   5-class DR severity prediction:
   [Normal] [Mild] [Moderate] [Severe] [Proliferative DR]
                  ↓
   Evaluation: Accuracy · Precision · Recall · F1 · Confusion Matrix
```

**Key design decisions:**
- **Dual DenseNet streams:** Each modality (Fundus vs OCT) carries different clinical signals — parallel streams capture both independently before fusion
- **Fusion Layer:** Concatenates feature vectors from both streams → richer representation than single-stream
- **DenseNet over VGG:** Dense connections reuse features across layers → better gradient flow, more efficient on small medical datasets
- **LightGBM classifier head:** Faster inference + interpretable feature importance vs. full softmax DNN head

| Layer | Technology |
|---|---|
| Stream A | DenseNet (Fundus images) |
| Stream B | DenseNet121 (OCT images) |
| Fusion | Custom Fusion Layer |
| Classification | LightGBM |
| Framework | TensorFlow · Keras |
| Environment | Google Colab · Jupyter |

- 🔗 [GitHub Repository](https://github.com/mloukikreddy/multi-modal-Diabetic-Retinopathy)
- [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1cicYcsZg32RakChF-KBpIsVJRpRTVKcM?usp=sharing)

---

### 📊 E-Commerce Sales Analysis & Dashboard

> *Python · SQL · SQLite · Pandas · Excel · Power BI · Olist Dataset*

End-to-end analytics pipeline on **real Brazilian e-commerce transactions (Olist dataset)** — from raw CSV ingestion to a 3-page interactive Power BI dashboard with actionable business KPIs.

**How it works:**

```
Raw Olist Dataset (Kaggle · multi-table relational data)
           ↓
   Excel → initial preprocessing & data validation
           ↓
   Python (Pandas) → data cleaning, merging tables,
   feature engineering (delivery time, review mapping)
           ↓
   SQLite (ecommerce.db) → structured storage
   SQL queries → KPI aggregations:
   [Total Revenue] [Total Orders] [AOV]
   [Avg Delivery Time] [Review Scores]
           ↓
   EDA Notebook (ecommerce_eda.ipynb)
   → Monthly revenue trends
   → Payment method distribution
   → Delivery performance vs. review score correlation
           ↓
   Power BI → 3-page interactive dashboard
   [Page 1: Executive Overview]
   [Page 2: Detailed Insights]
   [Page 3: Advanced Analytics]
```

**Key design decisions:**
- **SQLite as warehouse:** Lightweight, file-based DB — no server setup, reproducible, commitable to repo as `ecommerce.db`
- **Multi-page Power BI:** Separate pages for exec summary, product drill-down, and delivery analytics — prevents overcrowding a single canvas
- **Delivery-satisfaction correlation:** Surfaced that delivery delays directly tank review scores — key actionable insight for business

| Layer | Technology |
|---|---|
| Data Storage | SQLite · Excel |
| EDA & Cleaning | Python · Pandas |
| SQL Analysis | SQLite queries |
| Dashboard | Power BI (3-page) |
| Dataset | Olist Brazilian E-Commerce (Kaggle) |

- 🔗 [GitHub Repository](https://github.com/mloukikreddy/ecommerce-sales-analysis)

---

### 🩻 Diabetic Retinopathy Detection — Research Notebook

> *Python · VGG16 · LightGBM · TensorFlow/Keras · OpenCV · Google Colab · Kaggle*

Hybrid ML pipeline for automated DR screening from retinal fundus images (~5,000 images). Pretrained CNN for feature extraction + gradient boosting classifier — high accuracy at low inference cost.

**How it works:**

```
Retinal Fundus Images (~5,000 images · Kaggle dataset)
           ↓
   Preprocessing: resize → normalize → augmentation
           ↓
   VGG16 (pretrained on ImageNet)
   → Remove top classification layers
   → Extract deep feature vectors from conv layers
           ↓
   Feature vectors → LightGBM classifier
           ↓
   5-class DR severity prediction
           ↓
   Accuracy: 99%+ · Sample confidence: 99.50%
   Evaluation: Precision · Recall · F1 · Confusion Matrix
```

**Key design decisions:**
- **Hybrid DL + ML:** VGG16 extracts rich spatial features; LightGBM classifies faster + more interpretably than a full DNN softmax head — better for small medical datasets
- **Transfer learning:** ImageNet pretrained weights give strong edge detection and texture features critical for retinal vessel analysis
- **Kaggle API ingestion:** Dataset too large to commit → Kaggle API setup included for fully reproducible Colab runs

| Layer | Technology |
|---|---|
| Feature Extraction | VGG16 (TensorFlow/Keras) |
| Classification | LightGBM |
| Preprocessing | OpenCV · NumPy |
| Evaluation | Scikit-learn · Matplotlib · Seaborn |
| Environment | Google Colab · Jupyter |

- 🔗 [GitHub Repository](https://github.com/mloukikreddy/Diabetic-Retinopathy)
- [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mloukikreddy/Diabetic-Retinopathy/blob/main/Diabetic_Retinopathy_.ipynb)

---

### 🌦️ Weather App

> *Node.js · Express.js · HTML · CSS · JavaScript · Pug · Weather API · Render*

Full-stack real-time weather application. Search any city → get live temperature, humidity, wind speed, and conditions instantly. Deployed and live on Render.

**How it works:**

```
User enters city name in browser UI
           ↓
   Express.js server receives GET request
           ↓
   Server-side call to Weather API (live data)
           ↓
   API returns JSON:
   [temp] [humidity] [wind speed] [condition]
           ↓
   Express parses → renders via Pug template
           ↓
   Dynamic HTML returned → browser displays live data
```

**Key design decisions:**
- **Server-side API call:** API key stays on Node/Express server, never exposed to client browser — prevents key theft
- **Pug server-side rendering:** Fast initial load, no client-side JS framework overhead for a simple data-display app
- **Render deployment:** Free tier persistent process → app stays live at stable URL

| Layer | Technology |
|---|---|
| Backend | Node.js · Express.js |
| Templating | Pug |
| Frontend | HTML · CSS · JavaScript |
| Data Source | Weather API (live) |
| Deployment | Render |

- 🔗 [GitHub Repository](https://github.com/mloukikreddy/weather-app-main)
- 🌐 [Live Demo](https://weather-app-main-5fjm.onrender.com/)

---

### 📍 Loc88r — Location Review App

> *MEAN Stack · MongoDB · Express.js · Angular · Node.js · Render*

Full-stack location discovery and review platform on the MEAN stack. Users explore places, sign in securely, and add reviews. Live on Render.

**How it works:**

```
User visits Home page
           ↓
   Angular frontend → HTTP call to Express REST API
           ↓
   Express routes → controllers → MongoDB queries
           ↓
   MongoDB returns location/review documents
           ↓
   Angular renders dynamic UI (no full page reload)
           ↓
   Auth flow: Sign In → session token → write access
           ↓
   Authenticated user submits review
   → POST /api/reviews → persisted in MongoDB
```

**Key design decisions:**
- **MEAN stack:** Single language (JavaScript) across frontend, backend, and DB layer → faster dev, consistent data models
- **REST API-first:** Separate `app_api/` layer decouples backend from frontend → reusable, testable
- **MongoDB:** Schema-flexible NoSQL fits location/review data with variable fields — no rigid table migrations

| Layer | Technology |
|---|---|
| Frontend | Angular |
| Backend | Node.js · Express.js |
| Database | MongoDB |
| Auth | Session-based |
| Deployment | Render |

- 🔗 [GitHub Repository](https://github.com/mloukikreddy/loc88r)
- 🌐 [Live Demo](https://loc88r-ms2x.onrender.com)

---

## 🛠️ Tech Stack

**Data & Analytics**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat&logo=mysql&logoColor=white)
![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![Excel](https://img.shields.io/badge/Excel-217346?style=flat&logo=microsoftexcel&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white)

**Machine Learning & AI**

![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat&logo=tensorflow&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-D00000?style=flat&logo=keras&logoColor=white)
![LightGBM](https://img.shields.io/badge/LightGBM-9ACD32?style=flat)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=flat&logo=scikitlearn&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat)
![HuggingFace](https://img.shields.io/badge/HuggingFace-FFD21E?style=flat&logo=huggingface&logoColor=black)
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=flat&logo=opencv&logoColor=white)

**Web & Deployment**

![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=flat&logo=flask&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat&logo=mongodb&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)

---

## 💼 I'm Open To

| Role | What I bring |
|------|-------------|
| **Data Analyst** | SQL · Power BI · Python EDA · Excel · business KPI dashboards |
| **Data Scientist** | ML pipelines · LightGBM · feature engineering · model evaluation |
| **AI Engineer** | RAG · LangChain · LLM APIs · FAISS · FastAPI · multi-model orchestration |
| **Python Developer** | FastAPI · REST APIs · data pipelines · async · ML integration |
| **ML Developer** | CNN · DenseNet · DL (TF/Keras) · medical imaging · production deployment |

---

## 📈 GitHub Stats

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=mloukikreddy&show_icons=true&theme=tokyonight&hide_border=true" width="47%"/>
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=mloukikreddy&layout=compact&theme=tokyonight&hide_border=true" width="47%"/>
</p>

---

## 📫 Connect

- 📧 Email: [mloukikreddy@gmail.com](mailto:mloukikreddy@gmail.com)
- 💼 LinkedIn: [mekala-loukik-reddy-a717b4287](https://linkedin.com/in/mekala-loukik-reddy-a717b4287)
- 🐙 GitHub: [mloukikreddy](https://github.com/mloukikreddy)

---

<p align="center"><i>"Build. Analyze. Deploy."</i></p>
