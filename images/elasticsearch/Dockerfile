ARG ELK_VERSION

# https://www.docker.elastic.co/
FROM docker.elastic.co/elasticsearch/elasticsearch:${ELK_VERSION}

ARG ELK_VERSION
COPY ./elasticsearch-analysis-ik-${ELK_VERSION}.zip /
