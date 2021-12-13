# DBSCAN-Clustering-Python
Clustering Data With DBSCAN On Python
# Clustering Data With DBSCAN On Python
## Please cluster the following data with DBSCAN Algorithm
## [[3, 2, 1], [5, 5, 6], [4, 5, 5],[3, 3, 2], [7, 6, 6], [5, 5,4], [1, 0 ,1],[7, 8, 7]]


```python
from matplotlib import pyplot as plt
from sklearn.cluster import DBSCAN
import pandas as pd

# Use Pandas lib for Create Dataframe
MyData = pd.DataFrame([[7, 8, 7],
                       [3, 3, 2],
                       [5, 5, 6],
                       [3, 2, 1],
                       [1, 0, 1],
                       [5, 5, 4],
                       [7, 6 ,6],
                       [4, 5, 5]],columns=['F1', 'F2', 'F3'],index={'X1','X2','X3','X4','X5','X6','X7','X8'})
print('Show Our Data')
MyData
```
# Plotting Data
```python
fig = plt.figure(figsize=(5, 4), dpi=100)
ax = plt.axes(projection='3d')
ax = plt.axes(projection='3d')
ax.scatter3D(MyData['F1'], MyData['F2'], MyData['F3'])
```
**eps = The maximum distance between two samples for one to be considered as in the neighborhood of the other.**

**min_samples = The number of samples (or total weight) in a neighborhood for a point to be considered as a core point**

**eps = 3 && min_samples = 3**
```python
clustering = DBSCAN(eps=3, min_samples=3).fit(MyData)
MyData['clusts'] = clustering.labels_
print('Show Clustered Data')
MyData
```
# Use Matplotlib For plotting Clustered data
```python
fig = plt.figure()
ax = plt.axes(projection='3d')
ax = plt.axes(projection='3d')
ax.scatter3D(MyData['F1'], MyData['F2'], MyData['F3'], c=MyData['clusts'])
print ('Plotting Clustered Data')

print('Show Sorted by Clustered Data Label')
MyData.sort_values(by=['clusts'])
```
# Result is  = > C1=X1,X4,X7    &      C2=X5,X3,X6,X2,X8
