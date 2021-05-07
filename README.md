## Docker команды

[Шпаргалка по docker](https://habr.com/ru/company/flant/blog/336654/)  
[DO guide-1](https://www.digitalocean.com/community/tutorials/how-to-build-a-node-js-application-with-docker)  
[DO - How To Secure a Containerized Node.js Application with Nginx, Let's Encrypt, and Docker Compose](https://www.digitalocean.com/community/tutorials/how-to-secure-a-containerized-node-js-application-with-nginx-let-s-encrypt-and-docker-compose)  
[Как установить Nginx в Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/nginx-ubuntu-18-04-ru)

### Команды для Windows
```sh
docker-machine start default
docker-compose up --build
```
### Команды для использования

`docker ps -a`  ---  посмотреть запущеные контейнеры  
`docker run -it <container_name>`  ---  запуск контейнера по идентефикатору  
`docker inspect app_nginx_1 | grep IPAddress | cut -d '"' -f 4`  ---  узнать ip nginx  
`docker exec -it <id of container> bash`  ---  зайти в контейнер и запустить bash  

## Структура

- api -- сервис
- bin --- находятся скрипты для запуска docker
- database -- база данных
- logs -- логи доступа и ошибки nginx
- nginx -- конфигурация прокси-сервера
- static -- статичные файлы (стили, шрифты, скрипты, картинки ...)
- web -- приложение











[![All Contributors](https://img.shields.io/badge/all_contributors-1-orange.svg?style=flat-square)](#contributors)
[![license](https://img.shields.io/github/license/mashape/apistatus.svg?style=flat-square)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

[![Watch on GitHub](https://img.shields.io/github/watchers/paralect/docker-compose-starter.svg?style=social&label=Watch)](https://github.com/paralect/docker-compose-starter/watchers)
[![Star on GitHub](https://img.shields.io/github/stars/auxilincom/docker-compose-starter.svg?style=social&label=Stars)](https://github.com/auxilincom/docker-compose-starter/stargazers)
[![Follow](https://img.shields.io/twitter/follow/auxilincom.svg?style=social&label=Follow)](https://twitter.com/auxilin)
[![Tweet](https://img.shields.io/twitter/url/https/github.com/auxilincom/docker-compose-starter.svg?style=social)](https://twitter.com/intent/tweet?text=I%20run%20my%20development%20environment%20with%20a%20simple%20command%20using%20docker-compose%20%F0%9F%9A%80.%20Check%20it%20out:%20https://github.com/auxilincom/docker-compose-starter)

Run your development environment with a single command using docker-compose 🚀.
This repository was boarn with aim to share how simple development environment could be with [docker-compose](https://docs.docker.com/compose/). If you ever had to perform 100 steps to run a new project you will like this a lot. You could read more on the problem in [this blog post](https://blog.maqpie.com/2017/02/22/fully-automated-development-environment-with-docker-compose/).

## Features

* 🔥 **Simple project start** run your development evnrionment with a single command
* 🙀 **Environment agnostic** with [docker-compose](https://docs.docker.com/compose/) you can run your project on Mac, Windows or Linux environments without any issues.
* ️⚡️ **Multi-language projects** choose whatever language you need to solve the problem, but keep development environment easy for developers.

## Getting Started

`./bin/start.sh` — starts entire application
`./bin/run-tests.sh` — runs tests using docker-compose

The repository consists 4 demo-purpose independent services: 
1. Landing - a landing site
2. Web - a simple frontend that serves client side assets for React application and do some server side rendering.
3. Api - a restful api.
4. Admin - an admin site

For learning purpose just pay attention to the following files: 
1. [Dockerfile](./api/Dockerfile)
2. [Dockerfile.dev](./api/Dockerfile.dev)
3. [package.json](./api/package.json)
4. [docker-compose.yml](./docker-compose.yml)
5. [docker-compose.local-tests.yml](./docker-compose.local-tests.yml)
6. [.env](./.env)

### Separate Dockerfile for development

Dockerfile.dev used to run every project on local environment. There are two reasons for using separate dockerfile for local environments:

1. To run application using Nodemon, which automatically restart application on code change. (same can be achieved by overriding `command` in docker-compose.yml)
2. Production Docker files has `npm run build && npm prune --production`. That needed to keep your Docker images smaller, by removing devDependencies after `build` step has been completed. In this step you would typically use Webpack, Gulp or any other bundlers / task runners.

If image size is not an issue - I would recommend to keep same Dockerfile for both development and production environments. You might also want to look into [this](https://github.com/paralect/docker-compose-starter/issues/3) discussion

## Прототип
[Github](https://github.com/paralect/docker-compose-starter/)
