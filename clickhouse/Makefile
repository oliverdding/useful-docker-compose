.PHONY: config
config:
	mkdir -p clickhouse0{1,2,3,4}/{config,data} zookeeper0{1,2,3}
	REPLICA=01 SHARD=01 envsubst < config.xml > clickhouse01/config/config.xml
	REPLICA=02 SHARD=01 envsubst < config.xml > clickhouse02/config/config.xml
	REPLICA=03 SHARD=02 envsubst < config.xml > clickhouse03/config/config.xml
	REPLICA=04 SHARD=02 envsubst < config.xml > clickhouse04/config/config.xml
	cp users.xml clickhouse01/config/users.xml
	cp users.xml clickhouse02/config/users.xml
	cp users.xml clickhouse03/config/users.xml
	cp users.xml clickhouse04/config/users.xml

.PHONY: up
up:
	docker-compose up -d

.PHONY: start
start:
	docker-compose start

.PHONY: down
down:
	docker-compose down

.PHONY: clean
clean:
	rm -rf clickhouse0{1,2,3,4} zookeeper0{1,2,3}
