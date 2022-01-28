# Issues-of-custom-table-in-pdf-beamer-in-rmarkdown
Problem in making a table in beamer presentation in rmarkdown
I can create a custom table in pdf document. But the same command did not work in pdf beamer presentation. When I tried something like

## Custom Table

```{r, echo = FALSE, comment = FALSE, warning = FALSE, cache = FALSE, message = FALSE}

tab_01 = data.frame(
  State = c("In work", "Not in work"),
  cs = c("863", "1979"),
  wk = c("7461", "607"),
  nw = c("2622", "29616"),
  dd = c("215", "3587")
)

tab_01 %>%
kable(
  format = "latex",
  booktabs = TRUE,
  escape = FALSE,
  col.names = c("State at current time", "Censored state*", "In work", "Not in work", "Dead"),
  align = c("l", "c", "c", "c", "c"),
  caption = "Distribution of observed pairs of consecutive states among individuals in ELSA, 2002/2003 –   2018.") %>%
  row_spec(row = 0, align = "c") %>%
  kable_styling(full_width = TRUE, position = "center") %>%
  column_spec(1, width = "6em") %>%
  column_spec(2, width = "6em") %>%
  column_spec(3, width = "6.5em") %>%
  column_spec(4, width = "6.5em") %>%
  column_spec(5, width = "6.5em") %>%
  add_header_above(c(" " = 1, "State at next time (2 years interval)" = 4)) %>%
  footnote(symbol = c("Alive but in an unknown state at last observation time."),
  symbol_title = "Note:",
  footnote_as_chunk = T, title_format = "italic")

```

It gives me the message like LaTeX Error: Environment tabu undefined. Can anyone help me how to rectify.
