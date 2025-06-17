# Outlier-Resistant A/B Test Evaluation Study


This project investigates the performance of three A/B testing methods under varying conditions of noise, outliers, and effect sizes. It systematically evaluates the **Standard t-test**, **Welch's t-test**, and a **10% Trimmed Mean t-test** across 100 different scenarios using a simulation framework in R.

---

## 📌 Overview

A/B testing is widely used in industry to evaluate the impact of new features, products, or experiences. However, the statistical methods behind A/B testing often assume ideal conditions—equal variances, normality, and clean data. Real-world data—especially user behavior data—rarely satisfies these conditions.

In this study, we simulate **10,000 experiments per scenario** under combinations of:

- 5 **effect sizes**: `0`, `0.1`, `0.2`, `0.3`, `0.5`
- 4 **sample sizes per group**: `10`, `30`, `50`, `100`
- 5 **outlier levels**: `0%`, `2.5%`, `5%`, `10%`, `15%`

---

## 🧪 Methodology

### Data Generation

- **Control group**: Normally distributed values with mean = 60, sd = 10
- **Treatment group**: Same base distribution with effect size shifts, variance changes, and injected high-value outliers (simulating long session times or bot behavior)

### Statistical Tests Compared

- **Standard t-test** – assumes equal variances
- **Welch’s t-test** – accounts for unequal variances
- **Trimmed mean t-test (10%)** – removes top and bottom 10% of each group

### Metrics Evaluated

- **Statistical power** across all conditions
- **Power differences** between tests
- **Visualizations**: power curves, boxplots, distribution plots

---

## 📊 Key Results

### Main Findings

- **Trimmed t-tests** outperform others when **outlier contamination is ≥10%**, especially at low effect sizes.
- **Welch’s t-test** offers better protection when variances are unequal but can be slightly conservative.
- **Standard t-test** performs well under ideal conditions but suffers the most with outliers or heteroskedasticity.

### Model Performance & Visuals

- 100 simulated scenarios × 10,000 repetitions
- Paired t-tests and effect size plots show significant and consistent trends
- Code saves summary tables and ggplot2 visualizations of results

## 📁 Project Structure

ab_test_robustness/
│
├── FinalProjectCodeBehind.Rmd # R Markdown file with full simulation and analysis
├── Clark-Enge---PSTAT-122-Final-Project.pdf # Final report (written analysis)
├── results_df.rds # Saved simulation results (power values per scenario)
├── diff_summary.rds # Paired t-test comparison table
├── power_curves_es_tt.rds # Power curves by effect size
├── power_curves_outlier.rds # Power curves by outlier %
├── dist_differences.rds # Boxplot data for power differences between tests
├── power_diff.rds # Boxplot data for power distributions
├── README.md # Project documentation (this file)

yaml
Copy
Edit

---

## 📦 Dependencies

This project was developed using R. To run the simulation and generate the report, ensure the following packages are installed:

### Required R Packages
```
├── FinalProjectCodeBehind.Rmd # R Markdown file with full simulation and analysis
├── Clark-Enge---PSTAT-122-Final-Project.pdf # Final report (written analysis)
├── results_df.rds # Saved simulation results (power values per scenario)
├── diff_summary.rds # Paired t-test comparison table
├── power_curves_es_tt.rds # Power curves by effect size
├── power_curves_outlier.rds # Power curves by outlier %
├── dist_differences.rds # Boxplot data for power differences between tests
├── power_diff.rds # Boxplot data for power distributions
├── README.md # Project documentation (this file)
```
---

## How to Run
1. Clone the repository:
```
git clone https://github.com/yourusername/AB-Simulation-Study.git
cd AB-Simulation-Study
```
2. Open **AB-Simulation-Study.Rmd** in RStudio
3. Install required dependencies
4. Run the analysis by knitting the R Markdown file to a pdf
