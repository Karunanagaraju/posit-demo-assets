# R Markdown Report with Penguins Data

A parameterized RMarkdown report!

![](report/imgs/report-screenshot.png)

## Usage

To render the report run:

```r
knit_with_parameters("report/report.Rmd")
```

## Deployment

### Git-backed

To deploy the report to RStudio Connect:

```r
rsconnect::writeManifest("report")
```

Then commit any changes to GitHub.

### Programatic

You can also deploy using the `rsconnect` api:

```r
rsconnect::deployDoc(
  doc = "report/report.Rmd",
  appTitle = "RMarkdown Penguins API Deployment"
)
```