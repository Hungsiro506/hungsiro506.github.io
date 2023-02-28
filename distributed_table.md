### A note about distributed table in OLTPs.

**Sharding** and **partitioning** are both about breaking up a large data set into smaller subsets. The difference is that sharding implies the data is spread across multiple computers while partitioning does not. Partitioning is about grouping subsets of data within a single database instance. Sharding → horizontal, Partitioning → vertical. 
In many cases, the terms sharding and partitioning are even used synonymously, especially when preceded by the terms “horizontal” and “vertical.” Thus, “horizontal sharding” and “horizontal partitioning” can mean the same thing. 
- Citus uses *sharding* term to archive distributed table, while Oceanbase uses *partitioning*

Convention:  we will use both *sharding* and *paritioning* in this blog, depending on the origin of context. 

There are several mainstream forms of distributed table on exiting db in the market. 

1. **Implicit distributed table ( auto )**: TiDb, CockroachDb, Yugabyte. 
- All tables of this type database are distributed tables, no sharding/partition key needs to be specified.
- Using Distributed Transactions to maintain global indexes
1. **Explicit distributed table ( manual )**: Citus, OceanBase.
- A table without partition key is a normal table in traditional db and does not have scalability. Creating a distributed table requires a syntax similar to a partition table.
- This type of database generally also provides the ability of global indexing (we generally call it middleware rather than database if it is not provided). But unlike the first category, they generally take the global index as an option, which is manually specified and created by the user. In addition, they also provide local indexes implemented based on stand-alone transactions (local indexes).

**There is a large performance difference between distributed transactions + global indexes and stand-alone transactions + indexes**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ab4a23ed-beac-492e-a98e-aaaa052d9cbc/Untitled.png)

1. Transparent (automatic) ease of use determines the lower limit of the use of distributed databases, but there is a higher cost in terms of performance

2. Manual can provide the best performance, but the threshold of use will increase

Ref: [1]: [https://www.zhihu.com/question/400141995](https://www.zhihu.com/question/400141995)
