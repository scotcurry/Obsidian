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


**Networking**

Cloud Router - uses Border Gateway Protocol (BGP) to advertise IP address ranges to other networks and builds customer duynamic routes based on IP address information.

Cloud Armor - is a web application firewall (WAF) designed to mitigate DDoS attacks.  It is pre-configured to have rules that protect against the top 10 OWASP (Open Web Application Security Project) attacks.

Shared VPC - If multiple teams have their own Cloud Projects you may need to set up Shared VPC.  Shared VPCs have one host project and one or more service projects.  The projects must be in the same organization except when running a migration project.

VPC Network Peering - enables different VPC networks to communicate using private IP addresses to connect between different organizations.  Shared VPC does not allow this.  VPC peering is usually used in a SaaS platform when the SaaS provider wants to make the service available to different organizations.  Advantages are:
	* Low latency because the traffic stays on the Google network
	* Services in the VPC are inaccessible from the public internet
	* There are no egress charges
VPC peering works with Compute Engine, App Engine Flexible, and GKE.

**Cloud VPN**

GCP service that is implemented using IPSec VPNs.  HA VPN has two connections and provides 99.99% availability.  Cloud VPN supports 3Gbps speed.

**Cloud Interconnect**

Available in 10Gbps or 100Gbps when using a direct connection between Google Cloud and your data center, you can also use a third-party provider with options of 50Mps to 50Gps.  Data doesn't transverse the public internet.  Private IP addresses in the cloud are addressable from the on-prem instance and you can scale up to 200Gps.  If low latency and high availability are not required Cloud VPN will be less expensive.

**Direct Peering**

This is not a GCP service.  It works by exchanging Border Gateway Protocol routes.  It doesn't take advantage of VPC firewall rules or access control.

**Regional Load Balancing**

There are two types of regional load balancing: 1) Network TCP/UDP, uses forwarding rules to determine how to distribute traffic.  Uses the IP address, protocol and port to determine which server (target pool) will get the traffic.  All traffic is routed to the same instance which can cause imbalances if there are a lot of long lived connections.  2) Internal TCP/UDP, this is a good choice when distributing workloads across services that all run on GCP.

**Global Load Balancing**

HTTPS load balancing doesn't do SSL offloading, SSL Proxy does do SSL offloading, and TCP proxy allows for a single IP address and it will forward the traffic to the nearest instance.

**IAM**

There are Identities, Resources, Permissions, Roles, and Policies.  Identities consist of Google Accounts which are people that interact with GCP like devs and admins.  Service accounts are used by applications running in GCP.

Resources are things like projects, virtual machines, app engine applications, cloud storage buckets, and pub/sub topics.  Google defines the permissions according to the functionality of the resource.

Permissions are a grant to perform some action on a resource and roles are a set of permissions.  You cannot assign a permission to a person in GCP.  You grant it by assigning a role to the user.  There are three types of roles.  Predefined which are used for common functions, basic roles which were an older way of doing things with basically Viewer, Editor, and Owner roles.  You would only use basic roles for something like a DevOps team has a few users.