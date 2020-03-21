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
$ docker-compose run app bundle exec rails new . --force --no-deps --database=postgresql --skip-test --api
```
After that you must change database.yml like belows to connect to your database container.
```yml
default: &default
  adapter: postgresql
  encoding: unicode
  username: postgres
  password: password
  port: 5432
  host: postgres
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
```
Continue re-build images, run container and create database.
```sh
$ docker-compose run --rm app bundle
$ docker-compose up --build
$ docker-compose run --rm app bin/rails db:create db:migrate
```

And then you'll see the rails default page.
