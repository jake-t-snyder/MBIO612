### Question 1

-   Draw a concepts diagram that uses all the following R and
    programming terminology
    -   Include any missing keywords that will simplify the concepts
        diagrams

`Code`, `Variable`, `Data`, `Function`, `Call`, `Invoke`, `Type`,
`Expression`, `Assign`, `Return value`, `Character`, `Numeric`,
`Integer`, `Logical`, `Data structure`, `Arguments`, `Parameters`,
`Default values`, `Vector`, `Data Type`, `Statement`, `Comment`

For a brief description of concepts diagrams, see the following
[page](https://www.lucidchart.com/pages/concept-map). A phone picture of
simple doodle on paper with a pen will do, there is no need for a
specific tool.

We can discuss your solution next week. However, you are welcome to
attach an image here if you wish. The following syntax can be used to
include an image in a Jupyter or notebook:

<figure>
<img src="C:/Users/gails/Desktop/Concept%20Map_Practical%201.jpeg"
alt="image" />
<figcaption aria-hidden="true">image</figcaption>
</figure>

R users can, if they wish, include the URL where their image can be
found.

### Question 2

-   Rename this notebook to `Practical_1`

-   Make sure the notebook is set to use the `R` Kernel (instead of
    python by default)

    -   This is called the `runtime`

-   Test the runtime to make sure everything works, use the cell below
    to instantiate a vector `x` with any 5 values and computing its
    mean.

    -   The mean function can be invoked using `mean` and passing it `x`
    -   Assign the returned value to a variable called `y`

-   Create a cell above the current one and describe the computation
    that you just did

    -   A title that reads: “This is a markdown test”
    -   Text that reads: “the variable y contains the mean of 5 values.”
    -   Try to format (emphasize) the name `x` so it stands out.

# This is a markdown test

### the variable **y** contains the mean of 5 values

    x <- 5:10
    y <- mean (x)
    y

    ## [1] 7.5

### Question 3

In cell below: \* Crate a statement that assigns to a variable
`sec_per_min` the number of seconds in each minute \* Use the variable
`sec_per_min` to compute a new variable called `sec_per_hour`
representing the number of seconds per hour \* `sec_per_hour` is simply
the number of `sec_per_min` multilied by 60. \* Use the variable
`sec_per_hour` to compute a variable called `sec_per_day` representing
the number of seconds per day \* `sec_per_day` is simply the numebr of
`sec_per_hour` multilied by 24.

-   Use an expression to show the calculated value; i.e., the number of
    seconds in a single day.

<!-- -->

    sec_per_min <- 60
    sec_per_hour <- sec_per_min*60
    sec_per_day <- sec_per_hour*24
    sec_per_day

    ## [1] 86400

### Question 4

-   Recall that `c` creates atomic vectors

-   What does the following create?

    -   Specifically, what is the of the data it contains?

`c(1, 2, 3, "Hi")`

### It creates a vector of characters.

-   Would the following be valid?

`c(1, 2, 3, "Hi") + 1`

### No, it would not be valid. There are two different data types, one of which (character) that cannot be added.

-   How about

`c(1, 2, 3, FALSE) + 1`

### Yes, it is valid. Within the vector, the FALSE value has been converted to 0 (numeric). Thus, all values within the vector can be added to 1.

-   Hint: recall that know that the function `class()` returns the
    atomic data type stored in a vector

### Question 5:

-   We will be reproducing the following plot

![](https://www.dropbox.com/s/c4nf3n96np3i7nm/simple_qplot_example.png?dl=1)

### Create `x-axis` values

-   Create a variable called `x_axis` that is a `vector` of numerical
    values between 0 and 10 with a step of 0.5.
    -   i.e., `x_axis` will contain the values 0, 0.5, 1, 1.5, 2 …. 10
    -   Hint: you need a function that returns a sequence of values as a
        vector

<!-- -->

    x_axis <- seq(0, 10, by = 0.5)
    x_axis

    ##  [1]  0.0  0.5  1.0  1.5  2.0  2.5  3.0  3.5  4.0  4.5  5.0  5.5  6.0  6.5  7.0
    ## [16]  7.5  8.0  8.5  9.0  9.5 10.0

### Create `y-axis` values

-   Create a variable called `y_axis` that is a list of $x^2 + 2x + 3 $.
-   I.e., each position in `y_axis` is computed as $x^2 + 2x + 3 $, x is
    the value at the same position in `x_axis`
-   For example:
    -   The value at the first position of `y_axis` is 0^2 + 2\*0 + 3 =
        3
    -   The value at the second position of `y_axis` is 0.5^2 + 2\*0.5 +
        3 = 4.25
    -   etc…
-   Hint: remember that arithmetic operations on a vector are evaluated
    element-wise

<!-- -->

    y_func <- function(x) {
      x^2 + 2*x + 3
    }

    y_axis <- print(y_func(x_axis))

    ##  [1]   3.00   4.25   6.00   8.25  11.00  14.25  18.00  22.25  27.00  32.25
    ## [11]  38.00  44.25  51.00  58.25  66.00  74.25  83.00  92.25 102.00 112.25
    ## [21] 123.00

### Generate the plot of `x_axis` versus `y_axis`

-   Plot the values of `x_axis` and `y_axis`
-   Use the `qplot` function, which is part of `ggplot` library to plot
    the `x_axis` and `y_axis`.
    -   You can consult `qplot`’s documentation to see what arguments it
        takes as input
-   Change the behavior of your plot so that it has:
    -   A label for the `x-axis`. Mine says “My x\_axis”
    -   A label for the `y-axis`. Mine says “My x\_axis”
    -   A title. Mine says “My amazing plot of x\_axis versus y\_axis”  
    -   Dots that are bigger than those produced by default.
-   Hint: We know that we can change the default behavior of a function
    by changing the default parameters.
    -   Which default parameter (param) controls the `x-axis`, `y-axis`,
        and plot labels?
    -   Which default parameter controls the size of the symbol (dot
        here)?

<!-- -->

    library(ggplot2)

    qplot(x = x_axis, y = y_axis, 
          xlab = "Jake's x_axis", 
          ylab = "Jake's y_axis", 
          main ="Jake's amazing plot of x_axis versus y_axis") +
      geom_point(size = 5)

    ## Warning: `qplot()` was deprecated in ggplot2 3.4.0.
    ## This warning is displayed once every 8 hours.
    ## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was
    ## generated.

![](Jacob-Snyder_Practical-1_files/figure-markdown_strict/unnamed-chunk-5-1.png)

### The “x” parameter controls the x-axis; the “y” parameters controls the y-axis. The “xlab” and “ylab” parameters control the x-axis and y-axis labels, respectively. The “geom\_point” parameters controls the symbol size.
