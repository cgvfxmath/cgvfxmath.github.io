---
layout: post
title: "PCA"
author: "wano"
excerpt_separator: <!--more-->
tags: ['dev']
use_math: true
lastmode: 2023-04-24 13:00:00
sitemap:
  changefreq: weekly
  priority: 0.5
---

Simple PCA example using NumPy<!--more-->

```python
import numpy as np

# samples
# https://www.kaggle.com/xvivancos/image-compression-using-pca
data = [[2.5, 2.4],
        [0.5, 0.7],
        [2.2, 2.9],
        [1.9, 2.2],
        [3.1, 3.0],
        [2.3, 2.7],
        [2.0, 1.6],
        [1.0, 1.1],
        [1.5, 1.6],
        [1.1, 0.9]]

number_of_samples = len(data)

# D: data matrix
D = np.array(data)

# centering
D = D - D.mean()

# C: covariance matrix
C = np.cov(D.T)
n = len(C) # feature count

# eigenvalues & eigenvectors of C
eigen_values, eigen_vectors = np.linalg.eig(C)

# from increaing order to decreasing order
sorting_index = np.argsort(eigen_values)[::-1]
eigen_values = eigen_values[sorting_index]
eigen_vectors = eigen_vectors[sorting_index]

# v: principal axes
v = []
for i in range(n):
	v.append(eigen_vectors[:,i]) # the i-th column

# data restoration test
restored = []
for i in range(number_of_samples):
	p = D[i] # original point
	q = np.zeros_like(p) # restored point
	for j in range(n):
		projected_distance = np.dot(p, v[j])
		q += projected_distance * v[j]
	q = q.tolist()
	q = [round(qi, 2) for qi in q]
	restored.append(q)
	print(p, q)
```


