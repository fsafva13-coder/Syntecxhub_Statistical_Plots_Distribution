# 📉 Statistical Plots & Distribution Analysis
> Understanding the shape, spread and outliers of data before drawing any conclusions — using histograms, KDE curves, boxplots and violin plots across three regional employee groups.

![Python](https://img.shields.io/badge/Python-3.14-blue?style=flat&logo=python)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.x-orange?style=flat&logo=python)
![Seaborn](https://img.shields.io/badge/Seaborn-0.13-teal?style=flat&logo=python)
![Pandas](https://img.shields.io/badge/Pandas-2.x-darkblue?style=flat&logo=pandas)
![SciPy](https://img.shields.io/badge/SciPy-1.x-darkgreen?style=flat&logo=scipy)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=flat&logo=jupyter)
![Internship](https://img.shields.io/badge/Syntecxhub-Data%20Science%20Internship-purple?style=flat)

---

## 📌 Project Overview

Before building any model or drawing any business conclusion, a data scientist needs to understand the shape of the data. Is it normally distributed? Skewed? Are there outliers pulling the mean away from the median? Do different groups behave differently?

This project answers all of those questions through statistical visualization — using histograms, KDE curves, boxplots and violin plots on a simulated employee performance dataset across three regional groups (North, South, East). Every chart is saved as a PNG and a written one-paragraph interpretation is exported for each variable.

Built as part of the Syntecxhub Data Science Internship (Week 2, Project 2).

---

## ✨ Features

- **Histograms with mean and median lines** — visualize frequency distribution for all 4 variables with reference lines marking central tendency
- **KDE overlays** — smooth probability density curves for group comparison, showing how salary and performance differ across regions
- **Histogram + KDE combined** — overlays the smooth KDE curve on top of the histogram for experience and satisfaction to highlight skewness
- **Boxplots across groups** — compares median, IQR spread and outliers for all 4 variables across all 3 regions simultaneously
- **Violin plots** — combines KDE shape with boxplot summary statistics in a single compact view
- **IQR-based outlier detection** — programmatically identifies and reports outliers per variable with count and percentage
- **Skewness analysis** — computes and prints skewness score with direction label (right-skewed, left-skewed, symmetric)
- **Written interpretation export** — generates `distribution_interpretation.txt` with a one-paragraph analysis per variable

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python 3.14 | Core programming language |
| Matplotlib | Base chart creation and customization |
| Seaborn | Statistical visualization — boxplots, violin plots, KDE |
| Pandas | Data manipulation and aggregation |
| NumPy | Data generation and numerical operations |
| SciPy | Statistical calculations |
| Jupyter Notebook | Development and documentation environment |

---

## 📸 Charts

### Histograms — All Variables
<img width="2075" height="1516" alt="01_histograms_all_variables" src="https://github.com/user-attachments/assets/6d368363-5cb2-4cd8-8cda-c381fada9be5" />

### KDE Comparison by Region — Salary & Performance
<img width="2073" height="722" alt="02_kde_salary_performance_by_region" src="https://github.com/user-attachments/assets/d779e01d-3ff2-4788-a5a6-601482b83242" />

### Histogram + KDE Overlay — Experience & Satisfaction
<img width="2074" height="718" alt="03_histogram_kde_overlay" src="https://github.com/user-attachments/assets/b9e238a0-5318-44f3-b536-5d47eda0ff56" />

### Boxplots by Region — All Variables
<img width="2075" height="1516" alt="04_boxplots_by_region" src="https://github.com/user-attachments/assets/d74314b8-1da8-4e8e-873d-bf3c327a7750" />

### Violin Plots — Salary & Performance by Region
<img width="2075" height="868" alt="05_violin_plots" src="https://github.com/user-attachments/assets/56e56443-6611-454c-b377-96c15a57c52e" />

---

## 🚀 Installation

1. Clone the repository
```bash
git clone https://github.com/fsafva13-coder/Syntecxhub_Statistical_Plots_Distribution.git
cd Syntecxhub_Statistical_Plots_Distribution
```

2. Install dependencies
```bash
pip install pandas numpy matplotlib seaborn scipy jupyter
```

3. Launch the notebook
```bash
jupyter notebook project2_statistical_plots_distribution.ipynb
```

4. Run all cells with **Kernel → Restart & Run All**

---

## 📋 Usage

The notebook is fully self-contained — it generates a 600-row employee dataset automatically across 3 regions with different distribution shapes built in.

**Pipeline flow:**
1. Dataset is generated with intentional differences between regions
2. Histograms reveal the overall shape of each variable
3. KDE curves compare distributions across groups on the same axis
4. Boxplots detect and flag outliers using the IQR method
5. Violin plots combine shape and summary in one view
6. A written interpretation is exported to `distribution_interpretation.txt`

To use your own dataset:
```python
df = pd.read_csv("your_data.csv")
```
Make sure your CSV has a grouping column and at least one numeric column to analyse.

---

## 📁 Project Structure

```
Syntecxhub_Statistical_Plots_Distribution/
├── README.md
├── project2_statistical_plots_distribution.ipynb   ← main notebook
├── distribution_interpretation.txt                 ← written analysis
└── plots/
    ├── 01_histograms_all_variables.png
    ├── 02_kde_salary_performance_by_region.png
    ├── 03_histogram_kde_overlay.png
    ├── 04_boxplots_by_region.png
    └── 05_violin_plots.png
```

---

## 📊 Results

| Variable | Skewness | Direction | Outliers |
|---|---|---|---|
| Salary | Moderate positive | Right-skewed | Yes — high earners in all regions |
| Performance | Near zero | Approximately symmetric | Minimal |
| Experience | Strong positive | Right-skewed | Yes — long-tenured staff |
| Satisfaction | Varies by region | Left (North), Symmetric (South), Right (East) | Minimal |

**Key findings:**
- East region has the highest salary and performance but the lowest job satisfaction
- South has the widest salary spread — most pay variation across employees
- Experience is right-skewed in all regions as expected in any real workforce
- Salary outliers were detected in all 3 regions — consistent with executive compensation patterns

---

## 🧠 Challenges & Learnings

**Challenge:** Seaborn 0.13 deprecated the `palette` parameter without `hue` in boxplots and violin plots, throwing `FutureWarning` messages. The fix was to add `hue="region"` and `legend=False` to match the new API — a small but important change for keeping notebooks warning-free.

**Learning:** The difference between a histogram and a KDE is more than just aesthetics. Histograms depend heavily on bin width — too few bins and you lose shape, too many and you get noise. KDE removes that decision entirely and produces a smoother, more interpretable curve, especially when comparing multiple groups on the same axis.

**Key insight:** A variable can have the same mean across groups but completely different shapes. East and North may have similar average salaries, but their distributions tell very different stories — one tight and predictable, one wide and variable. Summary statistics alone would miss this entirely.

---

## 🔮 Future Improvements

- Add Q-Q plots to formally test whether each variable follows a normal distribution
- Perform statistical significance tests (t-test, ANOVA) to confirm whether group differences are meaningful or just random variation
- Add a correlation matrix to explore relationships between variables
- Build an interactive version using Plotly so users can filter by region dynamically
- Extend the outlier detection to use Z-score method alongside IQR for comparison

---

## 👩‍💻 Author

**Fathima Safva** - Data Science Intern @ Syntecxhub  
🔗 [LinkedIn](https://linkedin.com/in/fathima-safva-578294315) · [GitHub](https://github.com/fsafva13-coder)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
