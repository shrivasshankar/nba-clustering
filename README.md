# NBA Player Archetype Clustering with Neural Networks

Discover distinct NBA player archetypes by applying deep learning and unsupervised clustering techniques to over **1.4 million player-season statistics**. This project uses a neural network autoencoder to learn compressed player embeddings, which are then clustered and visualized to reveal meaningful groups representing different playing styles.

---

## Project Overview

This project identifies NBA player archetypes by:

- Preprocessing and normalizing player season statistics
- Training a neural network **autoencoder** to compress stats into an 8-dimensional embedding space
- Applying **k-means clustering** (k=7) to group players by style
- Using **PCA** and **UMAP** for dimensionality reduction and visualization
- Analyzing clusters to find representative and distinctive players

---

## Autoencoder Architecture

- **Input:** 17 normalized player statistics (points, assists, rebounds, shooting percentages, minutes, etc.)
- **Encoder:** Two fully connected layers with ReLU activations:
  - Input → 64 neurons
  - 64 → 8 neurons (embedding dimension)
- **Decoder:** Symmetric to encoder:
  - 8 → 64 neurons with ReLU
  - 64 → original input size (linear activation)
- **Embedding size:** 8-dimensional latent space
- **Loss function:** Mean Squared Error (MSE)
- **Optimizer:** Adam (learning rate = 0.001)
- **Training details:** 10 epochs, batch size = 128

---

## Data Pipeline

1. **Data Loading & Cleaning:** Reads and filters complete cases from raw player-season data CSV.
2. **Feature Scaling:** Standardizes features with z-score normalization.
3. **Embedding Extraction:** Generates 8D embeddings from the trained autoencoder.
4. **Clustering:** Performs k-means clustering on embeddings to identify 7 player archetypes.
5. **Dimensionality Reduction:** Uses PCA (2D) and UMAP (3D) for visualization.
6. **Cluster Labeling:** Assigns descriptive archetype names:
   - Versatile Role Player
   - Sharp Shooters
   - Star Scorers
   - Dominant Bigs
   - Bench Players
   - Supporting Guards
   - Energy Bigs
7. **Player Analysis:** Identifies most representative and most distinctive players per cluster.

---

## Visualizations

- **PCA Plot:** 2D scatter of player embeddings colored by archetype.
![Perceptron Result](https://raw.githubusercontent.com/shrivasshankar/images/main/PCASCATTERPLOT.png))
- **Representative Players:** Bar plots of players closest to cluster centers and bar plots of players most unique to each archetype.
![Perceptron Result](https://raw.githubusercontent.com/shrivasshankar/images/main/ClusterBarPlot.png)).
- **Interactive 3D UMAP:** Rotatable and zoomable plot with player names and cluster colors.
![Perceptron Result](https://raw.githubusercontent.com/shrivasshankar/images/main/3dModelPlot.png))

---

## Technologies Used

- R packages:  
  - `torch` (for deep learning)  
  - `dplyr`, `tidyr`, `purrr` (data manipulation)  
  - `ggplot2`, `patchwork`, `ggrepel` (visualization)  
  - `uwot` (UMAP dimensionality reduction)  
  - `plotly` (interactive 3D visualization)  
  - `stats` (k-means clustering)  

---

## Potential Applications

- NBA player scouting and recruitment
- Historical player style classification
- Game strategy and matchup analysis

---

## Author

**Shrivas Shankar**  

---

## Usage

To run this project, ensure you have the required R packages installed and your player statistics CSV file in place from PlayerStatistics.csv on Kaggle. Then execute the R Markdown notebook to reproduce the analysis and visualizations.
https://www.kaggle.com/datasets/eoinamoore/historical-nba-data-and-player-box-scores
---

