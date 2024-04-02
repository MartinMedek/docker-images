FROM mongo:6.0

LABEL maintainer="Debezium Community"

COPY init-inventory.sh /usr/local/bin/
COPY insert-inventory-data.js /usr/local/bin/

RUN chmod +x /usr/local/bin/init-inventory.sh

# Starting with MongoDB 4.4 the authentication enabled MongoDB requires a key
# for intra-replica set communication
RUN openssl rand -base64 756 > /data/db/mongodb.keyfile &&\
    chown mongodb:mongodb /data/db/mongodb.keyfile &&\
    chmod 400 /data/db/mongodb.keyfile

CMD ["mongod", "--replSet", "rs0", "--auth", "--keyFile", "/data/db/mongodb.keyfile"]
