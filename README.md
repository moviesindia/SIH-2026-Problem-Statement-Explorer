# SIH 2026 Problem Statement Explorer

Interactive exploration portal, multi-tag search, automated data cleaning pipeline, and comprehensive JSON/CSV dataset for all **226 Problem Statements** released for **Smart India Hackathon 2026 (SIH 2026)**.

The repository is organized into two main folders:

* **`sih2026-problem-statement/`** — Complete SIH 2026 problem statement explorer, dataset, scraper, and web application.
* **`Shortlisted/`** — Problem statements shortlisted for further evaluation and team discussion.

---

## Repository Structure

```text
.
├── Shortlisted/
│   └── # Shortlisted SIH 2026 problem statements
│
└── sih2026-problem-statement/
    ├── index.html                        # Modern Flat Design web portal
    ├── style.css                         # High-contrast CSS system tokens & responsive layouts
    ├── app.js                            # Search, multi-tag filter engine, and modal controller
    ├── sih2026_problem_statements.json   # Cleaned & normalized JSON dataset (226 statements)
    ├── sih2026_problem_statements.csv    # Cleaned CSV export for data analysis & Excel
    ├── scrape_sih.py                     # Canonical scraper & data normalizer
    ├── logo.png                          # SIH logo
    ├── favicon.ico / favicon-*.png       # Multi-resolution favicons
    ├── package.json                      # Project metadata
    └── README.md                         # Documentation
```

### Folder Overview

### `Shortlisted/`

Contains the problem statements that have been **shortlisted from the complete SIH 2026 dataset** for further analysis, comparison, discussion, and final team selection.

### `sih2026-problem-statement/`

Contains the complete **SIH 2026 Problem Statement Explorer**, including:

* All 226 official problem statements
* Search and filtering interface
* Cleaned JSON and CSV datasets
* Automated scraping and data normalization pipeline
* Problem statement detail viewer
* Export functionality

---

# Dataset Overview & Statistics

**Total Problem Statements:** 226 (`SIH26001` – `SIH26226`)

* **Software:** 172
* **Hardware:** 54

## Top Themes

| Theme                                     | Count |
| ----------------------------------------- | ----: |
| Miscellaneous                             |    38 |
| Smart Automation                          |    31 |
| Disaster Management                       |    29 |
| Blockchain & Cybersecurity                |    22 |
| MedTech / BioTech / HealthTech            |    14 |
| Smart Education                           |    13 |
| Agriculture, FoodTech & Rural Development |    12 |
| Space Technology                          |    11 |
| Robotics and Drones                       |    10 |
| Transportation & Logistics                |     8 |

## Top Ministries / Organizations

| Ministry / Organization                                  | Count |
| -------------------------------------------------------- | ----: |
| AICTE                                                    |    34 |
| Ministry of Earth Sciences / MoES                        |    30 |
| National Technical Research Organisation / NTRO          |    23 |
| ISRO                                                     |    11 |
| Ministry of Home Affairs                                 |    11 |
| Ministry of Rural Development                            |    10 |
| Ministry of Consumer Affairs, Food & Public Distribution |    10 |
| Government of Maharashtra                                |     9 |
| Ministry of Social Justice and Empowerment / MoSJE       |     8 |
| DRDO                                                     |     7 |

---

# Quick Start

## 1. Launch the Web Explorer Locally

Navigate to the `sih2026-problem-statement/` folder and serve the repository with any local HTTP server.

### Python 3

```bash
cd sih2026-problem-statement
python3 -m http.server 8080
```

### Node.js

```bash
cd sih2026-problem-statement
npx serve .
```

Open the application in your browser at the local server address.

---

## 2. Run the Data Pipeline & Cleaner

From the `sih2026-problem-statement/` directory:

```bash
# Clean & normalize the local dataset
python3 scrape_sih.py --clean-only
```

Or fetch and parse directly from the official portal:

```bash
python3 scrape_sih.py
```

---

# JSON Schema Format

Each problem statement entry in `sih2026_problem_statements.json` follows this structure:

