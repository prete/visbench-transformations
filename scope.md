## SCope

SCope works with loom files to follow the [convention for row names](http://linnarssonlab.org/loompy/conventions/index.html).
We need to change 'gene_short_name' to 'Gene'.

Input file type: `h5ad`
Transfromation steps:
- read h5ad file usign `scanpy.read`
- convert h5ad to loom

```python
import scanpy

dataset_name="embryo2m_Xk"
adata = scanpy.read(f"{dataset_name}.h5ad")
adata.var['Gene'] = adata.var['gene_short_name']
adata.write_loom(f"/output/{dataset_name}.loom", True)
```
