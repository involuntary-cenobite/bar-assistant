Tasks needed before we run docker compose up

0) NPM continer set up

--
1) Create external network for proxy
   $docker network create proxy_net
--
2) NPM needs a mod to work with this container
  a) $touch ./_hsts_map.conf
  b) add the mapping to the proy container
    volumes:
      - ./_hsts_map.conf:/app/templates/_hsts_map.conf
--
3) Set bar assistant proxy configuation
--
- proxy host

scheme = http
forward = salt-rim
port = 8080


- custom locations

location = /bar/ 
scheme = http
forward hostname = bar-assistant/ (forward slash needed)
forward port = 3000

location = /search/ 
scheme = http
forward hostname = meilisearch/ (forward slash needed)
forward port = 7700


- enable SSL

- create cert

--
4) Modify the .env configuration with your opeions

a) set password
b) set url to what is set in your registrar (use https)
