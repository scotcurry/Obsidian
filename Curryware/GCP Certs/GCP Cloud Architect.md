EHR Healthcare

* Multi-national
* Regulated
* Mix of relational and NoSQL databases
* File and API Integrations - No plan to upgrade at the current time
* IAM is MS AD
* Monitoring Open Source Tools

**Mountkirk Games**

* Geo-specific digital arenas
* Real-time leader board
* Using GKE, global load balancer, Spanner Cluster
* 5 games were lift and shift
* Each game exists in its own project nested below a folder that maintains most of the permissions and network policies.
* Latency is the most important consideration, with cost management as the next most important.



**Interesting Points**

Premium tier networking uses Googles network as opposed to the Internet.


**Data Storage**

Memorystore is cached data and should only be used if the data is going to be used by the application in the very near future.  Reduces latency but can disappear at any time so it needs to be backed by a permanent data store.

Time series databases may aggregate data over time.Basically this is roll-ups of metrics.

Object Storage is for unstructured data and backups.  Nearline is for data that is stored once a month, Cold is used for items accessed once a quarter, and archive is for data this is used once a year.

Cloud SQL is used for transaction processing systems such as e-commerce sales and inventory systems.

Cloud Spanner supports services that support horizontal scalability across regions.  It only supports Google Standard SQL and Postgres dialects.  Anything that needs global access to the data is a candidate for this technology.  It supports data encrypted at rest and defaults to Google managed keys.

Big Query supports queries that scan and return large volumes of data and performs aggregation on that data.  To the user it is serverless.  Billed based on data stored and the execution time, so it is a good idea to use --dry-run.
	*To get data into BigQuery you Storage Write API or Cloud Dataflow.

Cloud BigTable was designed for petabyte-scale databases for analytics such as stroing data for machine learning or getting IoT streams.  It has very low latency and supports huge datasets.  You can migrate from Hadoop to BigTable.

Cloud MemoryStore comes in a flavor for Redis and on for Memcached.  Redis has defined data types that can be stored while Memcached has only strings.

**Data Rules**

If submillisecond access time is needed, use cache (Cloud Memorystore), if data is frequently accessed and may be updated, and need persistent storage use a cloud database, if data is less likely to be accessed the older it gets use Big Query or Big Table.  If data is infrequently accessed and doesn't need a query language use Cloud Storage.  You can set retention policies on Cloud Storage.

Watch for latency question.  Cloud Spanner and Cloud Firestore are designed to scale globally.  You can also reduce latency by using Cloud CDN.