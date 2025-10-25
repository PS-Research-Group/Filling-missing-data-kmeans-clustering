# 🧠 Filling Missing Data Using K-Means Clustering (Workout Dataset)

This notebook demonstrates how to **fill missing labels** in the `intensity` column using **unsupervised K-Means clustering** based on numeric workout features.  
By clustering similar workouts and mapping each cluster to the most common known intensity, missing values are imputed intelligently without manual labeling.

---

## 📓 Notebook
- `KMeans_Clustering.ipynb` — main notebook file
- `Workout.csv` — dataset used in the notebook (should be in the same folder)

---

## 🧮 Overview

The workflow:
1. **Load data** using Pandas.
2. **Inspect missing values** to identify incomplete rows.
3. **Extract numeric features** (`duration_min`, `calories`) and target (`intensity`).
4. **Scale features** using `StandardScaler` for balanced clustering.
5. **Determine cluster count** based on the number of known intensity classes.
6. **Fit K-Means model** to the scaled features.
7. **Map clusters → most common known intensity**.
8. **Impute missing `intensity`** values using that mapping.
9. **Visualize** the clusters with Seaborn to verify grouping quality.

Example printed output from the notebook:
```
Number of clusters based on known intensity values: 3
✅ NaNs filled successfully!
Remaining NaNs: 0
```

## 📊 Visualization

At the end, the notebook generates a scatter plot of workouts:

```python
sns.scatterplot(data=df, x="duration_min", y="calories", hue="cluster")
plt.title("Workout Clusters by Duration and Calories")
plt.show()
```
This shows how workouts with similar durations and calories are grouped together.

## 🧩 Requirements
Install dependencies before running:


```pip install pandas numpy scikit-learn matplotlib seaborn```

## ▶️ How to Run
1. Ensure both KMeans_Clustering.ipynb and Workout.csv are in the same folder.

2. Open the notebook in Jupyter or VS Code.

3. Run all cells in order.

## 📁 Expected Columns in `Workout.csv`

| Column        | Type     | Description                                                  |
|----------------|----------|--------------------------------------------------------------|
| `duration_min` | float    | Workout duration in minutes                                 |
| `calories`     | float    | Calories burned                                             |
| `intensity`    | category | Target column (`Low`, `Medium`, `High`) — may contain NaNs  |


## 🧠 Example Use Case
This technique can be applied to real-world fitness tracking, sensor data, or user activity datasets to infer missing labels such as workout type or intensity from measurable features.

## 📜 License
This project is licensed under the MIT License.