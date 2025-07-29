# Data-Cleaning-With-Pandas
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/your-repo)
![Python](https://img.shields.io/badge/Python-3.11-blue)
![Pandas](https://img.shields.io/badge/Pandas-2.3.1-orange)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.10.3-blueviolet)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-yellowgreen)


## Overview
This project implements industry-standard data cleaning pipelines using Pandas to transform raw, unstructured datasets into analysis-ready formats. The repository serves as both a practical toolkit and an educational resource for handling real-world data quality issues.


## Cleaning Process
1- Data Analysis
  - printing out the shape using `df.shape`
  - getting sum of null values using `df.isnull().sum()`

2- Handling Missing Values
  - Safe deletion when appropriate
  - Filling null values with median if possible (for numerical columns)
  - Filling null values with an appropriate word in some situations (for categorical columns)

3- Cleaning Columns
  - Strip trailing/leading whitespace using `str.strip()`
  - Remove special symbols with regex: `df['text'].str.replace(r'[^\w\s]', '')`
  - formatting time and date columns 
  - converting data types for later use

4- Visulixation
  - using matplotlib for data visulization

5- Answering Key Questions
  - using libraries like pandas to answer some questions for better practice


## **Tech Stack**  

| Tool               | Use Case                                      |
|--------------------|-----------------------------------------------|
| **Pandas**         | Core data manipulation & cleaning operations  |
| **Matplotlib**     | Data visualization & outlier detection        |
| **Jupyter**        | Interactive documentation & analysis          |
| **jdatetime**      | Persian (Jalali) date conversions & handling  |
| **re (RegEx)**     | Advanced string cleaning & pattern matching   |




## Challenges and Solutions
### Dropping rows with '?' symbol in laptop price dataset cleaning
  - filling '?' values with NaN first then dropping NaN values
```python
df.replace('?', np.nan, inplace=True)
df.dropna(inplace=True)
```

### some dates were in DD-MM-YY format but some were in MM-DD-YY format
  - parse dates in DD-MM-YY format and convert unparsable dates to NaT
  - create a mask where NaT values are True
  - second attemp on NaT values but with MM-DD-YY foramt
```python
# first attempt
df['releasedate'] = pd.to_datetime(df['releasedate'], format='%d-%m-%y', errors='coerce')

# second attempt
mask = df['releasedate'].isna()
df.loc[mask, 'releasedate'] = pd.to_datetime(df.loc[mask, 'releasedate'], format='%m-%d-%y', errors='coerce')
```

### extracting ratings (numeric) from stars
  - first extract the rating part and store it in a new column
  - then replace the rating part with an empty string
  - now we have 2 columns, one for rating the other for stars
```python
# sample: 5 out of 5 stars34 ratings

# extracting rating from stars column
df['ratings'] = df['stars'].str.extract(r'(\d+)\s*rating[s]?$')[0].fillna('0').astype(int)

# replaceing the rating part with an empty string
df['stars'] = df['stars'].str.replace(r'\s*\d+\s*rating[s]?$', '', regex=True)
```

## Installation
**Clone the repository**  
   ```bash
   git clone https://github.com/Lord-Mahdi1383/Data-Cleaning-With-Pandas.git
   cd Data-Cleaning-With-Pandas
```

**Install dependencies**
```bash
pip install -r requirements.txt
```
