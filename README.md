# K-means Clustering with Parallelization

This repository contains a Python implementation of the K-means clustering algorithm, with both a non-parallel version and an optimized parallel version using `concurrent.futures` for multi-threading. The parallelization is applied to the assignment step of the K-means algorithm, where data points are assigned to the nearest centroid. The parallel version divides the data into chunks and assigns each chunk to a separate thread.

## Algorithm and Parallelization Method

### Non-parallel K-means:
The K-means algorithm involves two main steps:
1. **Assignment Step**: Each data point is assigned to the nearest centroid.
2. **Update Step**: The centroids are updated by computing the mean of the data points assigned to each centroid.

In the non-parallel implementation, the assignment and update steps are done sequentially.

### Parallel K-means:
The parallel version of K-means optimizes the assignment step using multi-threading. The data is split into chunks, and the assignment of data points to centroids is performed concurrently across multiple threads. This speeds up the algorithm by leveraging multiple CPU cores.

The parallelization is done using `ThreadPoolExecutor` from the `concurrent.futures` module, where each chunk of data is processed in parallel.

## Instructions to Reproduce the Results

1. **Clone this repository**:
   If you don't have Git installed, you can manually download the ZIP from GitHub and extract it to your local machine.

2. **Install Required Libraries**:
   Install the necessary Python packages using the following commands:
   ```bash
   pip install numpy scikit-learn
   ```

3. **Run the Algorithm**:
   - The code generates synthetic datasets for benchmarking the K-means algorithm.
   - You can run the script directly to test the non-parallel and parallel versions of the K-means algorithm.
   - The dataset is generated using `make_blobs` from `scikit-learn` with 70,000 samples, 10 features, and 3 clusters for the Gaussian dataset. You can modify the number of samples and features as needed.

   Run the code with:
   ```bash
   python kmeans_parallel.py
   ```

   The results will be printed to the console, showing the time taken by the non-parallel and parallel versions of the algorithm.

4. **Data Format**:
   - The data used for benchmarking is synthetic, generated in the script itself using `make_blobs`.
   - If you'd like to use your own dataset, ensure the data is a 2D NumPy array, where rows represent data points and columns represent features.

## Explanation of the Parallel Part

The parallelization in this implementation is applied to the **assignment step** of the K-means algorithm. Instead of computing the nearest centroid for all data points in a single loop, the data is split into chunks, and the assignment is done in parallel across multiple threads. This reduces the overall computation time, especially when dealing with large datasets.






