# Data-Cleaning-With-Pandas

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Pandas](https://img.shields.io/badge/Pandas-1.0%2B-orange)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-yellowgreen)
![License](https://img.shields.io/badge/License-MIT-green)


## Overview
This project focuses on cleaning and preprocessing raw datasets to make them analysis-ready. Data cleaning is a crucial step in the data science pipeline that ensures data quality and reliability for downstream tasks. This repository demonstrates professional data cleaning techniques using Python's powerful data manipulation libraries.

## Cleaning Process
1- Data Analysis
  - printing out the shape
  - getting sum of null values

2- Handling Missing Values
  - Safe deletion when appropriate
  - Filling null values with median if possible (for numerical columns)
  - Filling null values with an appropriate word (for categorical columns)

3- Cleaning Columns
  - removing any misleading trailspace and symbols
  - formatting time and date columns 
  - converting data types for later use

4- Visulixation
  - using matplotlib for data visulization

5- Answering Key Questions
  - using libraries like pandas to answer some questions for better practice


## Challenges and Solutions
### Dropping rows with '?' symbol in laptop price dataset cleaning
  - filling '?' values with NaN first then dropping NaN values

### some dates were in DD-MM-YY format but some were in MM-DD-YY format
  - parse dates in DD-MM-YY format and convert unparsable dates to NaT
  - create a mask where NaT values are True
  - second attemp on NaT values but with MM-DD-YY foramt

## Installation
**Clone the repository**  
   ```bash
   git clone https://github.com/Lord-Mahdi1383/Data-Cleaning-With-Pandas.git
   cd Data-Cleaning-With-Pandas




**Install dependencies**
