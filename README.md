# U+ Toronto Library Partnership Dashboard

A data analysis and visualization project designed to identify the best Toronto Public Library branches for U+ digital literacy skill-building partnerships.

## 📋 Project Overview

This project analyzes Toronto Public Library (TPL) branch data to support U+ in identifying optimal partnership locations for delivering digital literacy programs. The analysis considers multiple factors including branch activity levels, youth engagement, community reach, and facility features.

**Project Code:** DA-08  
**Organization:** U+ (Digital Literacy Program)  
**Focus:** Toronto Public Library System

## 📁 Project Structure

```
├── README.md                    # Project documentation (this file)
├── requirements.txt             # Python dependencies
├── TLPP-Dashboard/              # Main analysis and dashboard directory
│   ├── README.md               # Dashboard-specific notes
│   ├── CleaningDecisions.md    # Data cleaning methodology and decisions
│   ├── notebook.ipynb          # Main analysis notebook
│   ├── final_notes.ipynb       # Final findings and conclusions
│   ├── dashboard.html          # Interactive HTML dashboard
│   ├── DA08_Eden_ProjectFile.html # Project presentation/report
│   ├── SWEETVIZ_REPORT.html    # Automated data profiling report
│   ├── data/                   # Raw data files (CSV format)
│   │   ├── tpl-branch-general-information-2023.csv
│   │   ├── library-circulation-by-cardholder-type.csv
│   │   ├── tpl-visits-annual-by-branch.csv
│   │   ├── tpl-branch-space-rentals-2024.csv
│   │   ├── tpl-card-registrations-annual-by-branch.csv
│   │   ├── tpl-events-feed.csv
│   │   ├── tpl-events-feed_source2.csv
│   │   ├── tpl-workstation-usage-annual-by-branch-2018-2023.csv
│   │   └── README.md           # Data sources documentation
│   └── images/                 # Visualization outputs
│       ├── aligned_types.png
│       ├── graph2a_branch_heatmap.png
│       └── da-08_toronto_library_program_partnership_dashboard_1_.pdf
```

## 🎯 Key Data Sources

The analysis integrates multiple Toronto Public Library datasets:

1. **Branch General Information (2023)** - Core branch metadata, facilities, and program offerings
2. **Library Circulation Data** - Borrowing patterns by cardholder type
3. **Annual Visits by Branch** - Foot traffic and branch popularity
4. **Card Registrations** - New member registration trends
5. **Events Feed** - Community event programming
6. **Workstation Usage (2018-2023)** - Computer/technology resource utilization
7. **Space Rentals (2024)** - Room rental activity and facility usage

## 🔍 Analysis Highlights

### Data Cleaning & Preprocessing
- Removed non-physical branches (virtual services, bookmobiles)
- Standardized data formats and handled missing values
- Created normalized metrics for comparison (see `CleaningDecisions.md` for detailed methodology)

### Key Metrics Analyzed
- Youth engagement indicators (Kids Stop programs, Teen Council presence)
- Technology infrastructure (workstation availability and usage)
- Community reach (visits, card registrations, events)
- Facility capacity (space rentals, square footage)
- Service tier and accessibility

### Deliverables
- **Interactive Dashboard** (`dashboard.html`) - Visualize branch comparisons and rankings
- **Analysis Notebook** (`notebook.ipynb`) - Reproducible analysis code and methodology
- **Final Report** (`DA08_Eden_ProjectFile.html`) - Executive findings and recommendations
- **Data Profile Report** (`SWEETVIZ_REPORT.html`) - Automated statistical summaries

## 🚀 Getting Started

### Prerequisites
- Python 3.7+
- Jupyter Notebook or JupyterLab
- Dependencies listed in `requirements.txt`

### Installation

1. Clone or download this repository
2. Install required packages:
   ```bash
   pip install -r requirements.txt
   ```

### Running the Analysis

1. Open the Jupyter notebooks:
   ```bash
   jupyter notebook TLPP-Dashboard/notebook.ipynb
   ```

2. View the interactive dashboard:
   - Open `TLPP-Dashboard/dashboard.html` in a web browser

3. Explore the data:
   - Review `TLPP-Dashboard/SWEETVIZ_REPORT.html` for data profiling
   - Check `TLPP-Dashboard/final_notes.ipynb` for conclusions

## 📊 Key Findings

See `TLPP-Dashboard/final_notes.ipynb` and `TLPP-Dashboard/DA08_Eden_ProjectFile.html` for detailed findings and recommendations on optimal library partnership locations.

## 📝 Methodology

Comprehensive data cleaning and decision documentation is available in `TLPP-Dashboard/CleaningDecisions.md`, including:
- Columns retained/removed and rationale
- Row-level filtering decisions
- Data transformation logic applied to each dataset

## 🔧 Technologies Used

- **Python** - Data analysis and processing
- **Pandas** - Data manipulation and analysis
- **Jupyter Notebook** - Interactive analysis environment
- **HTML/CSS/JavaScript** - Dashboard visualization
- **Sweetviz** - Automated data profiling