```json
{
  "id": "SIH26001",
  "numeric_id": 26001,
  "serial_no": 1,
  "title": "AI-Based early warning and landslide Risk Monitoring System in NER",
  "organization": "Ministry of Development of North Eastern Region (MDoNER)",
  "department": "Ministry of Development of North Eastern Region (MDoNER)",
  "category": "Software",
  "theme": "Disaster Management",
  "submitted_ideas": {
    "count": 0,
    "capacity": 500,
    "raw": "0/500"
  },
  "deadline": "20 September 2026",
  "youtube_link": null,
  "dataset_info": null,
  "contact_info": null,
  "external_links": [],
  "sections": {
    "background": {
      "title": "Background",
      "content": "The North Eastern Region (NER) frequently faces landslides..."
    },
    "description": {
      "title": "Description",
      "content": "This problem statement proposes the development of..."
    },
    "expected_solution": {
      "title": "Expected Solution",
      "content": "A scalable AI-based software platform with..."
    }
  },
  "description": "**Background:**\n\nThe North Eastern Region (NER) frequently faces landslides...",
  "modal_id": "ViewProblemStatement26001"
}
```

---

# Clean Export Schema

When exporting selected or filtered statements via the **Download / Export** menu, the JSON format produces a clean schema without scraper bloat:

```json
{
  "id": "SIH26158",
  "title": "Single-Pass Drone Video to Accurate 3D Model Generation System",
  "category": "Software",
  "theme": "Robotics and Drones",
  "organization": "National Technical Research Organisation (NTRO)",
  "department": "National Technical Research Organisation (NTRO)",
  "submissions": "0/500",
  "deadline": "20 September 2026",
  "description": "...",
  "dataset_info": "...",
  "external_links": [],
  "sections": { ... }
}
```

---

# Loading the Dataset in Python

```python
import json
import pandas as pd

# Load JSON
with open(
    'sih2026_problem_statements.json',
    'r',
    encoding='utf-8'
) as f:
    data = json.load(f)

problem_statements = data['problem_statements']

print(f"Loaded {len(problem_statements)} problem statements")

# Convert to Pandas DataFrame
df = pd.DataFrame(problem_statements)

# Filter for AI/ML related statements
ai_statements = [
    p for p in problem_statements
    if 'AI' in p['title']
    or 'machine learning' in p['description'].lower()
]

print(f"Found {len(ai_statements)} AI/ML statements")
```

---

# Web Explorer Features

### Flat Design System

High-contrast, card-based interface with geometric typography.

### Mobile Responsive

Slide-out filter drawer, sticky action bar, and responsive modal actions.

### Search Scopes

Filter across:

* Full Text
* Title Only
* Description & Solution
* Organization
* Problem ID

### Technology Tag Pills

The explorer provides technology-oriented filtering for:

* AI/ML
* Computer Vision
* NLP/LLM
* GIS/Satellite
* IoT
* Blockchain
* Robotics
* Mobile Apps
* Cloud
* HealthTech
* AgriTech
* Cybersecurity

### 1-Click Copy as Markdown

Copies a problem statement as a formatted GitHub Markdown document containing metadata and structured sections.

### Clean Export Engine

Export filtered or selected subsets to:

* JSON
* CSV

with sanitized and analysis-friendly fields.

### Problem Detail Modal

Tabbed problem statement view featuring:

* Full Description
* Structured Sections
* Datasets & References

---

# Shortlisted Problem Statements

The **`Shortlisted/`** folder contains the problem statements selected from the full dataset for focused evaluation.

The recommended workflow is:

```text
All 226 SIH 2026 Problem Statements
                ↓
     Explore & Filter using
   sih2026-problem-statement/
                ↓
      Shortlist relevant ideas
                ↓
           Shortlisted/
                ↓
       Compare & Evaluate
                ↓
        Final Problem Statement
```

This separation keeps the **complete official dataset and exploration tools** independent from the **team's curated shortlist**.

---

# Project Purpose

This repository is designed to make the SIH 2026 problem statements easier to:

* Explore
* Search
* Filter
* Analyze
* Compare
* Shortlist
* Export
* Use for further solution development

The complete dataset serves as the source for exploration, while the `Shortlisted/` directory provides a focused working set for problem selection.

---

# License / Usage

Refer to the repository and source portal terms for applicable usage, attribution, and redistribution requirements.
