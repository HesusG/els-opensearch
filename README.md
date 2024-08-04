# Introduction to Amazon OpenSearch

### Overview
Amazon OpenSearch is a community-driven, open-source search and analytics suite derived from Apache 2.0 licensed Elasticsearch 7.10.2 and Kibana 7.10.2. It consists of:
- **OpenSearch**: A powerful search engine.
- **OpenSearch Dashboards**: A visualization and user interface.
- **Tools and Plugins**: Adding a series of functionalities.

### Elasticsearch

- **History**: Elasticsearch and Kibana have been pivotal in the open-source search and analytics space.
- **OSS Introduction (2019)**: Open Source Software (OSS) introduced significant enhancements.
- **License Change (2021)**: Transitioned from Apache 2.0 to a licensed software model.
- **AWS OSS Version**: AWS forked Elasticsearch 7.10 to create OpenSearch, maintaining an open-source version.

### Amazon OpenSearch Managed

- **Managed**: Fully managed service by AWS.
- **Secure**: Built-in security features.
- **Observability**: Comprehensive monitoring and observability tools.
- **Cost-Conscious**: Optimized for cost efficiency.

### Industry Examples for Real-Time Search at Scale

#### Use Cases for Real-Time Search at Scale
- **E-commerce Platform**: Enhance product search capabilities.
- **Document Portal**: Efficiently search through large volumes of documents.
- **Recommendation Engine**: Provide personalized recommendations.
- **Platform Search Services**: Improve search functionality across various platforms.

#### Examples for Log Analytics
- **Infrastructure Monitoring**: Locate, diagnose, and remediate issues with your infrastructure and AWS services.
- **Application Monitoring**: Monitor application performance and health.
- **Security Monitoring**: Enhance security through detailed log analysis.
- **Business Insights**: Gain insights into business operations.
- **Observability**: Comprehensive observability for your applications and infrastructure.

You can also set up alarms to monitor various metrics and events.

### How the Search Engine Works

- **Apache Lucene**: The underlying technology powering OpenSearch.
- **Inverted Index**: A data structure used to enable fast full-text searches.

### Interaction

- **JSON via REST API**: Interact with OpenSearch using JSON over REST API.
- **Data Indexing**: Data is indexed for efficient search and retrieval.
- **Search Using DSL**: Utilize the Domain Specific Language (DSL) for advanced search queries.

### Amazon OpenSearch Terminology

- **Value**: From large blocks of text to numeric, date, geo, etc., values are what the search engine uses for matching.
- **Field**: A single piece of data within a document.
- **Document**: A JSON object that contains one or more fields.
- **Shard**: A collection of documents, it is an instance of Apache Lucene. Shards can be primary or replica.
  - **Primary Shard**: Ingests data into primary shards.
  - **Replica Shard**: Used for backup; a replica of the primary shard.
- **Index**: Composed of one or more shards, the index is the logical unit of storage.
- **Node**: Provides storage and compute for OpenSearch. Node types include data, master, ingestion, and others.
- **Cluster**: A distributed system of nodes.

- **Structured Data**: Data in formats like CSV, JSON.
- **Unstructured Data**: Blobs of text.

#### Deployment Architecture

- **Nodes**: Types of nodes in OpenSearch:
  - **Data Nodes**
  - **Ultra Warm Nodes**
  - **Leader Nodes**

- **Security**: 
  - **Cognito, SAML**: Used for dashboard login and identity management.

#### Interaction with AWS Services

- **CloudTrail**: Monitors and logs account activity.
- **Kinesis Data Firehose**: Loads streaming data into OpenSearch.

#### Distributed Search Execution

- **Query Phase**: When a search request is sent, the node becomes the coordinating node. Each shard executes the search request locally and builds a priority queue of matching documents.
  - **Priority Queue**: The coordinating node merges these shard-level results into its own sorted priority queue, representing the globally sorted results (e.g., top 10).

### Lab 1: Creation of OpenSearch Domain

1. **Sign in to AWS**: Log in to your AWS account.
2. **Create Instance**: Follow the guidelines to create an OpenSearch instance.

#### Zone Awareness

- **Zones for Higher Availability**: Ensures higher availability.
- **Cross-Cluster Search**: Enables searching across multiple OpenSearch domains from a single dashboard interface.

