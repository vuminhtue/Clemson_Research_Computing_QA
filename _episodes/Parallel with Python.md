---
title: "Parallel Computing in Python"
teaching: 20
exercises: 0
questions:
- "How to utilize multiple cores for Pythopn programming"
objectives:
- "Learn multiprocessing package"
keypoints:
- "multiprocessing in loop"

---

- The `multiprocessing` package is a package that supports spawning processes using an API similar to the threading module

Example: 

Using some intensive computing function:

This function generates a square matrix of uniformly distributed random numbers, finds the corresponding (complex) eigenvalues and then selects the eigenvalue with the largest modulus. The dimensions of the matrix and the standard deviation of the random numbers are given as input parameters.

```python
import numpy as np

def max_eig(N):
    d = np.random.rand(N,N)
    E = np.linalg.eig(d)
    return abs(E[0][1]) 
```

Check available cores/processors using multiprocessing package:

```python
import multiprocessing as mp
print("Number of processors: ", mp.cpu_count())
```

## Using single core for looping:

```python
%%time
for i in range(2,500):
    max_eig(i)
```

```
CPU times: user 1min 11s, sys: 55.4 s, total: 2min 6s
Wall time: 31.7 s
```



## Using `multiprocessing` with 2 cpus for the loop

```python
%%time
with Pool(2) as p:
    p.map(max_eig, range(2,500))
```

```
CPU times: user 6.12 ms, sys: 19.1 ms, total: 25.3 ms
Wall time: 19.2 s
```
