# Run an R app container and deploy results to GitHub Pages

> This project is experimental!

Run an R app and deploy the results to git.

## Usage

It is easiest to use this action together with the [`build-r-app`](
  https://github.com/gaborcsardi/build-r-app) action. `build-r-app`
builds and publishes an app container, and `run-r-app` runs it on a
schedule.

Example workflow:

```yaml
name: run-app.yml
on:
  workflow_dispatch:
  schedule:
    - cron: '46 3 * * *'

permissions: read-all

jobs:
  cran-update:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
    - uses: gaborcsardi/run-r-app@main
```

## Inputs

* `app-dir`: directory of the R app. It will be used as the working
  directory.
* `branch`: branch to publish, default is `gh-pages`.
* `main`: the name of the R file to run with `Rscript`. It is a path
  relative to the app directory (the `app-dir` parameter). The default
  is `index.R`.

## R project setup

Make sure you also read the [`build-r-app` README](
  https://github.com/gaborcsardi/build-r-app#readme).

### Entry point

`run-r-app` will run `index.R` using `Rscript`.

## Example project

See https://github.com/r-hub/cran-metadata for a fully functional example
project.

## Related

* [`build-r-app` action](https://github.com/gaborcsardi/build-r-app) to
  dockerize an R app.

## License

MIT (c) Posit Software, PBC, 2024
