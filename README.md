# HAProxy MongoDB Read Load Balancer

This project configures `HAProxy` as a TCP load balancer to route **read requests** to `MongoDB secondaries` in a replica set.

## 🧠 Purpose

MongoDB replica sets typically serve **write** operations via the primary node, while **read** operations can be distributed among the secondaries to balance the load. It is tightly coupled with the [`mongodb-replicaset`](https://github.com/azita-abdollahi/mongodb-replicaset-docker) project, which defines the MongoDB replica set nodes this service connects to.

## 🔧 How It Works

- **HAProxy** listens on port `27018`
- Distributes incoming MongoDB read traffic to `mongodb2` and `mongodb3`
- Ensures high availability and read scalability
- Provides a monitoring dashboard on port `8404`

## ⚙️ Setup

1. Clone the [mongodb-replicaset](https://github.com/azita-abdollahi/mongodb-replicaset-docker) repo and follow setup instructions
2. Ensure all MongoDB containers are healthy and in the same Docker network (`connet`)
3. Create a `replica.key` and the Docker network. [`read mongodb replicaset readme`](https://github.com/azita-abdollahi/mongodb-replicaset-docker?tab=readme-ov-file#-requirements)

4.Run HAProxy:

```bash
docker compose up -d
```

## 📊 Accessing Stats

​    Visit: http://localhost:8404

​    Login with: admin / admin123

## 📚 Learn More

See the Wiki for full documentation:

[Home](https://github.com/azita-abdollahi/haproxy-mongodb-balancer/wiki)

​    [About HAProxy](https://github.com/azita-abdollahi/haproxy-mongodb-balancer/wiki/About-HAProxy)

​    [How It Balances Mongo Reads](https://github.com/azita-abdollahi/haproxy-mongodb-balancer/wiki/How-HAProxy-Balances-Mongo-Reads)

​    [Accessing HAProxy Stats](https://github.com/azita-abdollahi/haproxy-mongodb-balancer/wiki/Accessing-HAProxy-Stats)