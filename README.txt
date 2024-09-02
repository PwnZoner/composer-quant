
# PDF Metrics Extraction Script



This Python script processes multiple PDF files from Jhicken's Composer Quant Tools browser plugin (https://github.com/jhicken/composer-quant-tools) in order to compare metrics using excel.  

JHicken's tool is itself forked from DPods browser plugin https://github.com/dpods/symphony-tools 

The script extracts key metrics from each PDF saving the results into a CSV file. It PDF get's its own row for easy filtering and comparison.  It handles PDFs that contain financial or performance data, such as "live," "backtest," or "oos" scenarios, and organizes the extracted data into a structured format.  Especially useful for portfolio's running 20+ Composer Symphonies. 

## Features

- **Title Retention**: The script retains the full title of each PDF.
- **Title Type Extraction**: A new column, `Title Type`, is added to indicate whether the PDF relates to a "live," "backtest," or "oos" scenario.
- **Key Metrics Extraction**: Extracts and saves only the key metrics from each PDF, avoiding problematic sections like "Top 10 Drawdowns".
- **Avoids Duplicate Titles**: The script ensures that the metric titles are only captured from the first PDF, avoiding duplication in subsequent rows.

## Requirements

- Python 3.x
- `pdfplumber` library
- `pandas` library

You can install the required libraries using the following commands:
```
pip install pdfplumber pandas
```

## How to Use

1. **Prepare Your PDFs**: Place all the PDF files you want to process in a directory (e.g., `pdfs/`).
2. **Run the Script**:
    - Ensure the script points to the correct directory where your PDFs are stored (default is `pdfs/`).
    - Run the script using Python.

    ```bash
    python your_script_name.py
    ```

3. **Output**: The script will generate a CSV file called `combined_metrics_output_with_title_type.csv` in the current working directory.

## Example Output

The output CSV file will have the following structure:

| Title | Title Type | Risk-Free Rate | Time in Market | Cumulative Return | ... |
|-------|------------|----------------|----------------|-------------------|-----|
| ENO K-1 50/50 ... | live | 0.0% | 100.0% | 180.28% | ... |
| ENO K-1 50/50 ... | oos  | 0.0% | 100.0% | 530.6% | ... |
| ENO K-1 50/50 ... | backtest | 0.0% | 100.0% | 8,561,730.75% | ... |

## Notes

- **Title Type Extraction**: The script uses a regex to detect "live," "backtest," or "oos" in the title. If none of these are found, it defaults to "Unknown".
- **Handling Special Characters**: The script cleans the title by removing special characters like `|`, `[`, `]`, `$`, `%`, etc.

## Troubleshooting

- **No PDFs Found**: Ensure that the script is pointing to the correct directory containing the PDFs.
- **Incorrect Data Extraction**: If the data extracted seems off, review the PDF formatting or adjust the regex patterns used in the script.

## License

This script is provided "as-is" without warranty of any kind. Feel free to modify and use it as needed.

