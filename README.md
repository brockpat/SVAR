# SVAR
Project as part of the course on Structural Vector Autoregressive Analysis by Helmut Lütkepohl taught at the DIW Berlin

# Replication and Extension of Galí (1999): Technology, Employment, and the Business Cycle

## 📖 Preface

This project replicates the main findings of the article:

> **Technology, Employment, and the Business Cycle: Do Technology Shocks Explain Aggregate Fluctuations?**  
> Jordi Galí (1999), *American Economic Review*, Vol. 89, No. 1.

Beyond replication, I provide extensions of Galí’s framework and conduct independent analyses inspired by his work.  

- The majority of the analysis is carried out in **R**.  
- Some computations were conducted in **Stata** (Do-files available).  
- The **Appendix** of the seminar paper neatly organizes the R code and results for each section.

---

## 📊 Data

- **Original Data (Galí, 1999):** Quarterly U.S. data from 1948:1–1994:4 sourced from *Citibase*.  
- **Replication Data (this project):**  
  - Quarterly, seasonally adjusted real GDP and employment data from **FRED**.  
  - Annual hours worked combined with quarterly employment shares to construct quarterly hours.  

- Both productivity and hours worked exhibit non-stationarity, and are made stationary by first differencing.  
- Augmented Dickey-Fuller tests confirm stationarity of differenced series.

---

## 🔧 Methodology

### Reduced Form VAR
- VAR lag length selected via **AIC, HQC, and BIC**, with diagnostics guiding final choice.  
- Diagnostic checks include:  
  - ARCH effects  
  - Normality tests (Jarque-Bera)  
  - Serial correlation (Portmanteau test)  
- Chosen specification: **VAR(5)**.

### Forecasting
- VAR(5) in levels with a linear trend was used for forecasting.  
- Forecasts compared against true out-of-sample values (1995 onward).  
- Productivity forecasts track actual values closely; hours worked diverge after ~5 quarters.

### Structural Estimation (SVAR)
- Long-run identifying restriction: only **technology shocks** affect productivity in the long run.  
- Impulse-Response Functions (IRFs):  
  - Hours worked **decline** following a positive technology shock.  
  - This result is inconsistent with RBC models (which predict positive co-movement).

---

## 📈 Extensions

### Structural VECM (SVECM)
- Expanded Galí’s bivariate model by including the **interest rate**.  
- Tested for **cointegration** using Johansen’s method → found 1 cointegration relationship.  
- Estimated **VECM with 6 lags** (based on AIC and diagnostics).  
- Structural restrictions imposed:  
  - Long-run triangular identification.  
  - Technology shocks drive productivity in the long run.  
- Results: SVECM IRFs show **positive long-run labour effects**, somewhat mitigating the RBC critique.

---

## 🧪 My Own Analysis: Testing Monetarism

Inspired by Galí’s SVAR approach, I test monetarist predictions using U.S. data:

- **Variables:** Monetary base (*M1*) and CPI-based inflation.  
- **Sample:** 1960:1–2019:1 (quarterly) + monthly robustness checks.  
- **Identification:** Short-run restrictions (sticky prices → inflation does not respond immediately to monetary shocks).  

### Findings:
- Money supply shocks have **no significant long-run effect on inflation**.  
- Results align with **New Keynesian** theory, not monetarism.  
- Robustness checks with interest rates and higher frequency (monthly) data confirm findings.

---
