# Discovering Smuggling Ports and Unconventional Points of Interest Using Machine Learning

This project was developed as my **Bachelor's thesis in Computer Science** at **Alzahra University**.

The goal of this project was to explore whether **machine learning and unsupervised clustering techniques** could be used to identify **unconventional maritime activity and potential Points of Interest (POIs)** from vessel tracking data.

> **Important:** The detected locations should not be interpreted as confirmed smuggling ports or ground-truth smuggling locations. They represent unconventional or suspicious patterns identified through the applied data analysis and clustering approach.

---

## Project Overview

Maritime vessel tracking data can contain patterns that are difficult to identify through manual inspection alone. This project investigates vessel movement data from the **Automatic Identification System (AIS)** and applies unsupervised machine learning to discover spatial patterns and unconventional vessel activity.

The main approach focuses on clustering vessel positions based primarily on their geographical coordinates and examining the resulting clusters and vessel behavior.

The workflow includes:

1. Data collection and preparation
2. Data cleaning and preprocessing
3. Exploratory analysis of vessel movement data
4. Filtering invalid or irrelevant observations
5. Feature preparation and standardization
6. Spatial clustering using **HDBSCAN**
7. Identification of unconventional Points of Interest (UPOIs)
8. Visualization of detected clusters and spatial patterns

---

## Dataset

The project uses AIS vessel tracking data from **MarineCadastre**.

### Study Period

**December 31, 2020 – March 31, 2021**

### Area of Interest

The analysis was performed over a defined geographical region in the Gulf of Mexico:

```text
[-131.929, 26.086, -111.225, 28.618]
```

The original dataset contained approximately **385,560 records**.

After preprocessing and filtering, the dataset was reduced through several stages before clustering and analysis.

---

## Data Preprocessing

Several preprocessing steps were performed to prepare the AIS data for analysis.

These included:

* Removing irrelevant or unnecessary attributes
* Handling missing values
* Creating an indicator for missing draft values
* Removing physically unrealistic vessel speed observations
* Filtering vessel movement data based on **Speed Over Ground (SOG)**
* Preparing latitude and longitude features for clustering
* Standardizing numerical features before applying the clustering algorithm

Some vessel-identifying attributes, such as:

* `CallSign`
* `VesselName`
* `MMSI`

were excluded from the clustering process because the main focus of this analysis was on **spatial and movement patterns rather than vessel identity**.

---

## Methodology

### HDBSCAN

The main clustering algorithm used in this project is **HDBSCAN (Hierarchical Density-Based Spatial Clustering of Applications with Noise)**.

HDBSCAN was selected because maritime movement data does not necessarily form clusters with predefined shapes or densities, and the number of clusters is not known in advance.

The clustering process was performed using:

* Latitude
* Longitude
* `StandardScaler`
* HDBSCAN

The main clustering configuration included:

```text
min_cluster_size = 10
```

HDBSCAN also allows observations that do not belong to meaningful clusters to be classified as **noise**, which is useful when analyzing unusual spatial patterns.

---

## Unconventional Points of Interest

The purpose of the clustering stage was not to directly label locations as "smuggling ports."

Instead, the analysis identifies **Unconventional Points of Interest (UPOIs)** based on unusual spatial and movement patterns.

Different filtering conditions were investigated during the analysis.

For example, using:

```text
SOG < 5
```

resulted in **917 identified UPOIs** in the analyzed data.

These points should be interpreted as **candidate areas for further investigation**, rather than confirmed illegal activity.

---

## Results

The analysis produced spatial clusters and unconventional points of interest that can be explored through interactive visualizations.

Two interactive HTML visualizations are included in this repository:

### Cluster Map

`cluster_map.html`

An interactive visualization of the detected spatial clusters.

### Heatmap

`heatmap_clusters.html`

A heatmap visualization showing the spatial distribution of the detected activity and clusters.

> The interactive maps use a web-based map tile provider for the basemap. Therefore, their map background may not be available in every environment depending on network access and tile-service availability.

---

## Repository Structure

```text
Bachelor-s-Thesis-in-Computer-Science/
│
├── README.md
├── smuggling_poi_detection.ipynb
├── vesselDataSetFinal.csv
├── cluster_map.html
└── heatmap_clusters.html
```

### Files

| File                            | Description                                  |
| ------------------------------- | -------------------------------------------- |
| `README.md`                     | Project documentation                        |
| `smuggling_poi_detection.ipynb` | Main analysis and machine learning workflow  |
| `vesselDataSetFinal.csv`        | Processed vessel dataset used in the project |
| `cluster_map.html`              | Interactive cluster visualization            |
| `heatmap_clusters.html`         | Interactive heatmap visualization            |

---

## Technologies and Libraries

The project was implemented using Python and the following tools and libraries:

* Python
* Pandas
* NumPy
* Scikit-learn
* HDBSCAN
* Matplotlib
* Seaborn
* Jupyter Notebook

---

## Limitations

There are several important limitations to consider when interpreting the results.

* The detected UPOIs are **not confirmed smuggling locations**.
* AIS data may contain missing, inaccurate, or anomalous observations.
* The analysis is based primarily on spatial and vessel movement characteristics.
* The selected filtering thresholds can affect the resulting POIs.
* Density-based clustering results depend on the selected parameters.
* Further investigation and domain expertise would be required to determine whether an identified location corresponds to legitimate or suspicious maritime activity.

---

## Conclusion

This project demonstrates how **unsupervised machine learning and spatial data analysis** can be applied to maritime vessel tracking data to discover unconventional spatial patterns.

Rather than attempting to directly classify locations as smuggling ports, the proposed approach generates **candidate Points of Interest** that can potentially support further analysis and investigation.

The project combines data preprocessing, exploratory analysis, spatial clustering, anomaly-oriented analysis, and interactive visualization to explore patterns within real-world AIS data.

---

## Author

**Fatemeh Ghorbani**

B.Sc. in Computer Science
Alzahra University

GitHub: [fateme-ghorbani](https://github.com/fateme-ghorbani)
