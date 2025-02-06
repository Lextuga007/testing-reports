
# Testing out Quarto and Observable

<!-- badges: start -->
<!-- badges: end -->

Trying out transforming and plotting data using Observable because this occurs
in the html and doesn't require a ui/server relationship like Shiny that requires
a server (unless it is public).

Ultimately looking to speed up the transformation of SPC charts but these are
transformed before plotting because they are built up from statistics. 
For example, you can't have a whole dataset with all the statistics calculated
which can then be "cut" according to the category wanted.

ObservableHQ did some training in 2023 which is useful to follow:

[YouTube](https://www.youtube.com/watch?v=tHorkp-WCQY&t=2123s)
[materials](https://observablehq.com/@observablehq/plot-session-1-follow-along)

Replicating the notebook will require an account and it's possible to log in with
GitHub.
Highly recommend trying this out as the interactive nature of these notebooks 
means that charts can be started in through drop down wizards, code produced which
can be amended further in the notebook and then copied to Quarto.

The course doesn't include anything about importing data but it was quite easy 
and until I can work out how to transform data in Observable I used R to produce 
subset data using code to export to a csv that I imported:

```
library(NHSRdatasets)
library(dplyr)

sub_set <- ae_attendances |>
  filter(org_code == "RQM", type == 1, period < as.Date("2018-04-01")) |> 
  arrange(period)

readr::write_csv(sub_set, "subset_aeatt.csv")
```

Note there is a requirement to order this data by period! 

Also **do not** connect these notebooks to SQL with sensitive data because this
is all through the web so would be a security breach.
I recommend using data from things like `NHSRdatasets` or some made up dummy data
to test out charts.