# Bug in `rvest` version `0.3.2` function `html_table` with parameter `fill = TRUE`

The `fill = TRUE` parameter of the `html_table` function from the `rvest` library can be used to read HTML tables with an uneven number of cells in each row - for instance, when multicolumn or multirow cells are used, or simply when the table is malformed.

The documentation for `html_table` (`rvest` version `0.3.2`) states the following:

    fill    If TRUE, automatically fill rows with fewer
            than the maximum number of columns with NAs.

This was true for `rvest` version `0.3.1`. In version `0.3.2`, `html_table` apparently attempts to handle the multirow cells by repeating their data, but unfortunately some data is misplaced.

This repository provides two notebooks illustrating the following

* [the documented behaviour of `0.3.1`](rvest-0.3.1.nb.html), which requires some further work to properly organize the data, and
* [the new behaviour of `0.3.2`](rvest-0.3.2.nb.html), which leads to data that cannot be easily transformed into a well-behaved form.
