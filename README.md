# Breast Cancer Spatial Transcriptomics: Tissue Composition Dashboard

An interactive R Shiny dashboard that visualizes **spot-level tissue composition** from a spatial transcriptomics study of triple-negative breast cancer (TNBC). Each tissue spot on a Visium slide is annotated with a dominant tissue type: Tumor, Stroma, Immune, Necrosis, Fat, or Mixedbased, on cell-type deconvolution fractions. The dashboard enables exploration of how tissue types are spatially distributed within individual slides and how composition varies across the full patient cohort.

**Live dashboard:** [github.com/ML198/TNBC-ST-dashboard](https://github.com/ML198/TNBC-ST-dashboard)

---

## Research Topic

Spatial transcriptomics links gene expression to physical location within tissue, allowing researchers to map the tumor microenvironment (TME) at near-cellular resolution. This dashboard focuses on the composition of the TME in breast cancer — specifically how much of each slide is occupied by tumor cells, supportive stroma, immune infiltrates, and other tissue compartments. Characterizing TME composition is a key step toward understanding treatment resistance and identifying patients who may benefit from immunotherapy.

---

## Dataset

| Field | Details |
|---|---|
| **Source** | Andersson et al. (2024), *Nature Communications* — [doi.org/10.1038/s41467-024-54145-w](https://doi.org/10.1038/s41467-024-54145-w) |
| **Platform** | 10x Genomics Visium spatial transcriptomics |
| **Study population** | Primary breast cancer tumor resections from human patients, spanning multiple breast cancer subtypes |
| **Data collection** | mRNA captured from spatially barcoded spots (~55 µm each) arrayed across tissue sections; cell-type fractions estimated via the STNavigation deconvolution pipeline |
| **Labeling rule** | Spots are assigned a hard tissue-type label when one cell type exceeds 60% of the deconvolution fraction; otherwise labeled "Mixed" |

---

## Dashboard Features

### Page 1 — Overview & Data Description
- Cohort-level summary statistics (number of slides, total spots, average tissue-type percentages)
- Full dataset description with data source link

### Page 2 — Interactive Visualizations

**Widget 1 — Cell-Type Composition Across All Slides** (stacked bar chart)
- Slides ordered by descending tumor content
- Hover tooltip: slide ID, tissue type, percentage of spots (%), spot count
- Legend toggles to show/hide individual tissue types

**Widget 2 — Single Sample Explorer** (two sub-tabs)
- *Spatial Tissue Map*: each dot is one spot colored by tissue type; hover shows spot ID, label, tumor fraction, stroma fraction, and dominance score; sidebar checkboxes filter tissue types
- *Tumor Fraction Heatmap*: continuous color scale (0–1) encoding raw tumor fraction per spot; hover shows exact fractions and assigned hard label

---

## Source Code

- [`dashboard_visualizations.Rmd`](dashboard_visualizations.Rmd) — main dashboard source (R Shiny + flexdashboard)

---

## Why This Matters

Understanding the spatial distribution of tumor, stroma, and immune cells in breast cancer tissue is critical for designing targeted therapies — regions of high stromal content have been linked to treatment resistance and poorer patient prognosis. This dashboard enables clinicians and researchers to rapidly characterize the tumor microenvironment across a patient cohort, supporting data-driven decisions about which slides warrant deeper molecular profiling.
