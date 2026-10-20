# Body Mass vs Maximum Longevity in Mammals

A data analysis project that explores whether larger mammals live longer, using the AnAge database of animal life-history traits.

## Problem / Research Question

Is there a relationship between a mammal species' body mass and its maximum recorded longevity? How strong is the association?

## Dataset

- **File:** `Datasets/anage_data.csv`
- **Source:** AnAge database of animal longevity and life-history traits (https://genomics.senescence.info/aging); this is a course-provided extract containing 4,218 species records and 30 traits (e.g., Class, Body mass (g), Maximum longevity (yrs), Data quality).
- **Usage permissions:** The AnAge database is a public, open-access academic dataset. It is used here for educational purposes; please cite the source if you reuse it in a publication.

## Methods and Tools

- **Language / environment:** Python 3, Jupyter Notebook
- **Libraries:** pandas (data loading and filtering), seaborn and matplotlib (visualization)
- **Analysis steps:**
  1. Load the full AnAge extract.
  2. Filter to mammals (`Class == 'Mammalia'`) with body mass below 200,000 g (417 species).
  3. Fit and visualize a linear regression of body mass against maximum longevity (seaborn `regplot`).
  4. Inspect the distribution of maximum longevity (histogram with KDE).

## Key Findings

- Heavier mammals tend to live longer: the regression line slopes upward and the Pearson correlation between body mass and maximum longevity is **0.427**.
- The association is moderate but noisy: the median maximum longevity is only 12 years, and longevity varies widely even among species of similar size, so body mass explains only part of the variation.
- The longevity distribution is strongly right-skewed: most mammal species live less than ~25 years, with a few very long-lived outliers.

## Limitation

- This is an observational analysis: correlation does not imply causation, and lifespan depends on many other factors (taxonomy, environment, sample quality). Records also vary in data quality and provenance, and the extract is limited to the fields and species it contains.

## How to Run

1. Clone or download this repository.
2. Install the dependencies: `pip install -r requirements.txt`
3. Start Jupyter: `jupyter notebook`
4. Open `MC641763_Activity7.05.ipynb` and run all cells (Kernel → Restart & Run All).
5. The notebook saves two figures into `visualizations/`:
   - `body_mass_vs_longevity.png`
   - `longevity_distribution.png`
