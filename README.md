# Discovering Smuggling Ports and Unconventional Points of Interest Using Machine Learning

This project was developed as my **Bachelor's thesis in Computer Science** at **Alzahra University**.

The project explores the use of **machine learning and unsupervised clustering** to identify unconventional spatial patterns and potential Points of Interest (POIs) from maritime vessel tracking data.

> **Important:** The detected locations should not be interpreted as confirmed smuggling ports or ground-truth smuggling locations. They represent unconventional or potentially suspicious spatial patterns identified through the applied data analysis and clustering approach.

---

## Project Overview

Maritime vessel tracking data can contain spatial and behavioral patterns that may be difficult to identify through manual inspection.

This project uses **Automatic Identification System (AIS)** vessel tracking data and applies an unsupervised clustering approach to discover unconventional vessel activity and spatial patterns.

The main workflow includes:

* Data cleaning and preprocessing
* Exploratory analysis
* Handling missing and invalid values
* Filtering vessel movement data
* Feature preparation and standardization
* Spatial clustering using **HDBSCAN**
* Identification of Unconventional Points of Interest (UPOIs)
* Interactive visualization of the detected clusters

---

## Dataset

The project uses AIS vessel tracking data obtained from **MarineCadastre**.

### Study Period

**December 31, 2020 – March 31, 2021**

### Area of Interest

The analysis was performed over the following geographical region:

```text
[-131.929, 26.086, -111.225, 28.618]
```

The original dataset contained approximately **385,560 records**.

After preprocessing and filtering, the data was reduced through several stages before clustering and analysis.

### Dataset Availability

The processed dataset used in the analysis is **not included in this repository because of its large file size**.

The main notebook expects the processed dataset to be available locally as:

```text
vesselDataSetFinal.csv
```

Therefore, to reproduce the complete analysis, the dataset should be obtained separately and placed in the same directory as the notebook.

---

## Data Preprocessing

Several preprocessing steps were performed to prepare the AIS data for analysis.

These included:

* Removing irrelevant attributes
* Handling missing values
* Creating an indicator for missing draft values
* Removing physically unrealistic vessel speed observations
* Filtering observations based on **Speed Over Ground (SOG)**
* Preparing latitude and longitude features
* Standardizing numerical features before clustering

The following vessel-identifying attributes were excluded from the clustering process:

* `CallSign`
* `VesselName`
* `MMSI`

The analysis focused primarily on **spatial and movement patterns rather than vessel identity**.

---

## Methodology

### HDBSCAN

The main clustering algorithm used in this project is **HDBSCAN (Hierarchical Density-Based Spatial Clustering of Applications with Noise)**.

HDBSCAN was selected because vessel movement data may contain clusters with different densities and shapes, while the number of meaningful clusters is not known in advance.

The clustering process primarily used:

* Latitude
* Longitude
* Standardized numerical features

The main clustering configuration included:

```text
min_cluster_size = 10
```

HDBSCAN also identifies observations that do not belong to meaningful clusters as **noise**, which is useful when exploring unconventional spatial patterns.

---

## Unconventional Points of Interest

The objective of the clustering process was **not to directly classify locations as smuggling ports**.

Instead, the analysis identifies **Unconventional Points of Interest (UPOIs)** based on unusual spatial and vessel movement patterns.

Different filtering conditions were investigated during the analysis.

For example, using:

```text
SOG < 5
```

resulted in **917 identified UPOIs** in the analyzed data.

These points should be considered **candidate locations for further investigation**, rather than confirmed illegal activity.

---

## Results and Visualizations

The project includes interactive HTML visualizations of the detected spatial patterns.

### Cluster Map

`cluster_map.html`

An interactive map showing the detected spatial clusters.

### Heatmap

`heatmap_clusters.html`

A heatmap showing the spatial distribution of the detected activity and clusters.

> **Note:** The interactive maps rely on external web map tiles for their basemap. Therefore, the basemap may not be displayed correctly in some network environments, while the underlying project visualizations remain part of the generated HTML files.

---

## Repository Structure

```text
Bachelor-s-Thesis-in-Computer-Science/
│
├── README.md
├── smuggling_poi_detection.ipynb
├── cluster_map.html
└── heatmap_clusters.html
```

### Files

| File                            | Description                                 |
| ------------------------------- | ------------------------------------------- |
| `README.md`                     | Project documentation                       |
| `smuggling_poi_detection.ipynb` | Main analysis and machine learning workflow |
| `cluster_map.html`              | Interactive cluster visualization           |
| `heatmap_clusters.html`         | Interactive heatmap visualization           |

---

## Technologies and Libraries

* Python
* Pandas
* NumPy
* Scikit-learn
* HDBSCAN
* Matplotlib
* Seaborn
* Jupyter Notebook
* folium

---

## Limitations

Several limitations should be considered when interpreting the results:

* The detected UPOIs are **not confirmed smuggling locations**.
* AIS data may contain missing, inaccurate, or anomalous observations.
* The analysis relies primarily on spatial and vessel movement characteristics.
* The selected filtering thresholds can affect the resulting POIs.
* Clustering results depend on the selected algorithm parameters.
* Additional domain knowledge and investigation would be required to determine whether an identified location represents legitimate or suspicious maritime activity.

---

## Conclusion

This project demonstrates how **unsupervised machine learning and spatial data analysis** can be applied to maritime vessel tracking data to discover unconventional spatial patterns.

Rather than directly classifying locations as smuggling ports, the approach identifies **candidate Points of Interest** that may be useful for further analysis and investigation.

The project combines data preprocessing, exploratory analysis, density-based clustering, anomaly-oriented analysis, and interactive visualization to investigate patterns in real-world AIS data.

---

## Author

**Fatemeh Ghorbani**

B.Sc. in Computer Science
Alzahra University

GitHub: [fateme-ghorbani](https://github.com/fateme-ghorbani)
