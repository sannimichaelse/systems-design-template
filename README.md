
# Systems Design Template

A template for architecting and designing scalable systems



- ### Feature expectations - [5 min]
        - Use cases
        - Scenarios that will not be covered
        - Who will use
        - How many will use
        - Usage patterns


- ### Estimations - [5 min]
        - Throughput (QPS for read and write queries)
        - Latency expected from the system (for read and write queries)
        - Read/Write ratio
        - Traffic estimates
                - Write (QPS, Volume of data)
                - Read  (QPS, Volume of data)
        - Storage estimates
        - Memory estimates
                - If we are using a cache, what is the kind of data we want to store in cache
                - How much RAM and how many machines do we need for us to achieve this ?
                - Amount of data you want to store in disk/ssd
        
- ### Design goals - [5 min]
        - Latency and Throughput requirements
        - Consistency vs Availability  [Weak/strong/eventual => consistency | Failover/replication => availability]

- ### High level design - [5-10 min]
        - APIs for Read/Write scenarios for crucial components
        - Database schema
        - Basic algorithm
        - High level design for Read/Write scenario

- ### Deep dive - [15-20 min]
        - Scaling the algorithm
        - Scaling individual components: 
                -> Availability, Consistency and Scale story for each component
                -> Consistency and availability patterns
        - Think about the following components, how they would fit in and how it would help
                a) DNS
                b) CDN [Push vs Pull]
                c) Load Balancers [Active-Passive, Active-Active, Layer 4, Layer 7]
                d) Reverse Proxy
                e) Application layer scaling [Microservices, Service Discovery]
                f) DB [RDBMS, NoSQL]
                        > RDBMS 
                            >> Master-slave, Master-master, Federation, Sharding, Denormalization, SQL Tuning
                        > NoSQL
                            >> Key-Value, Wide-Column, Graph, Document
                                Fast-lookups:
                                -------------
                                    >>> RAM  [Bounded size] => Redis, Memcached
                                    >>> AP [Unbounded size] => Cassandra, RIAK, Voldemort
                                    >>> CP [Unbounded size] => HBase, MongoDB, Couchbase, DynamoDB
                g) Caches
                        > Client caching, CDN caching, Webserver caching, Database caching, Application caching, Cache @Query level, Cache @Object level
                        > Eviction policies:
                                >> Cache aside
                                >> Write through
                                >> Write behind
                                >> Refresh ahead
                h) Asynchronism
                        > Message queues
                        > Task queues
                        > Back pressure
                i) Communication
                        > TCP
                        > UDP
                        > REST
                        > RPC

- ### Justify -  [5 min]
	       - Throughput of each layer
	       - Latency caused between each layer
	       - Overall latency justification
