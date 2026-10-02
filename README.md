# ailab-ml1

Coursework from **GirlTHing AI Lab**, Tuzla 2026.

GirlTHing AI Lab is an eight workshop program in machine learning, data science
and AI for women aged 18 to 30. It runs in two blocks: the first covers machine
learning and data science, the second covers LLMs, RAG and building a chatbot
application.

This repository covers **Workshop 1: Introduction to data and visualization**.

> Notebooks are written in Bosnian, since that is the language of the program.

---

## Contents

| File | What it is |
|---|---|
| `Uvod_numpy-linalg-pandas-uvod.ipynb` | Workshop notebook: NumPy, linear algebra basics and Pandas |
| `EDA_tuzla_stanovi.ipynb` | Workshop exercise: EDA on apartment listings in Tuzla |
| `tuzla_stanovi_oglasi_1.csv` | Data for the exercise, 668 listings |
| `EDA_makeup_shades.ipynb` | **Assignment, Part 2:** independent EDA on a dataset of my choice |

---

## Assignment

### Part 1: local Python environment

The workshop itself ran in GitHub Codespaces. The task was to reproduce that
setup locally:

- Python and Visual Studio Code with the Python and Jupyter extensions
- a virtual environment (`venv`) scoped to this project
- packages: `numpy`, `pandas`, `matplotlib`, `seaborn`, `jupyter`
- notebooks running in VS Code against the kernel from that venv

The `.venv` folder is excluded through `.gitignore`, since it is tied to one
machine and should never be committed.

### Part 2: independent EDA

Find any CSV dataset and run a short exploratory data analysis: load it, inspect
the structure, check for missing values, produce descriptive statistics, filter
and sort, use `groupby`, make at least two charts, and write up the findings.

I picked a dataset on **foundation makeup shades**: 6,816 shades across 107
brands, each with its exact color. The data comes from the
[TidyTuesday collection](https://github.com/rfordatascience/tidytuesday/tree/master/data/2021/2021-03-30),
originally from [The Pudding](https://pudding.cool/2021/03/foundation-names/).

**The question:** do brands that offer more shades actually reach darker skin
tones, or do they just add more variation where they already were?

**Findings:**

- Of the 6,730 shades left after cleaning, only **6.4% are dark** while 38.2% are
  light. The median lightness is 0.66.
- The correlation between total shade count and the share of dark shades is
  **-0.25**, slightly negative. A bigger range does not mean broader coverage.
- Eight brands offering more than 40 shades have **no dark shades at all**,
  including Dior with 153.

Cleaning turned up real problems along the way: 77 duplicate shades, one column
holding the same value in all 6,816 rows, and 17 entries that were blank white
placeholder images rather than actual foundation.

---

## Running the notebooks

```bash
git clone https://github.com/asja-b/ailab-ml1.git
cd ailab-ml1

python -m venv .venv
.venv\Scripts\Activate.ps1          # Windows PowerShell
# source .venv/bin/activate         # macOS and Linux

pip install numpy pandas matplotlib seaborn jupyter ipykernel
```

In VS Code, open a notebook and pick the interpreter from `.venv` under
**Select Kernel**.

`EDA_makeup_shades.ipynb` pulls its data straight from a URL, so nothing needs to
be downloaded. `EDA_tuzla_stanovi.ipynb` uses `tuzla_stanovi_oglasi_1.csv` from
this repository.

---

## Note on AI tools

Part of the assignment was to activate GitHub Copilot and record where AI helps
and where it gets things wrong. I used AI tools while building the analysis, and
documented that in the final section of `EDA_makeup_shades.ipynb`.

In short: AI was useful for syntax and for explaining pandas operations I do not
yet know by heart. It was not reliable for decisions about what the data actually
means. Its first suggestion for missing values was to drop every row containing
`NaN`, which would have thrown away a quarter of the dataset for no reason. Every
time I verified a claim instead of accepting it, something in the analysis
changed.

---

**Asja Brčaninović** | [github.com/asja-b](https://github.com/asja-b)
