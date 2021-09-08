# Open Search Setup with Docker

All necessary changes have been made in `Dockerfile` and `docker-compose.yml` file as per document to run opensearch without security plugin.


## Build docker images locally

- `cd open-search && docker build -t opensearch-nosecurity:1.0.1 .`
- `cd opensearch-dashboard && docker build -t opensearch-dashboard-nosecurity:1.0.1 .`

## Run Open Search as a single docker container

`docker run -it -p9200:9200 -p9600:9600 -e "discovery.type=single-node" -e  "OPENSEARCH_JAVA_OPTS=-Xmx1024m -Xms1024m" opensearch-nosecurity:1.0.1`


## Run Open search in cluster mode with Docker compose

`docker-compose up -d`

## Create Index

`curl -X PUT -H 'Content-type:application/json' --data-binary @myschema.json "http://localhost:9200/myindex"`

## Reference

- https://opensearch.org/docs/security-plugin/configuration/disable/ 