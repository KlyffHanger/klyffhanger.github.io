{% include templates/install/queue-kafka-in-docker.md %}

##### Klyff Configuration

Edit Klyff configuration file

```text
sudo nano /etc/thingsboard/conf/thingsboard.conf
```
{: .copy-code}

Add the following line to the configuration file. **Don't forget** to replace "localhost:9092" with your real Kafka bootstrap servers:

```bash
export TB_QUEUE_TYPE=kafka
export TB_KAFKA_SERVERS=localhost:9092
```
{: .copy-code}