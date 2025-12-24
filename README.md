# Mixed Linear Models


# QTL Pyramiding — Unified Linear Mixed Model (MLM) Pipeline

This repository contains a comprehensive **Linear Mixed Model (MLM)** analytical framework implemented in R. It is specifically designed for **QTL Pyramiding** research, evaluating the interaction between introgression status, recurrent parents, donor parents, and environmental locations.

## 🔬 Experimental Model Structure
The pipeline fits a unified mixed-effects model to account for fixed genetic effects and random environmental variance:

**Formula:**
$$Trait \sim (Introgression \times RecurrentParent \times DonorParent) + (Introgression \times Location) + (1 | Location:Block)$$

* **Fixed Effects:** Testing the main effects and interactions of QTL introgression across different genetic backgrounds and environments.
* **Random Effects:** Accounting for the nested structure of experimental blocks within locations.

## 🚀 Key Features
* **Automated Trait Processing:** Dynamically detects and analyzes common and location-specific traits (e.g., yield, biomass, grain morphology).
* **Robust Data Cleaning:** Includes a custom numeric sanitization engine to handle messy Excel formatting and non-finite values.
* **Statistical Rigor:** * Generates **Type III ANOVA** tables with automated significance starring (`***`, `**`, `*`).
    * Calculates **Estimated Marginal Means (EMMeans)** for complex interactions.
    * Performs **Tukey HSD** post-hoc testing for mean comparisons.
* **Diagnostic Suite:** Automatically exports Q-Q plots and Residual vs. Fitted plots for every model to verify normality and homoscedasticity.

## 📊 Visualization Engine
The repository includes a specialized "Joined Plot" function that generates high-resolution, faceted GxE interaction plots:
* **Faceted by Parentage:** Rows represent Recurrent Parents; Columns represent Donor Parents.
* **Environment Interaction:** Visualizes phenotypic plasticitity across locations (Pullman, Othello, Almota).
* **Publication Ready:** Features `ggtext` integration for stylized, informative subtitles and custom color palettes for Wild Type (WT) vs. Mutant (MT).

## 🛠 Tech Stack
* **Modeling:** `lmerTest`, `emmeans`, `broom`
* **Data Wrangling:** `dplyr`, `tidyr`, `janitor`, `stringr`
* **Visualization:** `ggplot2`, `ggtext`

## 📂 Outputs
For every trait analyzed, the pipeline creates a dedicated directory containing:
1.  `MLM_ANOVA_Tidy.csv` — Significance results.
2.  `MLM_EMMEANS.csv` & `MLM_Tukey_HSD.csv` — Comparative statistics.
3.  `MLM_GxE_Combined.png` — Multi-faceted interaction plots.
4.  `MLM_Diagnostics.png` — Model validation plots.
5.  `Final_MLM_GxE_Summary.csv` — A master table summarizing significance across all analyzed traits.
