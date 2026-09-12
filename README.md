# Hyades Star Cluster Analysis

This project uses Python and machine learning to analyze a large astronomical dataset and identify likely members of the Hyades star cluster.
The analysis works with **100,000 stellar observations and 26 variables**, requiring data cleaning, feature engineering, exploratory analysis, feature standardization, visualization, and unsupervised clustering.

## Project Background

### What is Gaia?

Gaia is a European Space Agency space mission designed to measure the positions, distances, motions, and brightness of stars with very high precision. Its observations produce large datasets containing multiple measurements for individual stars, making Gaia data well suited for computational and statistical analysis.

### What is the Hyades?

The Hyades is a nearby group of stars that formed together and therefore share similar properties and motion through space.
A dataset covering the region also contains many unrelated stars, known as field stars. The challenge in this project was to use measured stellar properties to distinguish likely Hyades members from the surrounding stellar population.
This creates a practical clustering problem: **can stars belonging to the same physical population be identified from a large dataset using their numerical characteristics?**

## Skills Demonstrated

- Python
- Pandas and NumPy
- Data cleaning and preprocessing
- Feature engineering
- Exploratory data analysis
- Matplotlib and Seaborn visualization
- Feature standardization with Scikit-learn
- Unsupervised machine learning
- K-means clustering
- SciPy curve fitting
- Working with large, multidimensional scientific datasets

## Dataset

The project analyzes **100,000 observations across 26 variables** from Gaia data.
The variables include measurements such as:

- sky position
- parallax, which is related to stellar distance
- proper motion
- radial velocity
- brightness and color measurements
- measurement uncertainties
- astrometric quality indicators

Working with the dataset required selecting relevant variables, handling missing measurements, filtering unreliable observations, creating new features, and preparing variables with different numerical scales for analysis.
The dataset used by the notebook is included as `GaiaHyades.csv`.

## Analysis Workflow

### 1. Data Cleaning

The Gaia data were prepared for analysis by identifying the measurements needed for each stage of the project and removing observations with missing values where necessary.
Astrometric quality measurements were also considered when filtering the data so that unreliable stellar observations would not have an unnecessary influence on the analysis.

### 2. Feature Engineering

New variables were created from the original Gaia measurements to support the analysis.
This included calculating total proper motion from the proper-motion measurements in right ascension and declination.
Photometric variables were also prepared for the color-magnitude analysis, including stellar color and absolute G magnitude.

### 3. Exploratory Data Analysis

The stellar measurements were explored using several types of visualizations, including:

- distributions and histograms
- scatter plots
- correlation heatmaps
- proper-motion diagrams
- color-magnitude diagrams

These visualizations helped identify patterns in the data and determine which variables could be useful for distinguishing the Hyades population from surrounding stars.
A Gaussian curve was also fitted to the parallax distribution using SciPy to examine the distribution of stellar distance measurements.

### 4. Feature Standardization

The variables used for clustering, such as radial velocity, parallax, and proper motion, are measured using different units and numerical scales.
`StandardScaler` from Scikit-learn was used to standardize these features before clustering so that variables with larger numerical values would not dominate the analysis.

### 5. Clustering Method Selection

Different clustering approaches were studied when considering how to separate likely Hyades members from surrounding field stars.
K-means was selected for the final analysis as a practical unsupervised learning method for grouping observations using multiple standardized numerical features.
The final project therefore focuses on implementing and interpreting K-means clustering rather than implementing and comparing multiple clustering algorithms.

### 6. K-Means Clustering

K-means clustering was applied using standardized measurements of:
- radial velocity
- parallax
- total proper motion
The model divided the observations into **10 clusters**.
The resulting groups were then investigated using additional stellar measurements to determine which cluster most closely represented the expected properties of the Hyades.
This allowed the analysis to move from a large dataset containing many unrelated stars to a smaller candidate population with similar motion and distance characteristics.

### 7. Cluster Analysis and Visualization

The clustering results were examined across combinations of:
- proper motion
- parallax
- radial velocity
- sky position
- photometric measurements

The selected candidate cluster had a mean parallax of approximately **20.61 mas** and a mean radial velocity of approximately **33.42 km/s**.
The identified candidate stars were then examined using color-magnitude diagrams to study the stellar sequence of the likely Hyades population.

## Tools and Libraries

- **Python** — primary analysis language
- **Pandas** — data loading and manipulation
- **NumPy** — numerical operations
- **Matplotlib** — data visualization
- **Seaborn** — statistical visualization
- **Scikit-learn** — feature standardization and K-means clustering
- **SciPy** — curve fitting
- **CMasher** — visualization support
- **Google Colab** — notebook environment

## Repository Structure

```text
Hyades-star-cluster-analysis/
├── GaiaHyades.csv
├── hyades_analysis.ipynb
└── README.md
```

## Project Takeaway

This project demonstrates an end-to-end Python data analysis workflow using a large real-world scientific dataset.
Starting with **100,000 observations**, the project required cleaning and preparing data, creating useful features, exploring relationships visually, standardizing variables, applying unsupervised machine learning, and interpreting the resulting clusters.

Although the application is astronomy, the analytical workflow is transferable to other data problems involving large datasets, multidimensional observations, segmentation, pattern identification, and exploratory analysis.
