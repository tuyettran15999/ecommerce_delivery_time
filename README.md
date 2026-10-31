# E-commerce Delivery Time

This project explores factors associated with e-commerce delivery times and aims to predict the number of days from order purchase to customer delivery.

## Project Overview

- **Objective:** Explore delivery patterns and develop regression models to predict delivery time.
- **Domain:** E-commerce and logistics.
- **Methods:** Data cleaning, relational data merging, exploratory data analysis, and planned predictive modeling.
- **Current status:** Data preparation and five initial EDA analyses are complete. Additional EDA and modeling are planned.

The analysis describes associations in observational data; it does not establish causal effects.

## Data

**Source:** [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).

The source data contains orders, customers, order items, payments, reviews, products, sellers, geolocation records, and product category translations. Raw files are stored in `data/raw/`.

Two cleaned tables support different levels of analysis:

| Dataset | Unit of observation | Main use |
| --- | --- | --- |
| `data/processed/clean_orders.csv` | One row per order (`order_id`) | Order-level EDA and the planned modeling dataset |
| `data/processed/clean_order_items.csv` | One row per order item (`order_id`, `order_item_id`) | Product, category, and seller exploration; feature engineering |

Order-level values and delivery times repeat across items in the item table. Use `clean_orders.csv` for order-level totals and average delivery times to avoid counting an order more than once.

## Project Structure

```text
├── code/
│   ├── load_explore_data.ipynb       # Initial data exploration
│   ├── data_preparation.ipynb        # Current cleaning and merging workflow
│   ├── exploratory_data_analysis.ipynb
│   └── data_cleaning.ipynb           # Earlier cleaning notebook
├── data/
│   ├── raw/
│   └── processed/
├── requirements.txt
└── README.md
```

## Data Preparation

The current workflow is documented in `code/data_preparation.ipynb`:

1. Inspect table sizes, missing values, duplicate rows, and table keys.
2. Convert date columns to datetime, standardize ZIP codes, and correct misspelled column names.
3. Inspect product measurements, prices, freight values, payments, reviews, and order dates.
4. Prepare median coordinates per ZIP code after preliminary coordinate screening. ZIP coordinates represent approximate locations, not exact addresses.
5. Aggregate payment and item records separately to the order level before merging.
6. Build order-level and item-level tables with merge-cardinality checks.
7. Calculate delivery time and delivery delay.
8. Validate row counts, duplicate keys, and item price/freight totals before exporting.

Missing category, product measurement, coordinate, and delivery-date values are retained for analysis rather than removing all affected records. Eight orders marked as delivered have no customer delivery date and therefore no calculated delivery time.

### Derived Variables

- **`delivery_time_days`:** Actual customer delivery timestamp minus purchase timestamp, expressed in fractional days.
- **`delivery_delay_days`:** Actual delivery date minus estimated delivery date, using calendar dates. Positive means late, zero means the same date, and negative means early.
- **`total_order_value`:** Sum of item prices plus freight charges.
- **`payment_total`:** Sum of payment records per order, kept separately from total order value.
- **`item_count`, `product_count`, `seller_count`:** Number of items, distinct products, and distinct sellers per order.

## Completed EDA

The notebook `code/exploratory_data_analysis.ipynb` examines delivered orders with nonmissing, nonnegative delivery times. The current analysis includes 96,470 orders.

1. **Delivery Time Distribution:** Mean delivery time is 12.56 days and the median is 10.22 days. The distribution is right-skewed, with some much longer delivery times.
2. **Delivery Time by Customer State:** Median delivery times range from 7.21 days in SP to 25.88 days in AM. State sample sizes vary considerably.
3. **Order Value and Delivery Time:** Spearman correlation is 0.143, indicating a weak positive association. Order value includes freight charges.
4. **Delivery Time by Item Count:** Group medians range from 9.86 to 10.26 days, with no clear increasing trend as item count rises.
5. **Delivery Time by Seller Count:** Multiple-seller orders have a median of 7.93 days versus 10.25 days for single-seller orders. Group sizes are highly unequal, and this comparison does not establish causation.

These findings describe delivered orders with valid delivery times, rather than all placed orders. Extreme delivery times require investigation before any decision to exclude them.

## Planned EDA Extensions

- **Distance and Delivery Time:** Examine associations with mean and maximum seller–customer distance per order.
- **Monthly Delivery Time Trends:** Compare median delivery time by purchase month alongside order counts.
- **Product Weight and Volume:** Explore order-level product measurements while accounting for missing values.
- **On-Time and Late Deliveries:** Calculate on-time and late-delivery rates for orders with known actual and estimated delivery dates; compare states and purchase months.
- **Product Categories:** Compare delivery times and sample sizes across categories. Count each order once per category, noting that orders with multiple categories can appear in more than one group.

## Planned Modeling

**Task:** Predict `delivery_time_days` at the order level using information available when an order is placed.

Candidate features include customer state, purchase month/day/hour, item and seller counts, item value, and order-level distance and product measurements. Features must be checked for availability at the prediction time.

Planned comparisons:

1. A baseline predicting the training-set median delivery time.
2. Ridge regression.
3. Random Forest regression.

## Author

- [Krystal Tran](https://github.com/tuyettran15999)
- [Michael Schneider](https://github.com/m1schneider)

## Acknowledgements

- Olist for the public dataset.
- This project was developed for the Foundations of Data Science course at Seattle University.