#### Data Lifecycle in Amazon OpenSearch Service

- **Send Data**: Ingest data into Amazon OpenSearch.
- **Index State Management (ISM)**: Automate index migrations or deletions.
  - **Hot**: Frequently accessed data.
  - **Warm**: Data accessed over time.
  - **Cold**: Rarely accessed data.

Note: Data can only be indexed in hot nodes.

#### Observability with OpenSearch

Observability in OpenSearch involves monitoring and analyzing the performance and behavior of your applications and infrastructure. It encompasses several key concepts and tools:

- **Log Correlation**: The process of linking logs from different sources to provide a comprehensive view of an event or transaction. This helps in diagnosing issues by correlating logs from various services and components.

- **Trace Analytics**: The analysis of distributed traces to understand the flow of requests through a system. This helps in identifying performance bottlenecks, latency issues, and errors in microservices architectures.

- **OpenTelemetry**: An open-source observability framework that provides APIs, libraries, agents, and instrumentation to collect metrics, logs, and traces. It is a unified standard for service observability.

- **Jaeger, Zipkin, Z-Ray**:
  - **Jaeger**: An open-source, end-to-end distributed tracing tool used for monitoring and troubleshooting microservices-based applications.
  - **Zipkin**: Another open-source distributed tracing system that helps gather timing data needed to troubleshoot latency problems in service architectures.
  - **Z-Ray**: A tool for PHP applications that provides deep insights into application performance and behavior.

- **Trace Span Details**: Individual units of work within a trace. Each span represents a single operation within a request and includes details such as the start time, duration, and metadata.

- **Service Maps**: Visual representations of the relationships and dependencies between different services in your architecture. They help in understanding how services interact and identifying potential points of failure.

- **Trace Groups**: Collections of traces that share common characteristics, such as the same entry point or service. They help in organizing and analyzing traces based on specific criteria.

By leveraging these concepts and tools, you can achieve comprehensive observability in your OpenSearch environment, enabling you to monitor, troubleshoot, and optimize your applications and infrastructure effectively.
### Machine Learning in Amazon OpenSearch Service

- **Mitigating Issues Faster with Anomaly Detection in Streaming Data**: Anomaly detection helps identify unusual patterns in streaming data in real-time, allowing you to mitigate issues faster by automatically detecting and alerting on anomalies.

- **Improving Search**: Machine learning can enhance search capabilities by providing more relevant results, understanding user intent, and personalizing search experiences.

#### Multi-Layer Security

- **Importance of Security**: Security is crucial to protect sensitive data, ensure compliance with regulations, and maintain user trust.

- **Integrating SAML and Cognito for OpenSearch Dashboards Login**: 
  - **SAML (Security Assertion Markup Language)**: Enables single sign-on (SSO) by allowing users to authenticate through an identity provider.
  - **Amazon Cognito**: Provides user authentication, authorization, and user management for web and mobile apps.

- **IAM to Control Access to Endpoints**: Use AWS Identity and Access Management (IAM) to define who can access your OpenSearch endpoints and what actions they can perform.

- **Using Private Endpoints**: Deploy OpenSearch into your VPC (Virtual Private Cloud) and use security groups to control traffic. This ensures that your data remains within a secure network.

- **Fine-Grained Access Control**: Use OpenSearch's fine-grained access control to secure your data and dashboards by defining detailed permissions for different users and roles.

- **Encrypting Data in Transit and at Rest**: 
  - **Data in Transit**: Use TLS (Transport Layer Security) to encrypt data as it moves between clients and servers.
  - **Data at Rest**: Encrypt data stored in OpenSearch to protect it from unauthorized access.

- **What is TLS?**: Transport Layer Security (TLS) is a cryptographic protocol designed to provide secure communication over a computer network. It ensures data privacy and integrity between communicating applications.


# How is OpenSearch Different from Other Database Engines, Especially Those Focused on Analytics?

## Relational vs. NoSQL Databases

To understand how OpenSearch stands out, it's crucial to grasp the difference between relational and NoSQL databases:

### Relational Databases

