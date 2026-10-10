# Atlanta Homelessness Funding Analysis

This project explores homelessness-related funding in Atlanta using HUD grant award data, Point-in-Time homelessness counts, and U.S. Census community indicators. It examines how funding is distributed across organizations and programs through data cleaning, descriptive analysis, regression, clustering, and visualizations.

## Project features

- Filter HUD Point-in-Time counts to Atlanta's Continuum of Care (GA-500)
- Retrieve Georgia place-level population, median rent, and poverty data from the 2023 Census ACS five-year API
- Clean and analyze Atlanta-related HUD grant awards
- Compare the largest awards, average award amounts, and funding by program type
- Explore the relationship between award count and total organizational funding with linear regression
- Group award amounts using K-means clustering
- Create bar, pie, and scatter plots

The analysis is exploratory. It does not establish that funding causes changes in homelessness.

## Tech stack

Python, pandas, NumPy, requests, Matplotlib, scikit-learn, and Jupyter Notebook.

## Files

- `PhaseIII_Mannam_112.ipynb` — data preparation, analysis, and visualizations
- `README.md` — project overview and instructions

## Data sources

- HUD Point-in-Time counts: `2007-2024-PIT-Counts-by-CoC.xlsb`, filtered to Atlanta CoC `GA-500`
- U.S. Census Bureau 2023 ACS five-year data: [Georgia places API](https://api.census.gov/data/2023/acs/acs5?get=NAME,B01001_001E,B25064_001E,B17001_002E&for=place:*&in=state:13)
- HUD grant awards: `Grantee_Awards_04142026_101738462.xls`, filtered for Atlanta-related entries

**The two local spreadsheet inputs are not included in this repository.**

## How to run

1. Install Python and Jupyter Notebook or JupyterLab.
2. Install the dependencies:

   ```bash
   pip install pandas numpy requests matplotlib scikit-learn pyxlsb lxml
   ```

3. Obtain the two HUD input spreadsheets listed above.
4. Open `PhaseIII_Mannam_112.ipynb` and replace the absolute local file paths in `downloaded_dataset_parser()` and `html_parser()` with paths on your own computer.
5. Run the notebook cells in order. The Census API request requires internet access.

**Input note:** The existing `html_parser()` uses `pandas.read_html()` with a local `.xls` filename. Depending on the actual file format, that step may need an HTML-compatible source or a different reader. The notebook's original analysis code has been preserved.

## Outputs

The notebook generates:

- `atlanta_homeless_trends.csv`
- `census_comparison.csv`
- `bar_chart.png`
- `pie_chart.png`
- `scatter_plot.png`

It also displays funding summaries, regression results, and K-means clustering assignments.

## Data considerations

The homelessness parser converts nonnumeric counts to zero, which may not distinguish missing data from true zero values. The Census comparison excludes places with populations of 10,000 or fewer and nonpositive median-rent values. Regression and clustering results describe patterns within the analyzed records and should not be interpreted as causal findings.

## Presentation

- [Presentation video](https://youtu.be/90HQzW87gCA)
- [Presentation slides](https://docs.google.com/presentation/d/1ePjktmshvte72yZLasBtIVjsomiPVcyJ-vH7QnkahB8/edit?usp=sharing)
