# MongoDB Single Node ReplicaSet using Docker Compose

## Overview


This repository contains a `docker-compose.yaml` and a MongoDB replica set initiation script (`rs-initiate.js`) to quickly set up a single-node MongoDB replica set using Docker Compose.

## Pre-requisites

- Docker
- Docker Compose

## How to Use

### Step 1: Clone the Repository

Clone the repository to your local machine.

```bash
git clone git@github.com:numan-qapita/mongo-docker-sn-rs.git
```

### Step 2: Navigate to the Directory

Navigate to the directory where you have cloned the repo    .

```bash
cd mongo-docker-sn-rs
```

### Step 3: Start the MongoDB Service

Run the following command to start the MongoDB service as a single-node replica set.

```bash
docker compose up -d
```

This command will start the MongoDB container with the replica set name as `q-db-sn-rs`. The MongoDB service will bind to the default port `27017`.

### Step 4: Check the Status

To confirm that the replica set has been initiated, you can access the MongoDB shell by entering the running MongoDB container.

```bash
docker exec -it q-mongo-sn-rs mongo
```

Then run:

```javascript
rs.status()
```

This will display the replica set status.

## Configuration

### Docker Compose Configuration

Here are some key attributes of the `docker-compose.yaml`:

- **image**: Specifies the MongoDB Docker image. Set to use the latest version.
- **ports**: Maps the container port 27017 to the host port 27017.
- **volumes**: Specifies the data and config volumes, as well as the initiation script.
- **command**: Specifies the command that is run when the container starts. In this case, it starts MongoDB with the given replica set name and binds it to all available IP addresses.

### Replica Set Initialization

The `rs-initiate.js` file contains the logic for initializing the MongoDB replica set. Right now, it simply calls `rs.initiate()`.

## Troubleshooting

If you face any issues, you can check the logs by running:

```bash
docker logs q-mongo-sn-rs
```

## Cleanup

To stop and remove the running container, run:

```bash
docker-compose down
```

## Contributing

If you have suggestions or improvements, feel free to contribute.

---

This README aims to provide all the necessary steps and details to get you up and running with a single-node MongoDB replica set using this Docker Compose configuration. Feel free to reach out if you have any issues or questions.