
# Experient Lakehouse

A minimal modern data stack based on the lakehouse architecture using Apache Iceberg

## Dependencies
A Minio (S3) endpoint and access keys running locally on the host machine (host.docker.internal)

## Usage
Start up the lakehouse engine through.
```
docker-compose up
```

The Jupyter server will then be available at http://localhost:8888

The following query engines can be interactively launched from the host:
```
docker exec -it lakehouse spark-shell
```
```
docker exec -it lakehouse spark-sql
```
```
docker exec -it lakehouse pyspark
```

To stop everything, just run `docker-compose down`.

## Building the Docker Image 

If you want to make changes to the local files, and test them out, you can build the image locally and use that instead:

```bash
docker image rm experient/lakehouse && docker-compose build
```


### Publishing to Dockerhub

To deploy changes to the hosted docker image `experient/lakehouse`, run the following:

```sh
cd spark
docker buildx build -t experient/spark-iceberg --platform=linux/amd64,linux/arm64 . --push
```
