# ECE-2112-PA2

Paulene Anne V. Pereña <br>
2ECE-D

This repository contains the Programming Assignment 2 for the course Advanced Computer Programming (ECE2112).
This project consists of three Python problems assigned to Module 2: NumPy.

The specific functions and syntax structures utilized throughout the codebase were implemented as follows:

* The `import numpy as np` function loads the NumPy library into the code in order for mathematical tools and
  multidimensional arrays to run. The `import` statement brings an external library into the code, in this case `numpy`.
  Additionally, `as np` creates an alias for the library, allowing it to be called more efficiently with reduced typing.

* The `np.save(" file name", matrix name)` is used to create a permanent local backup of the processed Numpy Arrays on the computer's local drive. Without this, the matrix created would vanish once the .ipynb file is closed.
  
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

    This evaluates to the mean of the two-dimensional array, which is 46.36.
    ```

* The `std = np.std(X)` is used because the standardization formula looks for the dispersion of the baseline of the raw data, or
  how far each data point is separated from the others. The `std()` functions to calculate the standard deviation of the raw data
  in relation to the mean.
    ```
    std = np.std(X)
    std

    This evaluates to the standard deviation of the two-dimensional array, which is 25.864075471588002, approximately 26.
    ```

  When the baseline requirements were found, `mean()` and `std()`, the function is asked to be normalized using element-wise array
  operations. The syntax `(X - mean)` functions to transfer the data by subtracting 46.36 from every element in the data, while `/std`
  divides the result by 25.864075471588002. These processes transform the matrix layout to a new data set where the new mean is centered
  at `0,` and the standard deviation is scaled to `1`.
    ```
    X_normalized = (X-mean)/std
    X_normalized

    ```

  # B. CUBES DIVISIBLE BY 4
    The problem asks to create the first 100 positive integers, cube each element, and reshape the result into a 10 x 10 matrix. Ensure that it
    displays the shape of C, the array div_by_4, and the total number of selected elements (50), and that the first and last elements are 8 and
    1 000 000, respectively.

* The functions were called using an arbitrary variable 'C' as it is asked by the problem.
 
* The `C = np.arange(1, 101)` is used as the problem requires the initialization of an ordered sequence of numbers. The `.arange()` is a function
  that generates a one-dimensional array from the inclusive lower bound of 1 to its exclusive upper bound of 101. This function evaluates 100
  consecutive integers from 1 to 100 and assigns them to the arbitrary variable C.
    ```
    C = np.arange(1, 101)
    C

    This evaluates to an array of values from 1 to 100.
    ```

* The `C = C**3` is used to perform the problem requirement to create data in its cube form. The syntax applies an element-wise cubic
  transformation, cubing each number inside the array natively. The cube's values transformed the array, having 1 as the smallest and
  1 000 000 is the largest.
    ```
    C = C**3
    C

    This evaluates to an array containing the first 100 positive integers, each raised to the cube.

    ```

* The `C = C.reshape(10, 10)` is used to change the spatial orientation of the data layout. The function `.reshape()` reconfigures the 100 elements
  into a two-dimensional grid without changing their number or sequence. The parameters `(10, 10)` rearranged the vector layout into a matrix with 10
  horizontal rows and 10 vertical columns, which is then assigned to the arbitrary variable C.
    ```
    C = C.reshape(10, 10)
    C

    This evaluates to the cubes of the first 100 positive integers, arranged in 10 horizontal rows and 10 vertical columns.

    ```

* The `C.shape` is used to verify that the spatial dimension of the layout was successfully altered. The `.shape` reads out the structural
  dimensions of the array layout as a tuple representing the rows and columns.
    ```
    C.shape

    (10, 10)

    ```

* The function was named under `div_by_4` as stated in the problem. The `C[C% ==4]` was used because the problem asked for selected elements, which
  is why the boolean operator' = =' and the modulo operator `%` were used. The expression `C%==4` evaluates every single numeric position to see if
  dividing the number by 4 leaves a remainder of zero, creating an internal grid of `True` or `False`indicators. Placing back the condition into the
  syntax, extracting only the elements on which it remains true.
    ```
    div_by_4 = C[C%4==0]
    div_by_4

    This evaluates to an array divisible by 4, with 8 being the smallest and 1 000 000 being the largest.
    ```

* The `P1 = div_by_4.size` is used to check the volume of filtered data points. The `.size` property counts the total number of items stored inside
  the array regardless of its dimensionality or shape. This counts the filtered elements that met the divisibility condition.
    ```
    P1 = div_by_4.size
    P1

    50
    ```

# C. Above-Mean Squares Problem
  The problem asks for a 6 x 6 matrix, called under an arbitrary variable S, containing the squares of the first 36 positive integers in increasing order. 
  It also asks to compute the mean and use a boolean to filter for elements greater than the mean.

* The `S = np.arange (1, 37)` is used because the problem required initializing an ordered sequence of numbers. The `.arange()` function generates a one-dimensional
  array from the first inclusive value (lower bound) of 1 to the last exclusive value (upper bound) of 37. This evaluates to a vector containing exactly 36 consecutive
  integers ranging from 1 to 36 declared in the arbitrary variable S.
    ```
    S = np.arange(1, 37)
    S

    This evaluates to an array ranging from 1 to 36.

    ```

* The `S = np.power(S, 2) is used because the problem requires transforming the data exponentially, which is why `.power()` is used as the syntax applies an element-wise
  transformation across the vector, raising each data point to the power of 2.
    ```
    S = np.power(S, 2)
    S

    This evaluates to the square of S.

    ```

* The `S = S.reshape(6, 6)` is used to change the spatial orientation of the data layout. The function reconfigures the first 36 positive integers into a two-dimensional
  grid without altering their sequence. The parameter `(6, 6)` is used to directly rearrange the values into a matrix with 6 rows and 6 columns into the arbitrary variable S.
     ```
    S = S.reshape(6, 6)
    S

    This evaluates to a 6 × 6 matrix of the squares of the first 36 positive integers.

    ```

* The ` S.shape` is used to verify whether the spatial dimensions applied were successfully altered. It is used to properly read out the array's structural dimensions as
  a tuple representing the 6 rows and 6 columns.
    ```
    S.shape

    (6, 6)
    ```

* The `S_mean = np.mean(S)` is used  to find the baseline of the data or its average.    The `.mean()` function adds the thirty-six individual integers and divides the sum by
  the total element count, and stores it under S_mean.
    ```
    S_mean = np.mean(S)
    S_mean

    450.1666666666667
    ```

* The `above_mean = S[S>S_mean]` is used since the problem asked for a filtered value that satisfies the condition that it must exceed the calculated average or mean. The `S > S_mean` evaluates every single data point to see if the        number is greater than the mean, which is 450.1666666666667, creating an internal indicator whether the values are True or False. Once filtered, the elements that were true were stored in a new arbitrary variable called above_mean.
    ```
    above_mean = S[S>S_mean]
    above_mean

    array([ 484,  529,  576,  625,  676,  729,  784,  841,  900,  961, 1024,
       1089, 1156, 1225, 1296])
    ```

* The `P3 = above_mean.size` is used to check the volume of filtered data points found. The '.size` property reads the total number of data points stored in an array from memory, regardless of its dimensionality or layout.
    ```
    P3 = above_mean.size
    P3

    15
    ```
# Version History

* 30 August 2026 - The README repository was created, and the initial .ipynb file was uploaded.
* 31 August 2026 - The README file is continuously being updated.
* 01 September 2026 - The README file is still being updated, and the .ipynb file was uploaded.
  

  
  

  
  
    