**Structure:**
- Relational databases use tables to store data, with predefined schemas. Each table consists of rows and columns, and relationships between tables are established using foreign keys.
- Data integrity and normalization are key principles, ensuring that data redundancy is minimized, and relationships between data entities are clearly defined.

**Joins:**
- These databases support complex queries and joins, allowing data to be combined from multiple tables. This capability is fundamental for relational databases, enabling users to execute intricate queries that link data from various sources seamlessly.
- Joins can be of different types such as inner joins, left joins, right joins, and full outer joins, each serving a specific purpose in combining datasets.

**Examples:**
- Popular relational databases include MySQL, PostgreSQL, and Oracle Database. These systems are widely used in applications where data relationships are crucial, and transactional consistency is required.

### NoSQL Databases

**Structure:**
- NoSQL databases offer more flexible data models such as key-value pairs, documents, wide-columns, or graphs. They are designed to handle large volumes of unstructured or semi-structured data.
- Unlike relational databases, NoSQL databases do not require a fixed schema, allowing for greater flexibility and adaptability to changing data needs.

**Joins:**
- Traditional joins as seen in relational databases are often absent in NoSQL databases. However, some NoSQL databases offer mechanisms to link or embed documents within each other to simulate joins.
- The lack of native join support is often mitigated by denormalizing data or using application-side logic to combine data from multiple sources.

**Examples:**
- MongoDB, Cassandra, and Redis are well-known NoSQL databases. These systems are optimized for specific use cases, such as document storage, wide-column storage, or in-memory data caching.

## OpenSearch: A Specialized NoSQL Engine for Analytics

### Key Features of OpenSearch

**Search and Analytics:**
- OpenSearch is designed for fast search, logging, and analytics use cases. It excels at full-text search, structured search, and analytics over large datasets.
- The engine provides advanced search capabilities, including relevance ranking, filtering, and aggregations, making it ideal for applications that require powerful search functionality.

**Schema Flexibility:**
- Unlike relational databases, OpenSearch allows for dynamic schema changes, making it easy to adapt to evolving data structures. This flexibility is crucial for applications that need to handle diverse and rapidly changing datasets.
- Users can add new fields on the fly without the need for predefined schemas, facilitating rapid development and iteration.

**Scalability:**
- OpenSearch can handle horizontal scaling efficiently, distributing data across multiple nodes for better performance and reliability. This scalability is essential for handling large volumes of data and ensuring high availability.
- The system can scale out by adding more nodes to the cluster, providing linear scalability for both storage and processing capabilities.

**Near Real-Time Processing:**
- OpenSearch is optimized for near real-time data ingestion and querying, which is ideal for time-series data and monitoring use cases.
- The ability to ingest and index data in near real-time allows for immediate analysis and visualization, making it suitable for applications that require up-to-date information.

### Handling Relationships in OpenSearch

**Joins:**
- While traditional SQL-style joins are not natively supported, OpenSearch provides ways to relate data. Parent-child relationships, nested documents, and application-side joins can be used to link data together.
- These methods enable users to structure their data in ways that facilitate complex queries and relationships, even without traditional join support.

**Nested Objects:**
- You can store related data within a single document using nested objects, allowing for efficient querying of related data without the need for joins.
- Nested objects are useful for representing hierarchical relationships within a single document, simplifying the data model and query logic.

**Denormalization:**
- Often, data is denormalized in OpenSearch, meaning related information is stored together within a single document to optimize query performance.
- Denormalization reduces the need for joins and can significantly improve query performance, especially for read-heavy workloads.

### Comparison with Other Analytics-Focused Engines

**Relational Analytics Engines:**
- Engines like Amazon Redshift or Google BigQuery are designed for analytical processing over relational data, supporting complex joins and aggregations. These systems are optimized for large-scale analytical queries and provide robust support for SQL.
- However, they might not be as efficient in handling unstructured data or providing real-time search capabilities, which are strengths of OpenSearch.

**Other NoSQL Analytics Engines:**
- Platforms like Apache Cassandra or Google Cloud Bigtable are optimized for wide-column storage and handle large-scale data analytics, but they might not offer the same level of search functionality as OpenSearch.
- These systems are designed for high throughput and low-latency operations, making them suitable for certain analytical workloads, but they may lack the advanced search and indexing capabilities provided by OpenSearch.
