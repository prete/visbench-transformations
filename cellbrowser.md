## UCSC CellBrowser

Input file type: `h5ad`
Transfromation steps:
- read h5ad file usign `scanpy.read`
- export to cellbrowser using `scanpy.external.exporting.cellbrowser`

```python
import scanpy

dataset_name="embryo2m_Xk"
adata = scanpy.read(f"{dataset_name}.h5ad")
scanpy.external.exporting.cellbrowser(
    adata, 
    "/output/", 
    dataset_name,
    annot_keys=['Main_Cluster'], 
    cluster_field='Main_Cluster', 
    html_dir="output/html/")
```