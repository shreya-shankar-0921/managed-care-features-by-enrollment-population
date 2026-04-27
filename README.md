# Medicaid Managed Care: Longitudinal Trends and Population Models (2016-2024)

## Overview

This repository contains an automated data pipeline and interactive analytical report examining state-level Medicaid managed care utilization over the past decade. 

As state Medicaid agencies transition populations away from traditional fee-for-service models, understanding how different demographic groups—ranging from low-income adults to highly vulnerable populations requiring long-term services—are integrated into managed care is critical for evaluating health policy, program integrity, and care delivery structures.

### View the Live Interactive Report

**[https://shreya-shankar-0921.github.io/managed-care-features-by-enrollment-population/]**

## Key Analytical Themes

This project explores three core structural dynamics within Medicaid administration:

1. **The Saturation of Comprehensive MCOs:** Tracking the longitudinal adoption (2016-2024) of capitated risk-based contracts across primary eligibility categories following ACA expansions.

2. **Tiering High-Acuity Interventions:** A cross-sectional analysis of how states deploy resource-intensive, specialized models like **PACE** (Program of All-Inclusive Care for the Elderly) versus broader safety-net models like **MLTSS** (Managed Long-Term Services and Supports).

3. **The "Carve-Out" Strategy:** Evaluating state-level decisions to either integrate specialty services (Behavioral Health and Dental) into comprehensive plans or "carve them out" to specialized vendor networks for vulnerable populations.

## The Data Pipeline & Pre-processing

Public health administrative data often requires significant transformation before it is analysis-ready. This project features a robust data cleaning pipeline built in `R` using the `tidyverse`, designed to handle systemic inconsistencies in federal reporting data:

* **Regex Text Extraction:** Administrative data columns frequently embed footnote markers and non-standard characters directly into numeric fields (e.g., `"FC/AA26"`, `"--"`). The script utilizes `stringr` and regular expressions to safely isolate and extract true numeric values.

* **Standardizing Nomenclature:** Handled mid-dataset shifts in category strings (e.g., correcting "Oxford comma" inconsistencies introduced in 2022 that severed time-series continuity).

* **Structural Feature Engineering:** Identified and merged segmented "Mandatory" and "Voluntary" enrollment columns to accurately capture true state-level adoption metrics, particularly critical for 100% voluntary programs like PACE.

## Technologies Used

* **R / RStudio:** Primary environment for data manipulation and statistical programming.

* **Tidyverse (`dplyr`, `tidyr`, `stringr`):** Used for data wrangling, cleaning, and functional transformations.

* **ggplot2 & Plotly:** Used to generate static visual grammar and convert it into fully interactive, client-side HTML widgets.

* **RMarkdown:** Used to weave the reproducible code, data pipeline, and analytical narrative into a single compiled document.

## Repository Structure
```text
├── data/
│   └── managed-care-features.csv    # Raw administrative dataset
├── index.Rmd                        # Source code and analytical narrative
├── index.html                       # Compiled interactive report (served via GitHub Pages)
└── README.md                        # Project documentation