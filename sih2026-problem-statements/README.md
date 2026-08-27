SIH 2026 Problem Statement Explorer

Interactive exploration portal, multi-tag search, automated data cleaning pipeline, and comprehensive JSON/CSV dataset for all 226 Problem Statements released for Smart India Hackathon 2026 (SIH 2026).

Dataset Overview & Statistics
Total Problem Statements: 226 (SIH26001 – SIH26226)
Software: 172
Hardware: 54
Top Themes
Miscellaneous (38)
Smart Automation (31)
Disaster Management (29)
Blockchain & Cybersecurity (22)
MedTech / BioTech / HealthTech (14)
Smart Education (13)
Agriculture, FoodTech & Rural Development (12)
Space Technology (11)
Robotics and Drones (10)
Transportation & Logistics (8)
Top Ministries / Organizations
AICTE (34)
Ministry of Earth Sciences / MoES (30)
National Technical Research Organisation / NTRO (23)
ISRO (11)
Ministry of Home Affairs (11)
Ministry of Rural Development (10)
Ministry of Consumer Affairs, Food & Public Distribution (10)
Government of Maharashtra (9)
Ministry of Social Justice and Empowerment / MoSJE (8)
DRDO (7)
Repository Structure
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

Quick Start
1. Launch the Web Explorer Locally

Serve the repository with any local HTTP server:

# Python 3
python3 -m http.server 8080

# Or with Node.js
npx serve .


Open the application in your browser at the local server address.

2. Run the Data Pipeline & Cleaner
# Clean & normalize the local dataset
python3 scrape_sih.py --clean-only

# Or fetch and parse directly from the official portal
python3 scrape_sih.py

JSON Schema Format

Each problem statement entry in sih2026_problem_statements.json:

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

Clean Export Schema

When exporting selected or filtered statements via the Download / Export menu, the JSON format produces a clean schema without scraper bloat:

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

Loading the Dataset in Python
import json
import pandas as pd

# Load JSON
with open('sih2026_problem_statements.json', 'r', encoding='utf-8') as f:
    data = json.load(f)

problem_statements = data['problem_statements']
print(f"Loaded {len(problem_statements)} problem statements")

# Convert to Pandas DataFrame
df = pd.DataFrame(problem_statements)

# Filter for AI/ML related statements
ai_statements = [
    p for p in problem_statements
    if 'AI' in p['title'] or 'machine learning' in p['description'].lower()
]
print(f"Found {len(ai_statements)} AI/ML statements")

Web Explorer Features
Flat Design System: High-contrast, card-based interface with geometric typography.
Mobile Responsive: Slide-out filter drawer, sticky action bar, and responsive modal actions.
Search Scopes: Filter across Full Text, Title Only, Description & Solution, Organization, or Problem ID.
12 Tech Tag Pills: AI/ML, Computer Vision, NLP/LLM, GIS/Satellite, IoT, Blockchain, Robotics, Mobile Apps, Cloud, HealthTech, AgriTech, Cybersecurity.
1-Click Copy as MD: Copies the problem statement as a formatted GitHub Markdown document with metadata table and sections.
Clean Export Engine: Export filtered or selected subsets to JSON and CSV with sanitized fields.
Problem Detail Modal: Tabbed view featuring Full Description, Structured Sections, and Datasets & References.