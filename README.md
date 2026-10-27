# E-commerce Delivery Time

> This project answers the question: What factors influence e-commerce delivery times, and how accurately can machine learning models predict the number of days required to deliver an order?

---

## Project Overview

This project compares

- **Objective:** 
- **Domain:** 
- **Key Techniques:** Data collection, Data processing, Exploratory data analysis, Statistical hypothesis testing

---

## Project Structure

```
├── data/                 # Raw and processed data
├── code/                 # Jupyter notebooks and Python scripts
├── reports/              # Generated reports and visualizations
├── requirements.txt      # Dependencies
└── README.md             # Project documentation
```

---

## Data

- **Source:** https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce/data?select=olist_products_dataset.csv
- **Description:** 

The raw datasets used in the project are located in the `data/raw/` folder.

---

## Analysis

The data analysis used the data science methodology. Here are main steps included:

- Load and explore the Seattle and Boston weather datasets.
- Convert variables to appropriate data types.
- Combine two datasets into a tidy format data frame.
- Identify and fill in missing values.
- Explore precipitation by day.
- Create a variable for month and explore precipitation by month.
- Create a variable for year and explore precipitation by year.
- Create a variable for whether there was any precipitation and compare the proportion of days with any precipitation between Seattle and Boston.
- Compare the mean amount of precipitation on days when precipitation occurred.
- Perform statistical hypothesis tests to determine whether monthly differences in precipitation amount and frequency were statistically significant.

The Jupyter notebook used to clean and analyze the data is: `code/.ipynb`
The cleaned data file is: `data/processed/.csv`

---

## Results


The document communicating the results of this project is: `reports/.pdf`

---

## Authors

- Krystal Tran[](https://github.com/tuyettran15999)
- 

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Acknowledgements

- Tools/libraries used: Python, NumPy, pandas, Matplotlib, Seaborn, SciPy, statsmodels, and Jupyter Notebook.
- This project was completed as part of the Foundations of Data Science course at Seattle University.

See `requirements.txt` for the required software and libraries.
