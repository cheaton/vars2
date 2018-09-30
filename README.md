# vars2
The vars R package available at https://cran.r-project.org/web/packages/vars/index.html has a minor bug in the causality() function. For a VAR(p) of a vector of dimension r, if T is the number of observations (after taking p lags), then causality()  computes df2 = r(T - rp - 1). The correct denominator degrees of freedom is df2 = T - rp - 1 (see, for example, Hamilton, J.D. (1994) Time Series Analysis, PUP, p.305). Consequently, the test as performed by causality() is oversized. In many applications, the difference in the size is minor, but it becomes noticeable in cases where the number of parameters is a somewhat large proportion of the sample size.

I emailed the author of the vars package on the 7th of June 2018 to report the issue, but as of 30th September 2018, I have not received a reply, and the vars package still has the bug.

The software in this repo is the vars package with the bug fixed and the documentation modified appropriately. This is not intended to be a fork. I don't intend to do any more work on it, and I will delete it when the bug if fixed in vars. In the meantime however, it is easier to install from here than to install the vars package from CRAN and manually fix the bug each time.

If you have already installed the vars package, you should uninstall it before installing from this repo. This could be done by typing the following command in R:
```
remove.packages("vars")
```
Alternatively, you could find the vars directory in your local R library and delete it manually.

To install this package, in R type the following commands:
```
install.packages("devtools")  # You only need this line if you haven't already installed devtools.
library(devtools)
install_github("cheaton/vars2")
```
Note that, once the package is installed, it is named vars, rather than vars2. Therefore, it may be loaded using the command
```
library(vars)
```
At this point, if you type the command
```
help(causality)
```
and read the description, it should confirm that you are using the modified version of the package instead of the original vars package from CRAN.
