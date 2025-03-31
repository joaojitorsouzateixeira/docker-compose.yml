# docker-compose.yml
##Atividade1##

yaml
version: '3.8'

services:
  db:
    image: mysql:8.0
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
      MYSQL_DATABASE: joomla
      MYSQL_USER: joomlauser
      MYSQL_PASSWORD: joomlapassword
    volumes:
      - db_data:/var/lib/mysql

  joomla:
    image: joomla:latest
    restart: always
    ports:
      - "8080:80"
    environment:
      JOOMLA_DB_HOST: db
      JOOMLA_DB_USER: joomlauser
      JOOMLA_DB_PASSWORD: joomlapassword
      JOOMLA_DB_NAME: joomla
    depends_on:
      - db

volumes:
  db_data:
