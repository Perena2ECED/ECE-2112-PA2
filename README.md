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
      
    ```
    X = np.random.randint(10, 101, size=(5, 5))
    X

    array([[48, 11, 15, 67, 21],
       [11, 41, 13, 66, 24],
       [71, 79, 53, 67, 70],
       [77, 35, 91, 19, 96],
       [35, 54, 37, 41, 17]])
    ```

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

    array([[ 0.06340841, -1.36714726, -1.2124926 ,  0.79801809, -0.98051059],
       [-1.36714726, -0.20723725, -1.28981993,  0.75935442, -0.86451959],
       [ 0.95267275,  1.26198209,  0.25672675,  0.79801809,  0.91400909],
       [ 1.18465476, -0.43921926,  1.72594609, -1.05783793,  1.91926443],
       [-0.43921926,  0.29539042, -0.36189192, -0.20723725, -1.13516526]])
    ```
    ```
    m = np.mean(X_normalized)
    m

    0.0
    ```
    ```
    s = np.std(X_normalized)
    s

    0.9999999999999999
    ```

  # B. CUBES DIVISIBLE BY 4
    The problem asks to create the first 100 positive integers, cube each element, and reshape the result into a 10 x 10 matrix. Ensure that it
    displays the shape of C, the array div_by_4, and the total number of selected elements (50), and that the first and last elements are 8 and
    1 000 000, respectively.

* The functions were called using an arbitrary variable `C` as it is asked by the problem.
 
* The `C = np.arange(1, 101)` is used as the problem requires the initialization of an ordered sequence of numbers. The `.arange()` is a function
  that generates a one-dimensional array from the inclusive lower bound of 1 to its exclusive upper bound of 101. This function evaluates 100
  consecutive integers from 1 to 100 and assigns them to the arbitrary variable C.
  
    ```
    C = np.arange(1, 101)
    C

  array([  1,   2,   3,   4,   5,   6,   7,   8,   9,  10,  11,  12,  13,
        14,  15,  16,  17,  18,  19,  20,  21,  22,  23,  24,  25,  26,
        27,  28,  29,  30,  31,  32,  33,  34,  35,  36,  37,  38,  39,
        40,  41,  42,  43,  44,  45,  46,  47,  48,  49,  50,  51,  52,
        53,  54,  55,  56,  57,  58,  59,  60,  61,  62,  63,  64,  65,
        66,  67,  68,  69,  70,  71,  72,  73,  74,  75,  76,  77,  78,
        79,  80,  81,  82,  83,  84,  85,  86,  87,  88,  89,  90,  91,
        92,  93,  94,  95,  96,  97,  98,  99, 100])
    ```

* The `C = C**3` is used to perform the problem requirement to create data in its cube form. The syntax applies an element-wise cubic
  transformation, cubing each number inside the array. The cube's values transformed the array, having 1 as the smallest and
  1 000 000 is the largest.
  
    ```
    C = C**3
    C

    array([      1,       8,      27,      64,     125,     216,     343,
           512,     729,    1000,    1331,    1728,    2197,    2744,
          3375,    4096,    4913,    5832,    6859,    8000,    9261,
         10648,   12167,   13824,   15625,   17576,   19683,   21952,
         24389,   27000,   29791,   32768,   35937,   39304,   42875,
         46656,   50653,   54872,   59319,   64000,   68921,   74088,
         79507,   85184,   91125,   97336,  103823,  110592,  117649,
        125000,  132651,  140608,  148877,  157464,  166375,  175616,
        185193,  195112,  205379,  216000,  226981,  238328,  250047,
        262144,  274625,  287496,  300763,  314432,  328509,  343000,
        357911,  373248,  389017,  405224,  421875,  438976,  456533,
        474552,  493039,  512000,  531441,  551368,  571787,  592704,
        614125,  636056,  658503,  681472,  704969,  729000,  753571,
        778688,  804357,  830584,  857375,  884736,  912673,  941192,
        970299, 1000000])
    ```

* The `C = C.reshape(10, 10)` is used to change the spatial orientation of the data layout. The function `.reshape()` reconfigures the 100 elements
  into a two-dimensional grid without changing their number or sequence. The parameters `(10, 10)` rearranged the vector layout into a matrix with 10
  horizontal rows and 10 vertical columns, which is then assigned to the arbitrary variable C.
  
    ```
    C = C.reshape(10, 10)
    C

    array([[      1,       8,      27,      64,     125,     216,     343,
            512,     729,    1000],
       [   1331,    1728,    2197,    2744,    3375,    4096,    4913,
           5832,    6859,    8000],
       [   9261,   10648,   12167,   13824,   15625,   17576,   19683,
          21952,   24389,   27000],
       [  29791,   32768,   35937,   39304,   42875,   46656,   50653,
          54872,   59319,   64000],
       [  68921,   74088,   79507,   85184,   91125,   97336,  103823,
         110592,  117649,  125000],
       [ 132651,  140608,  148877,  157464,  166375,  175616,  185193,
         195112,  205379,  216000],
       [ 226981,  238328,  250047,  262144,  274625,  287496,  300763,
         314432,  328509,  343000],
       [ 357911,  373248,  389017,  405224,  421875,  438976,  456533,
         474552,  493039,  512000],
       [ 531441,  551368,  571787,  592704,  614125,  636056,  658503,
         681472,  704969,  729000],
       [ 753571,  778688,  804357,  830584,  857375,  884736,  912673,
         941192,  970299, 1000000]])
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

   array([      8,      64,     216,     512,    1000,    1728,    2744,
          4096,    5832,    8000,   10648,   13824,   17576,   21952,
         27000,   32768,   39304,   46656,   54872,   64000,   74088,
         85184,   97336,  110592,  125000,  140608,  157464,  175616,
        195112,  216000,  238328,  262144,  287496,  314432,  343000,
        373248,  405224,  438976,  474552,  512000,  551368,  592704,
        636056,  681472,  729000,  778688,  830584,  884736,  941192,
       1000000])
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

    array([ 1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16, 17,
       18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34,
       35, 36])
    ```

* The `S = np.power(S, 2)` is used because the problem requires transforming the data exponentially, which is why `.power()` is used as the syntax applies an element-wise
  transformation across the vector, raising each data point to the power of 2.
  
    ```
    S = np.power(S, 2)
    S

    array([   1,    4,    9,   16,   25,   36,   49,   64,   81,  100,  121,
        144,  169,  196,  225,  256,  289,  324,  361,  400,  441,  484,
        529,  576,  625,  676,  729,  784,  841,  900,  961, 1024, 1089,
       1156, 1225, 1296])
    ```

* The `S = S.reshape(6, 6)` is used to change the spatial orientation of the data layout. The function reconfigures the first 36 positive integers into a two-dimensional
  grid without altering their sequence. The parameter `(6, 6)` is used to directly rearrange the values into a matrix with 6 rows and 6 columns into the arbitrary variable S.
  
     ```
    S = S.reshape(6, 6)
    S

    array([[   1,    4,    9,   16,   25,   36],
       [  49,   64,   81,  100,  121,  144],
       [ 169,  196,  225,  256,  289,  324],
       [ 361,  400,  441,  484,  529,  576],
       [ 625,  676,  729,  784,  841,  900],
       [ 961, 1024, 1089, 1156, 1225, 1296]])
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

* The `P3 = above_mean.size` is used to check the volume of filtered data points found. The `.size` property reads the total number of data points stored in an array from memory, regardless of its dimensionality or layout.
  
    ```
    P3 = above_mean.size
    P3

    15
    ```
# Version History

* 30 August 2026 - The README repository was created, and the initial .ipynb file was uploaded.
* 31 August 2026 - The README file is continuously being updated.
* 01 September 2026 - The README file is still being updated, and the final .ipynb file was uploaded.
* 02 September 2026 - The README file is still being finalized.
* 03 September 2026 - Final touches for the README file was done and it was submitted.
  

  
  

  
  
    
