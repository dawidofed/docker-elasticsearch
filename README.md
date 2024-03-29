***Default***

This is docker image for elasticsearch 5.5.1 without x-pack plugin.


***Default ENV on image***
```bash
ENV http.host 0.0.0.0
ENV transport.host 127.0.0.1
```

***Warning!***
If your user id is not 1000 you need to create directory and set full permission on it.

```bash
mkdir elastic-search
chmod 777 elastic-search
```

***Default*** 

```bash
docker run -it -v `pwd`/elastic-search:/usr/share/elasticsearch/data dawidoFed/docker-elasticsearch:latest
```

***Docker compose***

```bash
version: '1'
services:
  search:
    image: dawidofed/docker-elasticsearch:latest
    volumes:
      - ./elastic-search:/usr/share/elasticsearch/data
```

***Docker stack***

```bash
version: '3'
services:
  search:
    image: dawidofed/docker-elasticsearch:latest
    volumes:
      - ./elastic-search:/usr/share/elasticsearch/data
    deploy:
      mode: global
```

***ENV override***

```bash
version: '2'
services:
  search:
    image: dawidofed/docker-elasticsearch:latest
    volumes:
      - ./elastic-search:/usr/share/elasticsearch/data
    environment:
      - "http.host=0.0.0.0"
```