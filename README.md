# DeepScholar-ES
This repository provides a dockerfile for using Elasticsearch in DeepScholar.

## Setup
1. Copy the sample files
```
cp .env.sample .env
cp docker-compose.yml.sample docker-compose.yml
```

2. Set the id and password in `.env`
```
ELASTICSEARCH_AUTH_ID=ABCDEFGHIJKLMN
ELASTICSEARCH_AUTH_PASSWORD=01234567890
```

3. Run docker-compose
```
docker-compose -f docker-compose.yml up
```

The authorization header is required to access Elasticsearch.
* Without the header, the server responds 403 Forbidden
```
curl -I http://localhost:8080/
HTTP/1.1 403 Forbidden
Server: nginx/1.15.6
Date: Fri, 25 Jan 2019 14:31:07 GMT
Content-Type: text/html
Content-Length: 153
Connection: keep-alive
```

* With the valid header, the server responds successfully
```
$ curl -I -u ABCDEFGHIJKLMN:01234567890 http://localhost:8080/
HTTP/1.1 200 OK
Server: nginx/1.15.6
Date: Fri, 25 Jan 2019 14:30:26 GMT
Content-Type: application/json; charset=UTF-8
Content-Length: 494
Connection: keep-alive
```
