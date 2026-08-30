# ECE-2112-PA2

Paulene Anne V. Pereña <br>
2ECE-D

This repository contains the Programming Assignment 2 for the course Advanced Computer Programming (ECE2112).
This project consists of three Python problems assigned to Module 2: NumPy.

The functions given where used keme keme 

* The `import numpy as np` function loads the NumPy library into the code in order for mathematical tools and
  multidimensional arrays to run. The `import` statement brings an external library into the code, in this case `numpy`.
  Additionally, `as np` creates an alias for the library so it can be called more efficiently with reduced typing.

insert the np.save
# A. REPRODUCIBLE NORMALIZATION PROBLEM
The problem asks to create a 5x5 integer ndarray named X. It is asked to be normalized, with its name X_normalized, 
under the standardization formula, identifying the mean and the population standard deviation.  

* The `np.random.seed(2112)` sets as the starting point to produce the exact same sequence of numbers every time the
code is run. The `seed()` was used to make the result reproducible, as it functions to generate an output with the same
sequence of random numbers.
 
* The `X = np.random.randint(10, 101, size=(5, 5))` is composed of parts that function as a generator of a matrix filled
  with random integers. <br>
    * `10` --> It functions as the inclusive lower bound for the set of numbers to be produced while making it the smallest
         possible number to be generated.
    * `101` --> It functions as the exclusive upper bound for the set of numbers to be generated, whereas the numbers to be
        produced must be less than it.
    * `size=(5, 5)` --> It functions as a parameter to create a 2D array matrix. The first 5 is defined as the rows while the
       second 5 is defined as the columns.

* The `mean = np.mean(X)` is used because the standardization formula requires the center baseline of the raw data, or the
  middle value, which makes the `mean()` useful. It adds all twenty-five individuals inside the matrix `X` and divides the
  sum by the total element count.
    ```
    mean = np.mean(X)
    mean

    This evaluates to the mean of the 2D array, which is `46.36.`
    ```

* The `std = np.std(X)` is used because the standardization formula looks for the dispersion of the baseline of the raw data or how far
  each data point is separated from the others. The `std()` functions to calculate the standard deviation of the raw data
  in relation to the mean.
    ```
    std = np.std(X)
    std

    This evaluates to the standard deviation of the 2D array, which is `25.864075471588002 approximately 26.`
    ```

  When the baseline requirements were found, `mean()` and `std()`, the function is asked to be normalized using element-wise array operations.
  The syntax `(X - mean)` functions to transfer the data by subtracting 46.36 from every element in the data, while `/std` divides the result by
  25.864075471588002. These processes transform the matrix layout to a new data set where the new mean is centered at `0,` and the standard deviation
  is scaled to `1`.
  ```
  X_normalized = (X-mean)/std
  X_normalized

  ```

  # B. CUBES DIVISIBLE BY 4
  The problem asks to create the first 100 positive integers, cube each element, and reshape the result into a 10 x 10 matrix. Ensure that it displays   the shape of C, the array div_by_4, and the total number of selected elements (50), and that the first and last elements are 8 and 1 000 000,          respectively.

  * The functions were called using an arbitrary variable 'C' as it is asked by the problem.
 
  * The `C = np.arange(1, 101)` is used as the problem requires the initialization of an ordered sequence of numbers. The `arange(0` is a function         that generates a one-dimensional array from the inclusive lower bound of 1 to its exclusive upper bound of 101. This function evaluates 100            consecutive integers from 1 to 100 and assigns them to the arbitrary variable C.
    ```
    C = np.arange(1, 101)
    C

    This evaluates to an array of values from 1 to 100.
    ```

  * The `C = C**3` 
  

  
  

  
  
    
