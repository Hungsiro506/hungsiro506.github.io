# Building Blocks Of An OLAP

### OLAP Commoditization trend

One recent trend of the last decade is the breakout
OLAP engine sub-systems into standalone opensource components

**Eg**: 
- Client Interface ( API server )
- Catalogs
- Query Optimizers
- Execution Engine
- File Format and Access Libraries
- Storage Engine

Those components are essential parts to build up an OLAP database

#### 1. Catalogs

Notable implementation:
- **HCatalog**
- Google Data Catalog
- Amazon Glue

Implementation from Distributed OLAP and Storage Engine:
- FireBolt: using Foundation DB
- Bydance Clickhouse: using Foundation DB
- Juicefs: On top of Redis to maintain S3 files directory structure

#### 2. Query Optimizers

Extendible search engine framework for heuristicand cost-based query optimization.
- DBMS provides transformation rules and cost estimates.
- Framework returns either a logical or physical query plan

Notable implementations:
- Greenplum Orca
- Apache Calcite

Implementation from other databases:
- Firebolt: Forks from Hyrise
- Bydance Clickhouse: in-house build - CBO for clickhouse
- Doris and Starsrock

#### 3. Fire Formats:
Most DBMSs use a proprietary on-disk binary file
format for their databases.The only way to share
data between systems is to convert data into a
common text-based format
- Examples: CSV, JSON, XML
There are open-source binary file formats that make
it easier to access data across systems and libraries
for extracting data from files.
- Libraries provide an iterator interface to retrieve (batched)
columns from files.

**HDF5** (1998)
- Multi-dimensional arrays for
scientific workloads.
  
**Apache Parquet** (2013)
- Compressed columnar storage from
Cloudera/Twitter

**Apache ORC** (2013)
- Compressed columnar storage from
Apache Hive.

**Apache Iceberg** (2017)
- Flexible data format that supports
schema evolution from Netflix.

**Apache Arrow** (2016)
- In-memory compressed columnar
storage from Pandas/Dremio.

#### 4.Execution Engines
Standalone libraries for executing vectorized query
operators on columnar data.
- Input is a DAG of physical operators.
- Require external scheduling and orchestration

Notable implementations:
- **Velox**
- **DataFusion**
- Intel OAP

Implementation from other databases:
- Clickhouse
- Doris

Andy's Note:
_`The long-term trend to watch is the proliferation of frameworks like Velox, DataFusion, and Polars. Along with projects like Substrait, the commoditization of these query execution components means that all OLAP DBMSs will be roughly equivalent in the next five years. Instead of building a new DBMS entirely from scratch or hard forking an existing system (e.g., how Firebolt forked Clickhouse), people are better off using an extensible framework like Velox. This means that every DBMS will have the same vectorized execution capabilities that were unique to Snowflake ten years ago. And since in the cloud, the storage layer is the same for everyone (e.g., Amazon controls EBS/S3), the critical differentiator between DBMS offerings will be things that are difficult to quantify, like UI/UX stuff and query optimization.`_

### Share Disk Architecture Trend

Traditionally the storage layer in shared-disk
DBMSs were dedicated on-prem NAS.
- Example: Oracle Exadata
Cloud object stores are now the prevailing storage
target for modern OLAP DBMSs because they are
"infinitely" scalable.
- Examples: Amazon S3, Azure Blob, Google Cloud Storage, MinIO, Cepth, JuiceFS

Cloud data warehouses and MPP db are mostly Share disk architecture. 
Newly MPP and OLAP databases are also follow the compute-storage segeration
- Firebolt, Bigquery, Redshift, ....
