# 🗺️ Ethorx - Smart Data Mapper

**Transform messy, inconsistent data into perfect templates — automatically.**

Ethorx is a privacy-first, industrial-grade data mapping tool. It uses advanced string matching algorithms (including the Hungarian Algorithm) to intelligently map your raw data columns to a standard template, ensuring 100% data integrity without sending a single byte of data to the cloud.

---

## 🚀 Key Features

### 🧠 **Industrial-Grade Matching**
- **Optimal Assignment**: Uses the **Hungarian Algorithm** to ensure one-to-one column mapping. No duplicate assignments, ever.
- **Smart Pattern Detection**: Automatically identifies Emails, Dates, Phone Numbers, and Currencies to prevent illogical matches (e.g., matching a date column to an email field).
- **Strict Validation**: Requires statistically significant evidence (word overlap OR high fuzzy match score) before making a suggestion.
- **Expanded Vocabulary**: recognizies hundreds of synonyms and abbreviations (e.g., `addr` -> `Address`, `qty` -> `Quantity`).

### 🔒 **Privacy First**
- **No Cloud Storage**: All processing happens locally in your browser/machine.
- **No AI Training**: Your data is never used to train models.
- **Metadata Only**: We only save your *mapping configuration* (column names), never your actual data rows.

### ⚡ **Professional Workflow**
- **Prevent Duplicates**: Once a raw column is mapped, it vanishes from other dropdowns.
- **Real-time Feedback**: Instant visual confirmation of mapping confidence.
- **Auto-Formatting**: Automatically cleans and standardizes dates, numbers, and text during export.
- **Multiple Formats**: Export clean data to CSV, Excel, or JSON.

---

## 🛠️ Installation

### Prerequisites
- Python 3.8 or higher
- `pip` or `uv` package manager

### 1. Clone the repository
```bash
git clone https://github.com/your-repo/ethorx.git
cd ethorx
```

### 2. Install Dependencies
Using standard pip:
```bash
pip install -r requirements.txt
```

OR using `uv` (faster):
```bash
uv pip install -r requirements.txt
```

---

## 🏃‍♂️ How to Run

Start the application with a single command:

```bash
uv run streamlit run app.py
```
(or `streamlit run app.py`)

The app will open automatically in your browser at `http://localhost:8501`.

---

## 📖 User Guide

1.  **Upload Template**: Upload a "perfect" file (CSV/Excel) that has the columns you WANT.
2.  **Upload Raw Data**: Upload your messy file (CSV/Excel/JSON) that contains the data you HAVE.
3.  **Auto-Map**: Click **🚀 Auto-Map Fields**. The system will intelligently link columns.
4.  **Review & Adjust**:
    *   Green dots (🟢) indicate high confidence.
    *   Review any unchecked mappings.
    *   Manual overrides are saved automatically.
5.  **Download**: Click **Download Transformed Data** to get your clean file.

---

## ⚙️ Technical Details

### The Matching Algorithm
Ethorx uses a multi-stage scoring system to determine the best match:
1.  **Exact Match**: 100% score.
2.  **Synonym Match**: 95% score (e.g., "Mobile" ↔ "Phone").
3.  **Word Match**: 95% score if one header is a subset of another (e.g., "Customer ID" ↔ "ID").
4.  **Fuzzy Match**: 70-90% score based on character similarity.

**The Hungarian Algorithm** (`scipy.optimize.linear_sum_assignment`) is then applied to the cost matrix of these scores to find the **globally optimal assignment**, ensuring that the sum of confidence scores is maximized across all columns while enforcing a strict 1-to-1 constraint.

### Directory Structure
- `app.py`: Main application UI and logic.
- `utils/mapper.py`: Core matching logic and pattern detection.
- `utils/transformer.py`: Data cleaning and formatting engine.
- `utils/metadata_manager.py`: Handles saving/loading of mapping rules.

---

## 🛡️ License

Private and Confidential. Internal Use Only.
