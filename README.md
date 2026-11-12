# Monetary Policy and the Taylor Rule in Canada (1994–2024)

**Does the Bank of Canada follow a systematic, Taylor-type reaction function?**
A macro-econometric study of quarterly Canadian data (1994Q1–2024Q1) comparing single-equation and system-based cointegration methods, and tracing the transmission of monetary policy shocks with a VECM.

📄 **Full paper:** [Taylor_Rule_Canada_VECM.pdf](report/Taylor_Rule_Canada_VECM.pdf)

---

## Research question

The Taylor rule describes the policy rate as a function of inflation and the output gap:

```
R_t = β0 + β1·P_t + β2·OG_t + ε_t        (expected: β1 > 1, β2 > 0)
```

We ask whether this relationship holds as a stable long-run equilibrium in Canada, and whether the answer depends on the econometric approach used to estimate it.

## Data

Quarterly data, 1994Q1–2024Q1 (T = 121). Source: **OECD Economic Outlook**.

| Variable | Description |
|---|---|
| `R_CAN` | Nominal short-term interest rate (policy instrument) |
| `P_CAN` | CPI inflation, year-over-year % change |
| `LY_CAN` | Log of real GDP |
| `hp_LY_CAN` | Output gap: cyclical component of `LY_CAN` from the Hodrick–Prescott filter |
| `U_CAN` | Unemployment rate (used for the unemployment gap and an Okun's law check) |

## Methodology

1. **Univariate analysis.** Plots, correlograms and ADF unit root tests (general-to-specific lag selection with AIC, constant and trend).
2. **Transformations.** HP-filtered gaps compared with first differences in two VAR(4) specifications.
3. **Single-equation cointegration.** ARDL/Bounds test (Pesaran–Shin–Smith) and the Engle–Granger two-step procedure.
4. **System cointegration.** Johansen trace and max-eigenvalue tests (restricted constant, 4 lags in levels).
5. **VECM.** Identification of the long-run reaction function and impulse response functions over 20 quarters.

All estimation was carried out in **Gretl**.

## Key results

**1. Single-equation methods fail to establish a stable rule.**

| Test | Statistic | Outcome |
|---|---|---|
| ARDL / Bounds (PSS) | F = 3.33 (5% upper bound: 4.85) | No level relationship |
| Engle–Granger | residual ADF = −2.63; ECM ≈ −0.056 | Weak / inconclusive |

Both methods treat inflation and the output gap as given, ignoring the joint endogeneity of the system.

**2. The Johansen system approach finds cointegration.**

| H0 | Trace | p-value |
|---|---|---|
| r = 0 | 50.19 | 0.0005 |
| r ≤ 1 | 20.79 | 0.043 |
| r ≤ 2 | 5.18 | 0.274 |

The cointegrating vector normalised on the policy rate gives the long-run reaction function:

```
R_CAN = −0.319 + 16.014·P_CAN + 28.657·hp_LY_CAN
```

Both coefficients have the expected positive sign, and the inflation response exceeds one (Taylor principle). The adjustment coefficient of the interest-rate equation is −0.039: about 3.9% of a deviation from the rule is corrected each quarter.

**3. Monetary transmission is consistent with theory.**
After a contractionary interest-rate shock, inflation shows a short-lived price puzzle and then declines persistently, while the output gap falls and turns negative after about five quarters. The VECM responses are smoother and more persistent than those of the VAR in differences, which discards the long-run information in the levels.

![Impulse responses from the VECM](result/IRF%20PLOT.png)

*Impulse responses from the VECM over 20 quarters with confidence bands. Each panel "X -> Y" shows the response of Y to a shock in X.*

![Output gap and unemployment gap](result/GAPS%20hp_LY%20hp_U.png)

*HP-filtered output gap (`hp_LY_CAN`) and unemployment gap (`hp_U_CAN`). The two gaps move in opposite directions, consistent with Okun's law; note the COVID-19 swing in 2020. Full series shown; the analysis uses 1994Q1–2024Q1.*

## Limitations

- The long-run coefficients are very large in magnitude, so they should be read as evidence on signs and the Taylor principle rather than as precise policy elasticities.
- Results depend on the HP filter for the output gap, which is known to have end-of-sample problems.
- The sample includes the 2008–09 crisis, the effective lower bound period and the COVID-19 shock, which may cause parameter instability.

## Repository structure

```
├── report/
│   └── Taylor_Rule_Canada_VECM.pdf   # full technical paper
├── result/
│   ├── IRF PLOT.png                  # VECM impulse responses
│   └── GAPS hp_LY hp_U.png           # output and unemployment gaps
└── README.md
```

## Authors

Group project for the course **Time Series Econometrics**, University of Bologna:
Olimpia Benelli, Carlotta Cosio, Tommaso Cotoloni, Marco Orlandi, Edoardo Tartarelli, Matteo Tugu.
