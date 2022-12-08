Pour builder et démarrer les containers :
```
docker-compose up -d
```

```
docker-compose exec tools bash
kafka-topics --bootstrap-server kafka-1:9092 --list

export KAFKA_OPTS="-javaagent:/agents/jmx_prometheus_javaagent-0.13.0.jar=7071:/agents/client.yaml"
kafka-console-producer --bootstrap-server kafka-1:9092 --topic test
kafka-producer-perf-test --topic test --num-records 1000000 --record-size 50 --throughput 100000 --producer.config /clients/producer.properties

export KAFKA_OPTS="-javaagent:/agents/jmx_prometheus_javaagent-0.13.0.jar=7072:/agents/client.yaml"
kafka-console-consumer --bootstrap-server kafka-1:9092 --topic test --group mytest
kafka-consumer-perf-test --bootstrap-server kafka-1:9092 --topic test --consumer.config /clients/consumer.properties --messages 100000
```

grafana => http://localhost:3000/  (admin/admin)

prometheus => http://localhost:9090/

Pour tout nettoyer :
```
docker-compose down -v
```
