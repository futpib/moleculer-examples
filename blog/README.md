# Blog example
![Blog screenshot](../assets/screenshots/blog-screenshot.jpg)

## :triangular_flag_on_post: Features
- multiple services (www, posts, users)
- Docker files to running in Docker containers (3 architectures)
- ExpressJS www server with Pug
- MongoDB database with [moleculer-db]() and [moleculer-db-adapter-mongoose]() modules
- NATS transporter
- Redis cacher
- [Traefik](https://traefik.io/) reverse proxy (in micro arch)
- static client side

## :nut_and_bolt: Install
```bash
git clone https://github.com/ice-services/moleculer-examples.git
cd blog
```

## :game_die: Start locally
To start locally, you need to running a MongoDB server on localhost.
```bash
npm install
npm start
```

**Open the [http://localhost:3000/](http://localhost:3000/) URL in your browser.**


## :cloud: Start in Docker

>First you need to build the `moleculer-blog` image. You can use the `npm run docker:build` command or `docker build -t moleculer-blog`

### :house: Running as monolith 
_All services are running in a container._
```bash
cd docker/mono
docker-compose up
# or 
# ./start.sh
```
**Open the http://docker-machine:3000/ URL in your browser.**

### :office: Running as microservices 
_All services are running in separated containers, communicate via NATS & use Traefik reverse proxy._
```bash
cd docker/micro
docker-compose up
# or 
# ./start.sh
```
**Open the http://docker-machine:3000/ URL in your browser.**

You can scale up the containers
```bash
# Scale up the users service to 2 instances
docker-compose scale users=2
```

You can scale up the WWW service as well. Traefik is load balancing the requests to instances.
```bash
# Scale up the WWW service to 2 instances
docker-compose scale www=2
```

### :hotel: Running as mixed
_Coherent services are running in the same container and communicate via NATS._
```bash
cd docker/mixed
docker-compose up
# or 
# ./start.sh
```
**Open the http://docker-machine:3000/ URL in your browser.**

You can scale up the containers
```bash
# Scale up the group1 container to 2 instances
docker-compose scale group1=2
```

## :wrench: Development locally
_Running MongoDB is required on localhost!_

```bash
npm run dev
```

## :cloud: Development in Docker (without dependencies)
In this case you don't need MongoDB, what is more, you don't need NodeJS environment. Everything is in Docker.

```bash
cd docker/dev
docker-compose up
```

_If you change source files, the app will be restarted automatically._

# License
This repo is available under the [MIT license](https://tldrlegal.com/license/mit-license).

# Contact
Copyright (c) 2016-2017 Ice Services

[![@ice-services](https://img.shields.io/badge/github-ice--services-green.svg)](https://github.com/ice-services) [![@MoleculerJS](https://img.shields.io/badge/twitter-MoleculerJS-blue.svg)](https://twitter.com/MoleculerJS)