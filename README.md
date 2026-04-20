[README.md](https://github.com/user-attachments/files/26890735/README.md)
# IOVC Analyzer — README

**Tool developed for:**
> Capuz Martínez, M. (2025). *Beyond Capital: Using Non-Financial Value Creation to Assess the Intentionality of Impact Investors.* Bachelor of Business Administration, IE University.

**Supervisor:** Nicolas Martinez Chiluisa
**Framework:** Nachyła, P., & Justo, R. (2024). How do impact investors leverage non-financial strategies to create value in social enterprises? *Journal of Business Venturing Insights, 21*, e00435.

---

## What is this tool?

The IOVC Analyzer is a browser-based automated content analysis tool built to support the methodology of the thesis above. It processes the text of impact investing reports and assigns a **1–5 prominence weight** to each of the **10 non-financial value-creation strategies** defined in the IOVC framework (Nachyła & Justo, 2024).

The tool requires **no installation**, runs entirely in the browser (client-side JavaScript), and does not send any data to a server.

---

## Files

| File | Description |
|------|-------------|
| `IOVC_Analyzer_v2.html` | Main tool — recommended version. Supports PDF drag & drop, multi-report comparison, CSV and JSON export. |
| `IOVC_Analyzer.html` | Original version — text paste only, no PDF support. |
| `README.md` | This file. |

---

## How to use

1. **Open** `IOVC_Analyzer_v2.html` in any modern web browser (Chrome, Firefox, Edge, Safari). No server needed — just double-click the file.

2. **Enter the report name** in the text field at the top (e.g., "GIIN State of Market 2024").

3. **Load the report text** — either:
   - Drag and drop a **PDF** onto the drop zone (text will be extracted automatically), or
   - Paste the report text manually into the text area.

4. **Click "Analizar"** — the tool will count keyword hits for each of the 10 IOVC strategies and display:
   - Total keyword hits
   - Number of strategies found
   - Word count analyzed
   - A 1–5 weight for each strategy (shown as a bar and star rating)
   - A tag cloud of all keywords found

5. **Click "+ Guardar"** to save the results for this report.

6. **Repeat steps 2–5** for each report in the corpus.

7. **Click "Comparar reportes"** to see a side-by-side comparison matrix of all saved reports.

8. **Click "Exportar CSV"** to download the weight matrix as a `.csv` file for analysis in Excel or similar tools.

---

## The 10 IOVC Strategies

The keyword dictionary is derived directly from Nachyła and Justo (2024), Table 5.

| Level | Strategy | Example Keywords |
|-------|----------|-----------------|
| Investee | Impact Planning | theory of change, impact thesis, logic model, impact workshop |
| Investee | Impact Measuring | KPI, impact metrics, IRIS, benchmark, additionality |
| Investee | Impact Reporting | impact report, disclosure, accountability, SFDR, GRI |
| Investee | Impact Managing | IMM, mission drift, impact guardian, organizational learning |
| Fund | Legal | LPA, mission lock, B Corp, impact covenant, investment contract |
| Fund | Governance | board, investment committee, impact committee, board seat |
| Fund | Talent Management | impact team, impact officer, dedicated impact, impact training |
| Fund | Financial Incentives | carried interest, impact carry, impact hurdle, compensation |
| Community | Portfolio Engagement | peer learning, investee community, knowledge sharing, synergy |
| Community | Ecosystem Building | ecosystem, market building, advocacy, field building, legitimacy |

---

## Weighting formula

For each document, raw keyword hit counts are normalized to a 1–5 scale:

```
weight = 0                              if hits = 0
weight = max(1, round(hits / max_hits × 5))   if hits > 0
```

Where `max_hits` is the highest keyword frequency observed across all strategies in that document. This ensures weights are **relative within each document**, not absolute across documents.

| Weight | Interpretation |
|--------|---------------|
| 0 | Strategy not present in this document |
| 1 | Marginal — mentioned but not prominent |
| 2 | Low — below average prominence |
| 3 | Moderate — average prominence |
| 4 | High — above average frequency |
| 5 | Central — near maximum frequency |

---

## Technical notes

- **PDF extraction** uses [PDF.js](https://mozilla.github.io/pdf.js/) (v3.11.174) loaded from Cloudflare CDN. An internet connection is required for PDF drag & drop. Text paste works fully offline.
- **No data is stored** between sessions. All results are held in memory and lost on page refresh unless exported.
- **Language:** The tool interface is in Spanish, but the keyword dictionary operates in English. All analyzed reports must be in English.
- **Browser compatibility:** Tested on Chrome 120+, Firefox 121+, Edge 120+. Safari 17+ supported.

---

## Corpus analyzed in the thesis

The tool was used to analyze 30 reports divided into three groups:

- **Group 1 — Impact Fund Reports (n = 9):** Bridges Fund Management (AR 2022/23, AR 2023/24, Transparency Report 2023), Big Society Capital (2023), Big Issue Invest (2022/23), SWEN Capital Partners Blue Ocean (2023), Pymwymic (2021, 2023), Triodos Impact Strategy Funds (2023).

- **Group 2 — Sectoral Reports (n = 15):** GIIN GIINsight series (2023, 4 reports), GIIN State of Market 2024, GIIN Sizing 2024, Impact Europe Annual Report 2024, Impact Europe 5 Ws 2024, EVPA Non-Financial Support Guide 2015, EVPA Investing for Impact Toolkit 2020, EVPA Navigating IMM 2022, EVPA How to Do IMM 2024, EVPA SFDR Survey 2023, ITF Report 2023.

- **Group 3 — Institutional Reports (n = 11):** OECD 2015, OECD 2019, OECD 2023, IFC OPIM 2019, IFC Annual Report 2023, World Bank Working Paper, Impact Management Platform Imperative 2021, Impact Europe/EVPA How to Do IMM 2024, EVPA Non-Financial Support Guide 2015, Impact Europe 5 Ws 2024, Impact Europe Annual Report 2024.

---

## Citation

If you use this tool in your own research, please cite:

> Capuz Martínez, M. (2025). *IOVC Analyzer* [Software tool]. Developed for TFG BBA, IE University. Based on the IOVC framework by Nachyła, P., & Justo, R. (2024). Journal of Business Venturing Insights, 21, e00435.

---

## License

This tool was developed for academic research purposes. You are free to use and adapt it for non-commercial research, provided you cite the original thesis and the IOVC framework (Nachyła & Justo, 2024).
