# iSEEE

## Using `.rds` files
Input file type: `rds`
Transfromation steps:
- read SingleCellExperiment using readRDS 

```R
library(SingleCellExperiment)
library(iSEE)

filename <- 'embryo2m_Xk.rds'
sce <- readRDS(filename)
app <- iSEE(sce)
shiny::runApp(app, launch.browser = TRUE)
```

## Using `.loom` files
Input file type: `loom`
Transfromation steps:
- read loom file and cast it to SingleCellExperiment
- add reduced dimensions from colData for UMAP 

```R
library(SingleCellExperiment)
library(iSEE)
library(LoomExperiment)

filename <- 'embryo2m_Xk.loom'
scle <- LoomExperiment::import(filename, type="SingleCellLoomExperiment")
sce <- as(scle, 'SingleCellExperiment')
reducedDim(sce) <- colData(sce)[,c("X_umap1", "X_umap2")]
app <- iSEE(sce)
shiny::runApp(app, launch.browser = TRUE)
```