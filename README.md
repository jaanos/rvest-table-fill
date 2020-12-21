# Bug in `rvest` version `0.3.2` (and later) function `html_table` with multirow cells

The `html_table` function from the `rvest` library can be used to read HTML tables with an uneven number of cells in each row. In the case of cells spanning multiple rows or columns, their contents are supposed to be replicated in each of the spanned cells of the resulting data frame.

Support for multirow cells has been added in version `0.3.2`, however, `html_table` unfortunately misplaces some data. The problem persists in version `0.3.4` and has finally been fixed in the version that will become `0.3.7`.

This repository provides three notebooks illustrating the following

* [the behaviour of `0.3.1`](https://jaanos.github.io/rvest-table-fill/rvest-0.3.1.nb.html), which requires some further work to properly organize the data,
* [the behaviour of `0.3.2`](https://jaanos.github.io/rvest-table-fill/rvest-0.3.2.nb.html), which leads to data that cannot be easily transformed into a well-behaved form,
* [the desired behaviour](https://jaanos.github.io/rvest-table-fill/rvest-pr196.nb.html), which is achieved through the patch in pull request [tidyverse/rvest#196](https://github.com/tidyverse/rvest/pull/196), and
* [the final behaviour](https://jaanos.github.io/rvest-table-fill/rvest-pr293.nb.html), which is achieved through total rewriting in pull request [tidyverse/rvest#293](https://github.com/tidyverse/rvest/pull/293).
