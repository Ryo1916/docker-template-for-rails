# Docker template for Ruby on Rails
This is the Dockerfile and docker-compose.yml templates for Ruby on Rails application.
- Dockerfile
  - base: alpine
  - ruby: 2.6
- docker-compose.yml
  - version: 3.7
  - postgres: latest
  - redis: latest

### Usage
Before execute the below commands, change versions, hostname, ports, base image or others if you want.
```sh
$ docker-compose build
$ docker-compose run web bundle exec rails new . --force --no-deps --database=postgresql
$ docker-compose up --build
```
