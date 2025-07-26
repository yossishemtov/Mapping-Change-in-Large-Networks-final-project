# 📊 Mapping Change in Large Networks

This project analyzes the structural evolution of large-scale academic citation networks over time.  
It uses graph embedding, semantic NLP, clustering, and advanced visualization to detect how scientific fields emerge, merge, split, or decline.

---

## 🧠 Key Features

- Semantic topic labeling with Sentence-BERT
- Node embedding with **GraphSAGE++** or **FastGCN**
- Scalable clustering using **MiniBatch KMeans**
- Dynamic tracking of cluster transitions between years
- Visualization via **Alluvial/Sankey Diagrams**
- GUI interface for running and configuring the system

---

## 🗂️ Project Structure

```bash
.
├── main_executor.py                   # Main orchestration script
├── requirements.txt                   # Dependency list
├── main_UI/                           # GUI for config and visualization
├── Clustering_algorithm/             # KMeans clustering logic
├── data_set_Processing/             # Data filtering + semantic preprocessing
├── vector_embeddings_generator/     # GraphSAGE++ & FastGCN trainers
├── Alluvial_Diagram_Generator/      # Sankey & Plotly-based visualizations
├── sintetic_data/                   # Testing with synthetic dataset
├── results/                         # Output diagrams (HTML)
└── utils/                           # Utility functions (embedding init, scoring)
 
```

---


### 📁 Project Location Inside ZIP

When downloading the project as a `.zip` file, the full source code is located inside:

```bash
phase b/Mapping-Change-in-Large-Networks-final-project_code/
```

Please make sure to navigate into this directory before proceeding with installation or running the system.


## 🚀 Getting Started

### 🐍 1. Set Up Python Virtual Environment (REQUIRED)

This project works best with Python **3.9–3.12**.

#### Option A: Using PyCharm
If you're using PyCharm:
1. Go to `Settings` → `Project` → `Python Interpreter`
2. Click **Add Interpreter** → **Virtualenv Environment**
3. Choose:
   - **Environment**: Generate new
   - **Base interpreter**: Python 3.12
   - **Location**: `.venv` inside the project folder
4. Click **OK** to create the environment

---

### 📦 2. Install Dependencies

```bash
pip install -r requirements.txt
```

Ensure:
- You are using the correct virtual environment
- `torch` and `torch-geometric` are installed
- You have internet access to download Sentence-BERT models

---

## 🖥️ Running the GUI

Simply launch the main executor:

```bash
python main_executor.py
```

A GUI will open with configuration options:

1. Set **year range** (e.g., 2000–2020)
2. Enter macro-categories (e.g., "AI, Biology, Physics")
3. Upload your dataset (.txt format)
4. Choose diagram type (Sankey / Plotly)
5. Set citation thresholds (Citing %, Cited Ratio)
6. Click **Run Analysis and Generate Diagram**

---

## 📄 Dataset Format

Input `.txt` file must include:

| Field           | Description                                 |
|-----------------|---------------------------------------------|
| `id`         | Unique identifier for the paper             |
| `year`       | Year of publication                         |
| `references` | List of paper IDs this paper cites          |
| `fos`        | List of fields of study (can be raw terms)  |

---

### 🧾 Using Preprocessed Dataset

The processed dataset was derived from the **Open Academic Graph (OAG v2.1)** and includes only selected papers after filtering by publication year and research domain.


A preprocessed version of the dataset is included in:

```bash
data_set_Processing/data_processed.jsonl
```

This file is the result of prior data filtering and semantic enrichment (macro-category assignment).  
You may use it directly for testing the pipeline **without uploading or processing raw input files via the GUI**.

To use it:
- Set `"enable_data_processing"` to `False` in the GUI, or skip the data preprocessing phase.
- The system will automatically load `data_processed.jsonl` as input for embedding and clustering.

---

## 🧪 Testing with Synthetic Data

You can test the pipeline using a built-in synthetic dataset:

```bash
sintetic_data/generate_sintetic_data.py
```

This generates structured `jsonl` files with known patterns to validate embeddings, clustering, and visualization.

---

## 🧰 Output Files

All generated diagrams are stored in the `results/` folder:

- `alluvial_diagram_<id>.html` – Sankey diagrams
- `plotly_diagram_<id>.html` – Interactive alluvial flows

Each stream represents a transition (split/merge/stable) between research clusters across time.

---

## ✨ Example Flow (Pipeline Steps)

> Executed in `main_executor.py`

- Load GUI config
- Filter raw data and assign macro-categories (Sentence-BERT)
- Build citation graph + initial embeddings
- Train GraphSAGE model
- Generate node embeddings
- Cluster nodes per year using MiniBatchKMeans
- Track cluster transitions across time (merges/splits)
- Visualize using Sankey / Plotly alluvial diagrams

---

## 👥 Authors & Acknowledgments

**Students:**  
- Shimron Ifrah 
- Yossi Shem-Tov 

**Supervisors:**  
- Dr. Renata Avros  
- Prof. Zeev Volkovich  

---

## 📘 License

This codebase is intended for educational and academic use only.  
Libraries used are under their respective open-source licenses.
