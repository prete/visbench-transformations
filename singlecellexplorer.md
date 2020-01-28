## Single Cell Explorer
Input file type: `h5ad`
Transfromation steps:
- read h5ad file usign `scanpy.read`
- using scpipeline.py provided by author
  - create ProcessPipiline object 
  - save annotations using mapInfo dictionary
  - insert to MongoDB

```python
import scanpy
import scpipeline

mapInfo = { 
    "mapType":"umap", "name":"", "study":"vizbench", "species":"human", "subjectid":"", 
    "disease":"", "source":"", "sample":"", "tissue":"", "comment":"", "author":""
}

dataset_name="embryo2m_Xk"
p =  scpipeline.ProcessPipline()
p.data = scanpy.read(f"{dataset_name}.h5ad")
mapInfo["name"] = dataset_name
p.saveAnnotation(mapinfo = mapInfo)
p.insertToDB(dbname= 'scDB',dbport= 27017,dbhost='localhost',rawDataIsNormalized=False,saveRawCounts=False)
```
