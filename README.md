YADC (unstable)
===

Yet Another Dockerized CouchDB (for testing and RC versions of couchdb).
Version: `CouchDB 1.6.1rc4`

If you're looking for a stable CouchDB you can check out [klaemo/couchdb](https://index.docker.io/u/klaemo/couchdb/)

If you're looking for a CouchDB with SSL support you can check out [klaemo/couchdb-ssl](https://index.docker.io/u/klaemo/couchdb-ssl/)


## Run

Available in the docker index as [klaemo/couchdb-testing](https://index.docker.io/u/klaemo/couchdb-testing/)

```bash
[sudo] docker pull klaemo/couchdb-testing

# expose it to the world on port 5984
[sudo] docker run -d -p 5984:5984 -name couchdb klaemo/couchdb-testing

curl http://localhost:5984
```

## Features

* exposes couchdb on port `5984` of the container
* runs everything as user `couchdb` (security ftw!)

## Build your own

You can use `klaemo/couchdb-testing` as the base image for your own couchdb instance.
You might want to provide your own version of the following files:

* `local.ini` for CouchDB

Example Dockerfile:
```
FROM klaemo/couchdb-testing

ADD local.ini /usr/local/etc/couchdb/
```

and then build and run

```
[sudo] docker build -rm -t you/awesome-couchdb .
[sudo] docker run -d -p 5984:5984 -v ~/couchdb:/usr/local/var/lib/couchdb you/awesome-couchdb
```
