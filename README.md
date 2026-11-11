# FIFA 21 Player Data Cleaning and Transformation

## Project Overview

This project focuses on cleaning and transforming the FIFA 21 player
dataset using Python. The goal is to make the data more consistent,
structured, and suitable for further exploratory data analysis and
potential machine learning work.

The notebook starts with an initial inspection of the dataset and then
works through selected columns that contain inconsistent formats, mixed
measurement units, dates, abbreviated numerical values, and star-based
ratings.

> **Project status:** In progress. The notebook documents the cleaning
> work completed so far. The remaining columns and final dataset
> validation still need to be completed.

## Dataset Overview

The dataset used in this project contains **18,979 player records and 75
original columns**. It includes player information such as financial
values, physical attributes, contract details, player ratings, and other
FIFA 21 attributes.

The dataset file is expected at:

``` text
rawDataset/fifa21 raw data.csv
```

## Dataset Source and Attribution
Dataset Source: The FIFA 21 dataset was obtained from Kaggle. Please refer to the original dataset page for its source and licensing information.

- **Dataset source:** [FIFA 21 Player Dataset](https://www.kaggle.com/datasets/ahmedmmmahmoud/fifa-21-player-dataset)
- **Platform:** Kaggle


The raw dataset is not included in this repository. Please visit the original Kaggle page to access it.

## Tools and Libraries

-   **Python** --- main programming language
-   **Pandas** --- loading, inspecting, and transforming tabular data
-   **NumPy** --- numerical operations and missing-value handling
-   **Matplotlib** --- data visualization
-   **Regular expressions (`re`)** --- extracting structured information
    from text

## Work Completed So Far

The current notebook covers the following transformations:

  ---------------------------------------------------------------------
  Column                             Work performed
  ---------------------------------- ----------------------------------
  `Value`                            Converted euro amounts containing
                                     `M` (millions) and `K` (thousands)
                                     into numerical values

  `Wage`                             Converted abbreviated euro amounts
                                     into numerical values

  `Release Clause`                   Converted abbreviated euro amounts
                                     into numerical values

  `Weight`                           Standardized kilograms and pounds
                                     into kilograms

  `Height`                           Standardized centimeters and
                                     feet/inches into centimeters

  `Contract`                         Created a contract-status column,
                                     extracted contract years and loan
                                     end dates, and calculated contract
                                     duration

  `Joined`                           Converted text dates into datetime
                                     values and extracted joining year,
                                     month number, and month name

  `Hits`                             Converted values such as `1.6K`
                                     into numerical values and
                                     preserved missing values

  `W/F`                              Removed the star symbol and
                                     converted weak-foot ratings into
                                     integers

  `SM`                               Removed the star symbol and
                                     converted skill-move ratings into
                                     integers

  `A/W`                              Inspected and preserved the
                                     `High`, `Medium`, and `Low`
                                     categorical labels

  `D/W`                              Inspected and preserved the
                                     `High`, `Medium`, and `Low`
                                     categorical labels

  `IR`                               Removed the star symbol and
                                     converted international-reputation
                                     ratings into integers
  ---------------------------------------------------------------------

## Selected Cleaning Decisions

### Financial values

Values such as `€103.5M` and `€500K` are converted into numerical euro
amounts:

-   `M` is interpreted as 1,000,000.
-   `K` is interpreted as 1,000.

### Physical measurements

-   Weight is standardized to kilograms.
-   Height is standardized to centimeters.

### Contract information

The original `Contract` field contains different formats. The notebook
creates additional fields for contract status, contract start year,
contract end year, loan end date, and contract duration.

These derived fields should be validated carefully before being used in
analysis. In particular, contract-year extraction should be checked
against loan records so that a loan expiration year is not mistakenly
interpreted as a regular contract start year.

### Dates

The `Joined` column is converted to datetime. Additional year and month
features are extracted to support date-based summaries and
visualization.

### Missing values

The `Hits` column contains missing values. These are preserved rather
than automatically replaced with zero because a missing value does not
necessarily mean that the player received zero profile views.

### Categorical attributes

The `A/W` and `D/W` columns contain meaningful labels (`High`, `Medium`,
and `Low`). They are preserved as categorical text rather than being
assigned arbitrary numerical values.

## Repository Structure

A suggested repository structure is:

``` text
fifa21-player-data-cleaning/
│
├── README.md
├── FIFA21_Player_Data_Cleaning_Updated.ipynb
├── rawDataset/
│   └── fifa21 raw data.csv       # Keep out of GitHub unless redistribution is permitted
│
└── .gitignore
```

## How to Run the Notebook

1.  Clone or download this repository.

2.  Make sure Python is installed.

3.  Install the required libraries:

    ``` bash
    pip install pandas numpy matplotlib jupyter
    ```

4.  Place the dataset at `rawDataset/fifa21 raw data.csv`, or update the
    file path in the notebook to match your local location.

5.  Start Jupyter Notebook:

    ``` bash
    jupyter notebook
    ```

6.  Open `FIFA21_Player_Data_Cleaning_Updated.ipynb` and run the cells
    from top to bottom.

## Next Steps

-   Continue inspecting and cleaning the remaining columns.
-   Review missing values and inconsistent formats across the full
    dataset.
-   Validate the derived contract fields, especially for loan records.
-   Perform final checks on data types, duplicate records, and
    unexpected values.
-   Save and document a final cleaned dataset, if permitted by the
    dataset's terms.
-   Add further exploratory analysis and visualizations where they
    provide useful insights.

## Author

**Farid Hassani**

https://github.com/fred5566
