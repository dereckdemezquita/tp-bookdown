# tp-bookdown

This is a simple and basic template for quickly creating working repos that are set to run and start writing a book or large document with R. Feel free to reference the original bookdown documentation for more information on the syntax required to write a bookdown document: [bookdown.org](https://bookdown.org/yihui/bookdown/)

This repo is originally based on the minimal bookdown example: [yihui/bookdown-minimal](https://github.com/yihui/bookdown-minimal) and only the most essential features are taken.

The following are set to run.

- `_bookdown.yml` K-M rendering model; all .Rmds have separate R sessions.
  - Note that due to a bug in bookdown the K-M rendering is not working; for more information see the issue here: [bookdown/issues/36](https://github.com/rstudio/bookdown/issues/36)
- `_output.yml` a `styles.css` script is set.


## Build the book

In order to build the book continously run the script found in the `index.Rmd`:

```{r}
for (i in 1:100) {
  tryCatch({
    servr::daemon_stop(i)
  }, error = function(e) {
    message("Error: ", e)
  })
}
bookdown::serve_book(dir = ".", output_dir = "_book", preview = TRUE, in_session = TRUE, quiet = TRUE)
```
