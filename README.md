# Cardiac Pre-Op Risk Calculator

A single-page, mobile-friendly perioperative cardiovascular risk stratification tool for hospitalists and preoperative clinics. Pairs validated risk scores with an auto-generated assessment & plan (A&P) ready to paste into the EMR.

**[Open the calculator](https://smoussa6.github.io/-cardiac-preop-calculator/)**

> **Decision support only — not a replacement for clinical judgment.** This tool estimates perioperative cardiovascular risk to inform shared decision-making. The decision to proceed with surgery is made by the performing physician and the patient. Per 2024 AHA/ACC guidance, our role is not to "clear" patients but to estimate risks and benefits.

## Privacy

- **100% client-side.** No patient data is transmitted, stored, or logged anywhere. All calculations happen in your browser.  
- **No analytics, no tracking, no cookies, no external API calls.**  
- Source code is in this repo — auditable by you and your institution.  
- Safe to use with real patient data at the bedside; nothing leaves the device.

## Included scores

| Score | Predicts | Reference |  
|---|---|---|  
| **RCRI** (Revised Cardiac Risk Index) | 30-day MACE | Lee TH et al. *Circulation* 1999;100:1043. Risk percentages updated per Davis C et al. systematic review (2013). |  
| **AUB-HAS2** | 30-day death/MI/stroke | Dakik HA et al. *JAHA* 2019;8:e016228. Derived in 3,284 patients, validated in 1.16M from ACS-NSQIP. |  
| **DASI** (Duke Activity Status Index) | Functional capacity (validated against 30-day MI/death) | Hlatky MA et al. *Am J Cardiol* 1989;64:651. METS study (Wijeysundera DN et al. *Lancet* 2018;391:2631) showed subjective MET assessment **did not** predict outcomes — DASI did. |  
| **Cardiac biomarkers** (NT-proBNP, hs-troponin) | Perioperative MI / cardiac mortality | 2024 AHA/ACC: Class 2a for NT-proBNP, Class 2b for hs-troponin |  
| **Active cardiac conditions checklist** | Triggers for delay/optimization | Per 2024 AHA/ACC/multisociety perioperative guideline |

For **CPT-specific** myocardial infarction or cardiac arrest risk, this tool links to the validated [ACS NSQIP Surgical Risk Calculator](https://riskcalculator.facs.org/RiskCalculator/).

## What it generates

A copy-paste-ready A&P block in Epic-friendly plain text:

- Procedure description, urgency category, and risk class  
- All risk scores with calculator interpretation  
- Active cardiac conditions and risk modifiers identified  
- Cardiac biomarker findings (if checked)  
- Medication management (anticoagulation, beta-blocker, statin, GLP-1)  
- Specific recommendations matched to inputs  
- Auto-included clinical disclaimer

## Guideline currency

Recommendations align with the **2024 AHA/ACC/ACS/ASNC/HRS/SCA/SCCT/SCMR/SVM Guideline for Perioperative Cardiovascular Management for Noncardiac Surgery** (*Circulation* 2024;150:e351). Last reviewed: 2026-05-21.

Key 2024 changes reflected:  
- DASI preferred over subjective METs (Class 2a)  
- BNP/NT-proBNP and troponin for biomarker stratification (Class 2a / 2b)  
- Stress testing reserved for poor/unknown functional capacity + high-risk surgery + management would change  
- Newly indicated beta-blockers must be started ≥7 days preop, never day-of  
- Recent PCI delay timelines: 12 mo (acute/complex DES), 6 mo (chronic DES), 3 mo (time-sensitive)  
- GLP-1 hold: weekly ≥1 week, daily day-of (per 2023 ASA, 2025 ASGE updates)

## Usage

1. Open the calculator (mobile or desktop)  
2. Step through RCRI, AUB-HAS2, DASI, and Biomarkers tabs  
3. Fill in the Assessment tab (procedure, urgency, active conditions, modifiers, medications)  
4. Click **Generate**, then **Copy** → paste into electronic medical record.

No sign-in, no install, works offline once loaded.

## Development

The calculation logic lives in the `PreopCalc` namespace inside `index.html` — pure functions with no DOM dependencies, designed to be tested in isolation.

**Tests:** Open `tests.html` in any modern browser. Should show all green.

> **⚠️ Important:** If you modify any function in the `PreopCalc` namespace inside `index.html`, you must apply the same change to the `PreopCalc` block in `tests.html` (look for the `// ===== PREOPCALC START =====` marker in both files).

## Not included (by design)

- **Built-in NSQIP MICA calculator** — links to the validated ACS calculator instead  
- **Patient identifiers** — the textareas accept free text; keep PHI out of the tool  
- **Decision automation** — recommendations are starting points for human reasoning

## License

MIT — see [LICENSE](./LICENSE). Includes a clinical-use notice.

## Author

Sumer Moussa, MD — Cardiovascular Disease Fellow. Built for personal/teaching use; shared in case it helps others.

---

*This tool does not constitute medical advice. Use of the tool does not establish a physician-patient relationship with the author.*  
