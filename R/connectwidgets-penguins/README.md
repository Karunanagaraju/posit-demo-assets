# Using connectwidgets with Posit Connect

A demo of connect widgets in RStudio Connect.

- Code: <https://github.com/SamEdwardes/demo-connect-widgets-penguins>
- Deployment: <https://colorado.rstudio.com/rsc/demo-connect-widgets-penguins/>

![](app/imgs/screenshot.png)

## Environment variable requirements

This content needs to have the following environment variables set to function:
- `CONNECT_SERVER` the URL of your Connect server, for Test Drive it will be in this format: https://YOUR_DOMAIN_HERE.eval.posit.co/cnct
- `CONNECT_API_KEY` an API key from your Connect server. See [API Keys](https://docs.posit.co/connect/user/api-keys/) in the Connect User guide for more information.
 
Variables can be saved in an .Renviron config file when working with this project. [`usethis`](https://usethis.r-lib.org/) has a function for creating and editing .Renviron files: 

```r
library(usethis)
usethis::edit_r_environ()
```

Add the variables to that file in the format `KEY=VALUE` and save it. Restart the session so the new environment variables will be loaded with `ctrl shift f10` or through the RStudio IDE through the **Session** dropdown and selecting **Restart R**.

## Usage

To render the report locally:

```r
rmarkdown::render("app/report.Rmd")
```

## Deployment

### Git-backed

To deploy to RStudio connect refresh the manifest.json file:

```r
rsconnect::writeManifest(
  "app", 
  appFiles = c("report.Rmd", "imgs")
)
```

Then, push any changes to git. RStudio connect will automatically deploy any changes.

### Programmatic

You can also deploy using the rsconnect api:

```
rsconnect::deployDoc(
  doc = "app/report.Rmd",
  appTitle = "Connect Widget Example"
)
```