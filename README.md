# docs-leaflet-rstudio-macos
Documentation for how to get Leaflet working in RStudio on macOS (tested on Apple Silicon)

## Instructions

Step 1.

- If you do not have this already, set up Homebrew, a _package manager_ which will help install the additional components we need to get Leaflet up and running in RStudio on macOS.
- Visit https://brew.sh/ for instructions.

Step 2.

- Once Homebrew is set up properly, run this command to install [GDAL (Geospatial Data Abstraction Library)](https://en.wikipedia.org/wiki/GDAL) and [PROJ (cartographic projects library)](https://en.wikipedia.org/wiki/PROJ):

    ```zsh
    brew install gdal proj
    ```

Step 3.

- If GDAL and PROJ were successfully installed using Homebrew, then go to the RStudio console, and run this command to install [terra](https://cran.r-project.org/web/packages/terra/index.html), which is required for Leaflet to work:

    ```r
    install.packages("terra", type = "source", configure.args = c("--with-sqlite3-lib=/opt/homebrew/opt/sqlite/lib", "--with-proj-lib=/opt/homebrew/opt/proj/lib"))
    ```

- The additional configurations are required to link up to the components installed by Homebrew.

Step 4.

- If step 3 above ran successfully, now run the following to finally install Leaflet:

    ```r
    install.packages("leaflet", type = "source", configure.args = c("--with-sqlite3-lib=/opt/homebrew/opt/sqlite/lib", "--with-proj-lib=/opt/homebrew/opt/proj/lib"))
    ```

## Acknowledgements

- Thanks to `gcamp` on [Stack Overflow #30034372](https://stackoverflow.com/a/30034372) for the hint about installing `libproj` on macOS
- Thanks to `pat-s` on [GitHub - repo _sf_ - issue #1894](https://github.com/r-spatial/sf/issues/1894#issuecomment-1025559431) for the hint about how to configure `install.packages(...)` to work with Homebrew-installed components
