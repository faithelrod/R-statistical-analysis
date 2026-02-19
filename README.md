# R-statistical-analysi# R Statistical Analysis Projects

Statistical modeling and analysis projects completed during my Master of Science in Business Analytics at the University of Alabama.

---

## Projects

### Chicago Crime Seasonality Modeling (`Final_Project_1.R`)
**Course:** Business Analytics / Statistical Modeling, Fall 2025

Modeled how seasonality, day of week, and major Chicago special events influence daily crime counts across four crime categories using 10 years of data (2015–2024).

---

### Overview

This project investigates whether temporal factors and special events are statistically significant predictors of daily crime in Chicago. Four negative binomial regression models were built and evaluated — one per crime category.

---

### Crime Categories

| Category | Crime Types Included |
|----------|-------------------|
| **Violent** | Battery, Assault, Criminal Damage, Homicide |
| **Non-Violent** | Theft, Robbery, Narcotics, Burglary |
| **Human Trafficking / Sex** | Criminal Sexual Assault, Domestic Violence, Prostitution, Kidnapping, Stalking, Sex Offense, Human Trafficking |
| **Special Event** | Arson, Gambling, Other Offense |

---

### Methodology

**Data Preparation:**
- Parsed datetime fields and extracted year, month, day, hour
- Converted day, month, season, and weekend to factor variables
- Aggregated to daily crime counts by category

**Exploratory Analysis:**
- Boxplots by day of week, month, season, and weekend vs. weekday
- Time series plot of total daily crimes with LOESS smoothing

**Modeling:**
- Negative binomial regression (`glm.nb`) for each crime category
- Predictors: day of week, month, season, weekend, marathon event, Lollapalooza, special events, river events
- 80/20 train/test split using `caret::createDataPartition`
- Model evaluation: RMSE, AIC, Deviance/DF ratio

**Diagnostics:**
- Residual plots
- VIF (Variance Inflation Factor) check for multicollinearity
- ANOVA with Tukey HSD post-hoc tests for month and weekend effects

---

### Key Findings

- Seasonal patterns are statistically significant predictors of violent and non-violent crime
- Special events (Lollapalooza, Chicago Marathon) have measurable effects on certain crime categories
- Month and season predictors show multicollinearity — VIF analysis flags this
- Summer months consistently show elevated violent crime counts

---

### Libraries Used

```r
library(arrow)      # Read parquet files
library(tidyverse)  # Data manipulation and ggplot2 visualization
library(lubridate)  # Date handling
library(caret)      # Train/test split
library(broom)      # Tidy model outputs
library(knitr)      # Formatted tables
library(car)        # ANOVA and VIF
library(MASS)       # Negative binomial regression (glm.nb)
```

---

## How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/r-statistical-analysis.git
   ```
2. Install required packages in R:
   ```r
   install.packages(c("arrow", "tidyverse", "lubridate", "caret", "broom", "knitr", "car", "MASS"))
   ```
3. Place `chicago_crime_seasonality_2015_2024.parquet` in your working directory
4. Run `Final_Project_1.R`

> **Note:** The parquet dataset is not included in this repo due to file size.

---

## Author
**Faith Elrod** | MS Business Analytics, University of Alabama  
[LinkedIn](https://linkedin.com/in/faithelrod) | faith.elrod03@gmail.com
