# Macro-TimeSeries-Canada-VECM
# Monetary Policy and the Taylor Rule in Canada (1994-2024)

## Overview
This repository presents a macro-econometric study of the Canadian economy, focusing on the empirical validation of the Taylor Rule. The project analyzes how the Bank of Canada adjusts its policy interest rate in response to inflation and cyclical economic fluctuations.

## Research Question
Does the Bank of Canada follow a systematic reaction function? The study investigates the long-run equilibrium and the dynamic transmission mechanism of monetary shocks between 1994 and 2024.

## Data & Variables
Analysis based on quarterly Canadian macroeconomic data:
* **Short-term Interest Rate (R_CAN):** The primary monetary policy instrument.
* **Inflation (P_CAN):** Year-over-year CPI change.
* **Output Gap:** Cyclical component of Real GDP extracted via the Hodrick-Prescott (HP) filter.
* **Unemployment Gap:** Alternative slack indicator used to validate Okun's Law.

## Methodology
The research was conducted using **Gretl** and follows a rigorous econometric workflow:
* **Filtering:** HP filter application for trend-cycle decomposition.
* **Stationarity:** Unit root analysis via Augmented Dickey-Fuller (ADF) tests and correlograms.
* **Cointegration:** Evaluation of long-run relationships using ARDL/Bounds tests, Engle-Granger two-step procedure, and the Johansen multivariate framework.
* **System Dynamics:** Estimation of a Vector Error Correction Model (VECM) to identify structural parameters and adjustment speeds.
* **Transmission:** Analysis of structural shocks through Impulse Response Functions (IRFs).

## Key Findings
* **Hawkish Stance:** The Bank of Canada strictly satisfies the Taylor Principle, with an aggressive reaction to inflation (coefficient > 1).
* **Systemic Equilibrium:** Cointegration was successfully identified through the Johansen procedure, highlighting the importance of accounting for joint endogeneity in macroeconomic variables.
* **Policy Transmission:** Impulse response analysis confirms a theoretically consistent Keynesian transmission, where contractionary shocks lead to a persistent decline in both inflation and the output gap.

## Repository Structure
* **`/report`**: Full technical paper (`GROUP'S 2 PC EXAM.pdf`) including theoretical framework and detailed diagnostic results.
* **`/results`**: Selection of key analytical charts, including the Output/Unemployment Gap comparison and the complete set of Impulse Response Functions (IRFs).
