# K-means-Implementation-using-Spark
Implementation of k-means algorithm, using spark and python.



**The Algorithm:**

1. Randomly select k centroids (by calling the "kRandom" func).
2. While the number of iterations is smaller than I and there is no convergence: perform the mapper and reducer function. 

**Main parts and functions:**

1. **read_csv:** this functions reads the file and returns the following objects:
points - list of lists, each internal list represtns a points with normalized coordinates. 
pointsrdd - RDD object of points
labels_true - a list containing the true labels of the clusters for each point

2. **centroidForPoints:** receives a point as input and list of k centroids, returns the index of the centroid with the smallest distance between it
and the given point. 
2. **Mapper:** for each point it returns tuple with the index of the centriod assigned for the point and a tuple containing the point itself and "1".  
-> mapper = [(centroid_index, (point,1)),(centroid_index2, (point2,1)),....]
3.**reducer:** returns for each index of a centroid the new centroid received by calculating the mean of the points assigned to this centroid. 


**model evaluation:**
We evaluated the model using 2 different measurements - "CH" and "ARI".
the results are documented in the ipynb file, according to different k values:
**iris dataset**: as we can see, according to "CH" measurement the best partition is according to k=2,
an according to "ARI" the best one is k=3.
**glass dataset:** as we can see, according to "CH" measurement the best partition is k=2, and according to ARI it's the same.
Anyway, the values of the measuremnets are pretty low and it indicates of low performances.

