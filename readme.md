# Docker Existing Wordpress Example

> Simple example of a Dockerized Existing WordPress app 🐳 👍

## Get Started

This example is using a blank WordPress installation along with a default DataBase. If you want to use your existing WordPress Installation replace wp.sql with your WordPress SQL backup. If you change the name of wp.sql be sure to change the reference to it as well in the `.docker-compose.yaml` file:

```bash
  # Database
  db:
    image: mysql:5.7
    volumes:
      # Ensure wp.sql matches your Wordpress .sql backup in this directory
      - ./wp.sql:/docker-entrypoint-initdb.d/wp.sql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: password
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress
    networks:
      - wpsite
```

Next replace the default Wordpress files in this directory with your Wordpress installation files. Be sure not to delete the `.dockerignore` and `.docker-compose.yaml` files.

To install and run the example, first clone the repository and optionally replace the "dockerExample" directory with your desired name.

```bash
git clone https://github.com/greatdane89/docker-wordpress-existing-example.git dockerExample
```

```bash
#Navigate into proper directory
cd dockerExample

#install dependencies
npm install

#Run the application
npm run start

```

Wordpress: http://localhost:3000
PHPMyAdmin http://localhost:8080

## Commands

```bash
# Run in Docker
docker-compose up
# use -d flag to run in background

# Tear down
docker-compose down

# To be able to edit files, add volume to compose file
volumes: ['./:/usr/src/app']

# To re-build
docker-compose build
```
