Along with the Composable DBMS Trend, which mentioned in [OLAP Components](olap_components.md), the Cloud Native Data Warehouse design is another buzzword
that achieved through Shared Disk Architecture.

### Shared Disk Architecture Trend

There are two common architecture of distributed database:
Shared nothing and Shared disk.
Some advantages of Shared Disk Architecture:
- Scale compute layer independently from the storage layer.
- Easy to shutdown idle compute layer resources.
- May need to pull uncached persistent data from storage
layer to compute layer before applying filters.

Traditionally the storage layer in shared-disk
DBMSs were dedicated on-prem NAS.
- Example: Oracle Exadata

Cloud object stores are now the prevailing storage
target for modern OLAP DBMSs because they are
"infinitely" scalable.
- Examples: Amazon S3, Azure Blob, Google Cloud Storage, MinIO, Cepth, JuiceFS

Cloud data warehouses are mostly Shared disk architecture. 
Newly MPP and OLAP databases are also follow the compute-storage segeration by
partitioning tables into large, immutable files stored in an object store.

Fundamentally these new DBMSs are not different than
previous distributed/parallel DBMSs except for the
prevalence of a cloud-based object store for shared disk.
- Firebolt, Bigquery, Redshift, ....

Breaking down some newly added CDW: 
[WIP]
