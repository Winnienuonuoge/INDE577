# K-Means Clustering on NBA Player Stats (2017 Season)

This project applies **K-Means clustering** to group NBA players based on their in-game statistical performance. The goal is to identify natural player segments (e.g., high scorers, role players, bench players) using unsupervised learning techniques.

---

## 1. Objective

To use K-Means clustering on numerical performance data from the 2017 NBA season to group players into meaningful categories based on their play style, usage, and production.

---

## 2. Dataset

- **Source**: Kaggle — `Seasons_Stats.csv`
- **Filtered Year**: 2017
- **Preprocessing**:
  - Removed non-numeric columns: `Player`, `Pos`, `Tm`, `Year`, etc.
  - Filled missing values with 0
  - Scaled numerical features using `StandardScaler`
  - Applied PCA for 2D visualization

---

## 3. Methodology

- **Clustering Algorithm**: `KMeans` from Scikit-learn
- **Number of Clusters**: 4
- **Dimensionality Reduction**: PCA (2 components)
- **Evaluation**: Visual inspection of cluster separation and player samples

---

## 4. PCA Cluster Visualization

- The PCA plot shows four distinct clusters with moderate separation.
- Cluster 0 appears to span more broadly along PC1, suggesting more variance in star-level roles.
- Clusters 1 and 2 are more compact and statistically homogeneous.

---

## 5. Cluster Interpretation

### Cluster 0 – Star-Level / High-Usage Players
- **Examples**: Giannis Antetokounmpo, LaMarcus Aldridge, Carmelo Anthony
- High in **PTS**, **AST**, **TRB**
- Likely primary scorers or all-around starters

### Cluster 1 – Bench / Low-Usage Players
- **Examples**: Quincy Acy, Ron Baker, Wade Baldwin
- Low minutes and production
- Likely backup players, developmental or injury-limited

### Cluster 2 – Mid-Tier / Role Contributors
- **Examples**: Tony Allen, Al-Farouq Aminu
- Moderate stats across the board
- Rotational defenders, 3-and-D players, utility starters

### Cluster 3 – Likely Outliers or Specialists
- Not shown in sample tables
- Based on PCA spread, may include rookies, one-dimensional roles, or statistical outliers

---

## 6. Conclusion

- K-Means effectively grouped NBA players into meaningful categories:
  - High-impact starters
  - Mid-tier role players
  - Low-usage bench players
- PCA helped validate cluster separability visually.
- The model can support:
  - Player comparison & scouting
  - Team-building strategies
  - Unsupervised segmentation in sports analytics
