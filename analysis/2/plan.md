# Plan: Grounding Radiology Report Findings into Medical Image Segmentation (CF2Seg)

- Issue: #2
- Paper: `recommended/2026-08-20/cf2seg-clinical-findings-guided-segmentation/paper.json`
- DOI: https://doi.org/10.1038/s41746-026-03051-0
- Physician focus: "잘 검증해주세요" (please validate thoroughly) — no specific subgroup named, so the plan defaults to validating whether text-only-derived spatial information is plausible for our multi-label, unannotated cohort.

## Proposed presentation

Dashboard entry: "CF2Seg feasibility check — text-derived localization vs. our label-only cohort".

1. **Stacked bar chart — findings label composition** (x: label combination, y: study count, stacked/colored by single- vs multi-label). Encodes how much of our cohort is multi-label (the exact situation CF2Seg targets) vs. single-label/No Finding. This directly supports "잘 검증해주세요" by showing physicians how much of the data could even benefit from the method before any deep dive is funded.
2. **Pie chart — PA vs AP view position share**. CF2Seg's dual-stage fusion may be sensitive to view geometry; a quick share view flags how much of the cohort is AP (often portable/sicker patients) vs PA, relevant to whether spatial priors transfer.
3. **Text section — cohort vs. paper scale gap**. A short paragraph (not a chart) stating our 272 studies/153 patients vs. the paper's 53,386 examinations, since this is the single biggest transferability caveat and deserves plain text emphasis rather than a chart that would mislead by implying comparability.
4. **Text section — annotation gap disclosure**. Explicit statement that we hold no pixel-level annotations, so no segmentation accuracy metric can be computed locally; only qualitative radiologist review of any locally-generated masks would be possible.

Layout order: (1) label composition chart → (2) view position pie → (3) scale-gap text → (4) annotation-gap text → open questions. Rationale: lead with what makes the paper *relevant* (multi-label burden), follow with a secondary technical factor (view position), then ground expectations with the two hardest limitations before asking the physician to decide anything.

## Open questions

- Physician gave no specific subgroup; should the deep dive focus on the multi-label subset only (33 studies with `|` in findings_label) or the full cohort?
- Is any small-scale radiologist qualitative review of CF2Seg-generated masks (per the paper's own "check" note) feasible/acceptable here, given we have no ground-truth spatial annotations to validate against?
- Should AP-view studies (88/272, often portable/ICU-type) be excluded from a first feasibility pass given potential geometry mismatch with the paper's training distribution?
- What would count as "validated" for the physician given no local ground truth exists — expert visual plausibility only, or is that insufficient to greenlight any clinical use?
