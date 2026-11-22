# CSET485 – AI and Society | Assignment 1

**Student:** Aditya Rawat  
**Enrollment:** S24CSEU2155  
**Dataset:** Statlog German Credit Data (UCI)  
**Random state:** 155  
**Split:** 70% train / 30% test (stratified)

## Project contents

- `CSET485_Aditya_Rawat_Assignment.ipynb` — fully reproducible analysis notebook.
- `german.data` — original symbolic/categorical German Credit data file.
- `german.data-numeric` — numeric version supplied with the dataset archive.
- `german.doc` and `Index` — documentation and index supplied with the dataset.
- `build_report.py` — creates the complete PDF report from notebook outputs.
- `outputs/` — computed CSV tables, fairness chart, summary JSON, and final PDF report.

## Run the project

Use Python 3.10 or later.

```bash
python -m venv .venv
# Windows: .venv\\Scripts\\activate
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook CSET485_Aditya_Rawat_Assignment.ipynb
```

Run **all notebook cells from top to bottom**. The notebook reads `german.data` locally; it does not need to download the dataset. It regenerates the preprocessing diagnostics, OLS/logistic model comparison, subgroup coefficient analysis and confidence intervals, omitted-variable analysis, adversarial subset, fairness threshold table/chart, CSV outputs, and PDF report. The final notebook cell runs `build_report.py` to create `outputs/CSET485_Aditya_Rawat_Report.pdf`.

You can also regenerate the PDF after the notebook has produced the CSV outputs:

```bash
python build_report.py
```

## Outcome definition and limitations

The original UCI target is `1 = good credit risk` and `2 = bad credit risk`. For the assignment's requested binary target, the notebook maps good credit risk to `approval=1` and bad credit risk to `approval=0`. This is an analytical proxy; it is **not** a record of historical bank approval decisions. The analysis is descriptive and does not establish causation or production readiness.

The notebook uses the last three digits of the enrollment number as the random seed (`155`) and a stratified 70/30 split. The sex/status groups are defined from `personal_status_sex`: women-coded A92/A95 and men-coded A91/A93/A94. The supplied file contains A92 but no A95 rows.

## Dataset citation

Hofmann, H. (1994). *Statlog (German Credit Data)* [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5NC77. The supplied dataset archive includes the original symbolic file and documentation. Cite the dataset when reusing it.

## GitHub submission

Create a GitHub repository and upload the contents of this folder. Keep the notebook, dataset, report-generation script, requirements file, and `outputs/` folder together so the project can be reproduced. After uploading, copy the repository URL into the assignment submission portal. No GitHub repository has been published from this package.
