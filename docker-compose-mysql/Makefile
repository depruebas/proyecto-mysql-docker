#!/bin/bash

U_ID = $(shell id -u)

up: ## start containers
	@echo 'Iniciando containers: UserUID=${U_ID} docker-compose up -d'
	UserUID=${U_ID} docker-compose up -d 

stop:
	@echo 'Parando containers:  docker-compose stop'
	UserUID=${U_ID}  docker-compose stop

down:
	@echo 'Parando containers:  docker-compose down'
	UserUID=${U_ID}  docker-compose down

mysql:
	UserUID=${U_ID} docker exec -it --user ${U_ID} mysql_dev mysql -u root -proot
  
shell:
	UserUID=${U_ID} docker exec -it --user ${U_ID} mysql_dev bash

build:
	@echo 'Reiniciando containers: UserUID=${U_ID} docker-compose build'
	UserUID=${U_ID} docker-compose build
