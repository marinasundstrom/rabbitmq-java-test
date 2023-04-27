# RabbitMQ test

```java
podman pull docker.io/library/rabbitmq:latest

RABBITMQ_ERLANG_COOKIE="SomeRandomStringHere"
HOSTNAME="rabbit00"

podman run -d \
    --hostname ${HOSTNAME}.kresy.local \
    --name ${HOSTNAME} \
    -p 5672:5672 \
    -e RABBITMQ_ERLANG_COOKIE=${RABBITMQ_ERLANG_COOKIE} \
    -e RABBITMQ_NODENAME=rabbit@${HOSTNAME} \
    docker.io/library/rabbitmq:latest
```

With Management Plugin:

```java        
podman pull docker.io/library/rabbitmq:management

RABBITMQ_ERLANG_COOKIE="SomeRandomStringHere"
HOSTNAME="rabbit01"

podman run -d \
    --hostname ${HOSTNAME}.kresy.local \
    --name ${HOSTNAME} \
    -p 5672:5672 \
    -p 15672:15672 \
    -e RABBITMQ_ERLANG_COOKIE=${RABBITMQ_ERLANG_COOKIE} \
    -e RABBITMQ_NODENAME=rabbit@${HOSTNAME} \
    docker.io/library/rabbitmq:management
```


``sh
mvn package
podman image build -t t-server:latest .
``