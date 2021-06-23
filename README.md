# Rabbit test cluster

Test environment for RabbitMQ cluster based on docker compose

## How to stat it up

Run `docker-compose up`, once the containers started, stop them an copy `./erlang.cookie` file to `mnesia*/.erlang.cookie`, then restart the containers.

Once all 3 containers are running, you have to join node 2 and 3 to the cluster, so go inside each container (`rabbit-compose-cluster_rabbitmq2_1` and `rabbit-compose-cluster_rabbitmq3_1`) and run the following commands:

```
rabbitmqctl stop_app
rabbitmqctl reset
rabbitmqctl join_cluster rabbit@rabbitmq1
rabbitmqctl start_app
```