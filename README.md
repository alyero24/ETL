# Periodic Table → BigQuery
This project fetches periodic table element data from the ptable.com JSON API, cleans it into a pandas **DataFrame**, and uploads it into **Google BigQuery** for querying and analysis.

**Sample Output**
| Atomic Number | Symbol | Atomic Weight | Electron Configuration | Series   | Melting Point (K) | Boiling Point (K) | Electronegativity | Valence | Discovery Year |
|---------------|--------|---------------|-------------------------|----------|-------------------|------------------|-------------------|---------|----------------|
| 1             | H      | 1.008         | 1s1                     | Nonmetal | 14.01             | 20.28            | 2.20              | 1       | 1766           |
| 2             | He     | 4.002602      | 1s2                     | Noble    | —                 | 4.22             | —                 | 0       | 1895           |
| 3             | Li     | 4.002602      | [He] 2s1	               | Alkali	  | 453.69            | 1615             | 0.98              | 1       | 1817           |

**Features**

- Fetches JSON data directly from the ptable.com API

- Cleans raw data (removes empty rows, standardizes column names)

- Converts into a pandas DataFrame with readable column headers

- Pushes the dataset into a BigQuery table for SQL queries

- Ready for data analytics and visualization with SQL or BI tools

**Tools Used**

Python 

Google BigQuery

pandas-gbq

Requests

# Sample Code Snippets
 **Upload DataFrame to BigQuery**

    to_gbq(

    df,
    
    destination_table="data123.periodicdata",  
    
    project_id="periodic-table-dataset",
    
    if_exists="replace"
    )

**Query data in BigQuery**

    SELECT 
    atomic_number,
    symbol,
    atomic_weight,
    series,
    discovery_year
    FROM `periodic-table-dataset.data123.periodicdata`
    WHERE series = 'Noble'
    ORDER BY atomic_number;

**Query Sample Output**

| **atomic_number** | **symbol** | **atomic_weight** | **series** | **discovery_year** | 
|-------------------|------------|-------------------|------------|--------------------|
| 10                | Ne         | 20.179            | Noble      | 1898
| 18                | Ar         | 39.948            | Noble      | 1894



**What You’ll Learn**

- How to fetch JSON data from a public API

- How to clean and standardize datasets with pandas

- How to load structured data into BigQuery

- How to query datasets in BigQuery using SQL


DATA SOURCE:https://ptable.com/JSON/properties-951c835.json

