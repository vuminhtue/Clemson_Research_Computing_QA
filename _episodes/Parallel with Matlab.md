---
title: "Parallel Computing in Matlab"
teaching: 20
exercises: 0
questions:
- "How to utilize multiple cores for Matlab programming"
objectives:
- "Learn about parfor"
keypoints:
- "parallel for loop"

---

- The `parfor` executes for-loop iterations in parallel on workers in a parallel pool.

Example: 

Using some intensive computing function:

## Using single core for looping:

```matlab
tic
for i =2:500
    d = abs(eig(rand(i)));
    E = d(1);
end
toc
```

```
Elapsed time is 22.101458 seconds.
```



## Using `parfor` with 2 cpus for the loop

```matlab
parpool(2)
tic
parfor i=2:500
    d = abs(eig(rand(i)));
    E = d(1);
end
toc
delete(gcp('nocreate'))
```

```
Elapsed time is 10.976068 seconds.
```
