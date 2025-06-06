{% include templates/install/queue-confluent-cloud-config.md %}

Configure Klyff environment file:

```text
nano .env
```
{: .copy-code}

Check following line:

```bash
TB_QUEUE_TYPE=confluent
```
{: .copy-code}

Configure Confluent Cloud environment file for Klyff queue service:

```text
nano queue-confluent-cloud.env
```
{: .copy-code}

Don’t forget to replace "CLUSTER_API_KEY", "CLUSTER_API_SECRET" and "confluent.cloud:9092" with your real Confluent Cloud bootstrap servers:

```bash
TB_QUEUE_TYPE=kafka

TB_KAFKA_SERVERS=confluent.cloud:9092
TB_QUEUE_KAFKA_REPLICATION_FACTOR=3

TB_QUEUE_KAFKA_USE_CONFLUENT_CLOUD=true
TB_QUEUE_KAFKA_CONFLUENT_SSL_ALGORITHM=https
TB_QUEUE_KAFKA_CONFLUENT_SASL_MECHANISM=PLAIN
TB_QUEUE_KAFKA_CONFLUENT_SASL_JAAS_CONFIG='org.apache.kafka.common.security.plain.PlainLoginModule required username="CLUSTER_API_KEY" password="CLUSTER_API_SECRET";'
TB_QUEUE_KAFKA_CONFLUENT_SECURITY_PROTOCOL=SASL_SSL
TB_QUEUE_KAFKA_CONFLUENT_USERNAME=CLUSTER_API_KEY
TB_QUEUE_KAFKA_CONFLUENT_PASSWORD=CLUSTER_API_SECRET

TB_QUEUE_KAFKA_RE_TOPIC_PROPERTIES=retention.ms:604800000;segment.bytes:52428800;retention.bytes:1048576000
TB_QUEUE_KAFKA_CORE_TOPIC_PROPERTIES=retention.ms:604800000;segment.bytes:52428800;retention.bytes:1048576000
TB_QUEUE_KAFKA_TA_TOPIC_PROPERTIES=retention.ms:604800000;segment.bytes:52428800;retention.bytes:1048576000
TB_QUEUE_KAFKA_NOTIFICATIONS_TOPIC_PROPERTIES=retention.ms:604800000;segment.bytes:52428800;retention.bytes:1048576000
TB_QUEUE_KAFKA_JE_TOPIC_PROPERTIES=retention.ms:604800000;segment.bytes:52428800;retention.bytes:104857600

# These params affect the number of requests per second from each partitions per each queue.
# Number of requests to particular Message Queue is calculated based on the formula:
# ((Number of Rule Engine and Core Queues) * (Number of partitions per Queue) + (Number of transport queues)
#  + (Number of microservices) + (Number of JS executors)) * 1000 / POLL_INTERVAL_MS
# For example, number of requests based on default parameters is:

# Rule Engine queues:
# Main 10 partitions + HighPriority 10 partitions + SequentialByOriginator 10 partitions = 30
# Core queue 10 partitions
# Transport request Queue + response Queue = 2
# Rule Engine Transport notifications Queue + Core Transport notifications Queue = 2
# Total = 44
# Number of requests per second = 44 * 1000 / 25 = 1760 requests

# Based on the use case, you can compromise latency and decrease number of partitions/requests to the queue, if the message load is low.
# By UI set the parameters - interval (1000) and partitions (1) for Rule Engine queues.
# Sample parameters to fit into 10 requests per second on a "monolith" deployment: 

TB_QUEUE_CORE_POLL_INTERVAL_MS=1000
TB_QUEUE_CORE_PARTITIONS=2
TB_QUEUE_RULE_ENGINE_POLL_INTERVAL_MS=1000
TB_QUEUE_TRANSPORT_REQUEST_POLL_INTERVAL_MS=1000
TB_QUEUE_TRANSPORT_RESPONSE_POLL_INTERVAL_MS=1000
TB_QUEUE_TRANSPORT_NOTIFICATIONS_POLL_INTERVAL_MS=1000
TB_QUEUE_VC_INTERVAL_MS=1000
TB_QUEUE_VC_PARTITIONS=1
```
{: .copy-code}

You can update default Rule Engine queues configuration using UI. More about Klyff Rule Engine queues see in [documentation](/docs/{{docsPrefix}}user-guide/rule-engine-2-5/queues/).
