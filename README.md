# Body Mass vs Maximum Longevity in Mammals

A data analysis project that explores whether larger mammals live longer, using the AnAge database of
animal life-history traits.

## Problem / Research Question

Is there a relationship between a mammal species' body mass and its maximum recorded longevity, and how
strong is that association?

## Dataset

- **File:** `Datasets/anage_data.csv`
- **Source:** AnAge database of animal longevity and life-history traits
  (<https://genomics.senescence.info/aging>). The extract used here is the course-provided copy:
  4,218 records and 30 traits (Class, Body mass (g), Maximum longevity (yrs), Data quality, and others).
- **Subset analysed:** 417 mammal species (`Class == 'Mammalia'`, body mass below 200,000 g).
- **Usage permissions:** AnAge is a public, open-access academic database used here for educational
  purposes. Please cite the original source if you reuse it in a publication. No restricted or personal
  data is included in this repository.

## Methods and Tools

- **Language / environment:** Python 3, Jupyter Notebook
- **Libraries:** pandas (loading and filtering), numpy (log transform), seaborn and matplotlib (figures)
- **Analysis steps:**
  1. Load the full AnAge extract and filter to mammals under 200,000 g (417 species).
  2. Compute the association between body mass and maximum longevity three ways: Pearson on raw mass,
     Pearson on log10 mass, and Spearman rank correlation.
  3. Figure 1: scatter plot of maximum longevity against body mass with a fitted regression line and a
     95% confidence band. Body mass spans five orders of magnitude, so the horizontal axis is
     logarithmic and ticked in grams and kilograms.
  4. Figure 2: median maximum longevity for five body-mass classes, with the number of species in each
     class annotated on the bars.

## Key Findings

- Heavier mammals live longer on average, and the relationship is monotone: median maximum longevity
  rises from **4.8 years** for species under 10 g to **26.6 years** for species of 10-200 kg.
- The association is stronger on a logarithmic scale: Pearson **r = 0.59** for log10 body mass and
  **rho = 0.65** (Spearman), against only **r = 0.43** for raw mass. Body mass therefore acts
  multiplicatively on lifespan rather than additively.
- The association is moderate, not tight. Longevity ranges from about 2 to over 100 years inside a
  single mass class, so body mass explains part but not all of the variation.

## Limitation

This is an observational analysis of one curated database. Correlation does not imply causation, records
differ in data quality and provenance, and the 200,000 g cut-off excludes the largest mammals (for
example elephants and whales). The results describe this sample, not all mammals.

## Peer Feedback and Response

A classmate reviewed the first version of this repository and pointed out that the charts did not explain
what the measurements represented: the scatter plot had no axis labels and no units, so a reader could not
tell what the numbers on either axis meant.

**Response — commit `da0a7f6` ("Improve figures: axis labels, units and a median-by-mass-class
chart"):**

- Both axes are now labelled with units ("Body mass", "Maximum longevity (years)").
- The title states the finding and the sample size (n = 417 species, r = 0.59).
- The body-mass axis is logarithmic and ticked in grams and kilograms, so the five orders of magnitude are
  readable.
- An annotation describes the scatter points and the 95% confidence band.
- A second chart was added: median maximum longevity for five body-mass classes, with the number of species
  in each class shown on the bar.
- The notebook was updated to produce both figures, and this README was rewritten to match the new results.

## Figures

| Figure | File | What it shows |
|---|---|---|
| 1 | `visualizations/body_mass_vs_longevity.png` | Longevity against body mass (log scale) with regression line and 95% CI |
| 2 | `visualizations/longevity_by_mass_class.png` | Median longevity by body-mass class, with sample sizes |

Both figures carry axis labels with units, a title stating the finding, and the sample size.

## How to Run

1. Clone or download this repository.
2. Install the dependencies: `pip install -r requirements.txt`
3. Start Jupyter: `jupyter notebook`
4. Open `MC641763_Activity7.05.ipynb` and run all cells (Kernel -> Restart & Run All).
5. The notebook writes the two figures into `visualizations/`.

The dataset is included in `Datasets/`, so no download step is required.
