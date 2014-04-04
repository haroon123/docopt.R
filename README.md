docopt
========================================================

`docopt` helps you to:

- define an interface for your command-line app, and
- automatically generate a parser for it.

For more information see [docopt.org](http://docopt.org)

R package `docopt` is an implementation of [docopt](http://docopt.org) in the R language.

Install
-------

`docopt` is currently in development and not available on CRAN.
To test it out use

```r
library(devtools)  # make sure to have devtools 1.4!
install_github("edwindj/docopt.R")
```


It is tested against the tests defined for the reference implementation.
It passes most tests. It currently fails tests that 

- count arguments: `prog -v -v` should return `list(v=2)`
- multiple prog statement: i.e. `prog -a \n prog -b`

The tests can be run using devtools `test()` and can be found in "inst/tests"

Usage
-----

docopt uses the description of the commandline interface to parse command line
arguments.


```r
'usage: prog [-a -r -m <msg>]

options:
 -a        Add
 -r        Remote
 -m <msg>  Message' -> doc

# load the docopt library
library(docopt)
```

```
## Warning: package 'docopt' was built under R version 3.0.3
```

```r

# retrieve the command line arguments
opts <- docopt(doc)
str(opts)
```

```
## List of 3
##  $ -a: logi FALSE
##  $ -r: logi FALSE
##  $ -m: chr "<msg>"
```

```r

# or set them manually
opts <- docopt(doc, "-m Hello")
str(opts)
```

```
## List of 3
##  $ -a: logi FALSE
##  $ -r: logi FALSE
##  $ -m: chr "Hello"
```

