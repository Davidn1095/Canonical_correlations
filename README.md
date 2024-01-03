# Canonical_correlations

## Loading Required Libraries and Data

- `library(readxl)`: This command loads the `readxl` package which is essential for reading Excel files in R.
- `datos <- read_excel("Aplicacion.xlsx")`: This line reads data from the "Aplicacion.xlsx" file and stores it in a DataFrame called `datos`.

## Data Preparation

- `matriz.datos <- datos[c("X1", "X2", "X3", "X4", "Y1", "Y2")]`: This creates a new DataFrame `matriz.datos` by selecting specific columns from `datos`.
- `datos.Partidos <- datos[c("X1", "X2", "X3", "X4")]`: Extracts a subset of `datos` into `datos.Partidos`.
- `datos.Nombres <- datos[c("Y1", "Y2")]`: Similarly extracts another subset to create `datos.Nombres`.

## Canonical Correlation Analysis

- `library(CCA)`: Loads the `CCA` package for performing Canonical Correlation Analysis.
- `matriz.correlacion <- matcor(datos.Partidos, datos.Nombres)`: Computes the correlation matrix between `datos.Partidos` and `datos.Nombres`.
- `img.matcor(matriz.correlacion, type = 2)`: Visualizes the correlation matrix, likely as a heatmap or similar graphical representation.

## Performing CCA and Extracting Results

- `cca.datos <- cc(datos.Partidos, datos.Nombres)`: Performs Canonical Correlation Analysis.
- The code then extracts and displays various components of the CCA result, such as canonical correlations (`cca.datos$cor`), coefficients for X (`cca.datos$xcoef`), and Y (`cca.datos$ycoef`), and canonical scores.

## Plotting CCA Results

- `plt.cc(cca.datos, var.label = TRUE)`: Generates a plot of the CCA results, labeling the variables.
- `plot(cca.datos$cor, type = "b")`: Creates a line plot for the canonical correlations.

## Statistical Significance Testing

- `library(CCP)`: Loads the `CCP` package for performing significance testing in CCA.
- `rho <- cca.datos$cor`, `n <- dim(datos.Partidos)[1]`, `p <- length(datos.Partidos)`, `q <- length(datos.Nombres)`: These lines define variables used in the significance testing.
- `p.asym(rho, n, p, q)`: Performs a significance test for the canonical correlations. Variations of this test are conducted with different test statistics such as "Hotelling" and "Pillai", offering alternate methods for assessing the significance of the canonical correlations.
