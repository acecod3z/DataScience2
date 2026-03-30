# Assignment 2 — Movie Producer Analytics (IMDB Dataset)

This repository contains a Jupyter Notebook (`assignment2_ds.ipynb`) that analyzes an IMDB-style movie dataset (~3000 movies) to help a “rookie movie producer” decide **what kinds of movies to produce** and **which actors/directors/producers to work with**, based on profitability and ROI.

## Notebook: `assignment2_ds.ipynb`

### Objective
Explore the dataset for sanity and answer six business questions:

1. **Which movie made the highest profit?** Who were its producer and director? Identify the actors in that film.
2. **Which original language has the highest average ROI** (Return on Investment)?
3. **What are the unique genres** in the dataset?
4. Build a table of **producers and directors per movie** and find the **top 3 producers** by highest *average* ROI.
5. **Which actor appears in the most movies?** Deep dive into their movies, genres, and profits.
6. **Which actors do the top 3 directors prefer most?**

---

## Dataset
The notebook expects a CSV file that looks like a movie metadata export and includes columns such as:

- `budget`, `revenue`
- `original_language`
- `genres` (stored as a string representation of a list of dictionaries)
- `cast` and `crew` (also stored as stringified lists of dictionaries)
- other descriptive fields (title, overview, runtime, etc.)

### Important notes about input files
- The notebook is written for **Google Colab** and uses `files.upload()` to upload the CSV.
- In some cells the file path is referenced like:
  - `/content/imdb_data  (1).csv`
- Later, there is also a read using:
  - `imdb_data .csv`
  
If you run locally (or want consistent execution), you should **standardize the filename** and update reads accordingly.

---

## Key Features / Methods Used

### Libraries
- `pandas`, `numpy`
- `matplotlib`, `seaborn`
- `ast` (to parse stringified lists/dicts in `cast`, `crew`, `genres`)

### Derived Metrics
After filtering out invalid budgets:
- **Profit**: `profit = revenue - budget`
- **ROI**: `ROI = profit / budget`

### Parsing helpers
The notebook defines helper functions that parse the `crew` and `cast` fields to extract:
- `director` (job == `"Director"`)
- `producer` (job == `"Producer"`)
- `actors` (list of actor names)

---

## Example Results Highlighted in the Notebook

### Highest profit movie (from the notebook output)
- **Title:** Furious 7  
- **Director:** James Wan  
- **Producer:** Vin Diesel  
- **Profit:** 1316249360  
- **Actors:** a long list including Vin Diesel, Paul Walker, Dwayne Johnson, etc.

### Highest average ROI by language (top shown)
The notebook groups by `original_language` and prints the top results (example shown includes `ko`, `en`, `el`, ...).

### Unique genres
The notebook prints a set of unique genres found (e.g., Action, Drama, Comedy, Thriller, etc.) and also plots a **genre frequency bar chart**.

---

## Visualizations
The notebook includes plots such as:
- **Top 10 movies by profit** (bar chart)
- **Number of movies per genre** (bar chart)

---

## How to Run

### Option A — Run in Google Colab (recommended)
1. Open the notebook in Colab (the first cell includes an “Open in Colab” badge).
2. Run the upload cell and upload your dataset CSV.
3. Run cells top-to-bottom.

### Option B — Run locally (Jupyter)
1. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn
