# Data Comparison and Error Detection Script

## Description
This Python script compares data from two Excel sheets (`calculo_metricas.xlsx` and `COLECAO_DOURADA.xlsx`) for different sheets. It identifies errors by comparing rows in the two dataframes based on similarity and exact matching of numeric columns. The script performs the following steps:

1. **Reading Excel Files**: It loads the relevant sheet from both Excel files for each sheet name in a predefined list (`dfs`).
   
2. **Comparing Data**: 
   - It compares data based on exact matches for a numeric column and similarity checks for other string-based columns.
   - If no match is found, it records an "Error" and specifies which columns differ.
   - For rows with a match above a threshold (94%), the status is set to "Not Error".
   
3. **Output**: The results are saved as CSV files in the `Avaliações` folder, one CSV per sheet.

## Functions

### `compare(df_metrics, df_gold_collection)`
- Compares rows between two dataframes, `df_metrics` and `df_gold_collection`.
- It calculates the similarity between the rows and checks for exact matches for numeric fields.
- Returns a merged dataframe with a status of "Not Error" or "Error" and an explanation of differences for each row.

### `save_to_csv(df_gold_collection, sheet_name)`
- Saves the comparison results to a CSV file in the `Avaliações` directory, named after the sheet name.

## How to Use
1. Place the `calculo_metricas.xlsx` and `COLECAO_DOURADA.xlsx` files in the parent directory.
2. Ensure the list `dfs` contains the sheet names you want to compare.
3. Run the script in your Python environment. The script will generate a CSV file for each sheet in the `Avaliações` directory.

## Dependencies
- `pandas`: Used for data manipulation.
- `openpyxl`: Required to read Excel files.
- `difflib`: Used for calculating row similarity.

## Example Output
For each sheet, a CSV file will be saved in the `Avaliações` folder. The output will contain columns like:
- `status`: Whether the row is an "Error" or "Not Error".
- `error_reason`: A description of the column differences (if any).