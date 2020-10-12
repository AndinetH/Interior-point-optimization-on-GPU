# Interior-point-optimization-on-GPU
Interior point optimization on GPU. A code I wrote in 2016 to solve an interior point (IP) optimization problem on GPU (Jetson tx1). The focus is more on translating an algorithm from literature into a code snippet that should solve the IP problem and run faster as compared to a Matlab version ( targeted for a regular laptop).   

I have included below a screenshot of the actual output. In the output reported below, the variables x[0] and x[1] represent the optimal dimensions of the major and minor axes of a circumscribing ellipse to a given region. The time it took for various tasks in a single iteration are represented as 
MM: to perform matrix-matrix product, 

LU: to perform LU decomposition, 

Mem: to copy n elements from a vector x in host memory space to a vector y in GPU memory space, 

H2: to compute the Euclidean norm of the vector x.


![Output Result (screenshot)](https://github.com/AndinetH/Interior-point-optimization-on-GPU/blob/main/Screenshot%20from%202016-06-23%2008_25_51.png)


The code uses cublas as well as magma packages/libraries. Send an email for the full code. 

# include <stdio.h>
# include <stdlib.h>
# include <math.h>
# include <cuda_runtime.h>
# include "cublas_v2.h"

# include "magma.h"
# include "magma_lapack.h"
