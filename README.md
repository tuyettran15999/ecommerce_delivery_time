# Weather Project: Seattle vs Boston

> This project compares precipitation in Seattle, WA and Boston, MA from January 1, 2018 to December 31, 2022.

---

## Project Overview

This project compares precipitation patterns in Seattle and Boston to investigate whether it rains more in Seattle. The project uses historical daily precipitation data from both cities from 2018 to 2022.

The analysis shows that whether Seattle is rainier than Boston depends on how precipitation is measured. Seattle experiences precipitation more frequently, while Boston tends to receive more precipitation when precipitation occurs and generally has higher total annual precipitation.

- **Objective:** Determine whether Seattle receives more rainfall than Boston.
- **Domain:** Weather Analytics
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

- **Source:** https://www.ncei.noaa.gov/cdo-web/search?datasetid=GHCND
- **Description:** Historical daily precipitation data for Seattle, WA and Boston, MA from January 1, 2018 to December 31, 2022.

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

The Jupyter notebook used to clean and analyze the data is: `code/Weather_Data.ipynb`
The cleaned data file is: `data/processed/clean_seattle_boston_weather.csv`

---

## Results

The results show that whether Seattle receives more precipitation than Boston depends on how precipitation is measured.

Seattle has precipitation more frequently, particularly during the winter months. However, Boston has more precipitation on average on days when precipitation occurs and generally has higher total annual precipitation. Boston also experiences more extreme daily precipitation events.

Overall, Seattle is rainier in terms of precipitation frequency, while Boston tends to have heavier and greater precipitation. Statistical tests also identified significant differences in precipitation amount and frequency between the two cities during several months of the year.

The document communicating the results of this project is: `reports/Weather_Project_Report.pdf`

---

## Authors

- Krystal Tran[](https://github.com/tuyettran15999)

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Acknowledgements

- Tools/libraries used: Python, NumPy, pandas, Matplotlib, Seaborn, SciPy, statsmodels, and Jupyter Notebook.
- This project was completed as part of the Foundations of Data Science course at Seattle University.

See `requirements.txt` for the required software and libraries.
