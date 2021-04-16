
## Criar un container com CMD:
docker​​ ​​run​​ ​​-i​​ ​​-t​​ ​​--rm​​ ​​-v​​ ​​${PWD}:/usr/src/app​​ ​​ruby:2.6​​ ​​bash​

## Dockerfile exemplo:

​ 	FROM ruby:2.6
​ 	
​ 	RUN apt-get update -yqq
​ 	RUN apt-get install -yqq --no-install-recommends nodejs
​ 	
​ 	COPY . /usr/src/app/
​ 	
​ 	WORKDIR /usr/src/app
​ 	RUN bundle install


## para rodar o rails server no container
docker​​ ​​run​​ ​​-p​​ ​​3000:3000​​ ​​Image_Name​​ ​​\​​​bin/rails​​ ​​s​​ ​​-b​​ ​​0.0.0.0​

## Para dar nome ao Container
docker tag _image_ID_ colocque o nome que deseja

## Para mudar a versao de latest para sua escolha (Ex. 1.0)
docker tag railsapp railsapp:1.0 

## Voce pode construir sua image ja com tag e versao (Ex. abaixo:)
​​docker​​ ​​build​​ ​​-t​​ ​​railsapp​​ ​​-t​​ ​​railsapp:1.0​​ ​​.​

## Para cada inserçao no Dockerfile deve-se re buildar pelo commando (Ex.)
docker​​ ​​build​​ ​​-t​​ ​​railsapp​​ ​​.

## Para rodas o container agora faça (Ex.)
​​docker​​ ​​run​​ ​​-p​​ ​​3000:3000​​ ​​railsapp

## Containers in detached mode by specifying the -d option, run:
docker-compose​​ ​​up​​ ​​-d​

## To check what containers are currently running
docker-compose​​ ​​ps​

## To stop all containers in the entire application, we would run:
docker-compose​​ ​​stop​

## To target a particular service, we’d specify the service name after the action like so:
docker-compose​​ ​​stop​​ ​​<service_name>

## viewing the container logs:
docker-compose​​ ​​logs​​ ​​-f​​ ​​web

## Pruning: Freeing Up Unused Resources:
docker image prune

docker container prune

docker system prune

## Docker to run a container based on the official Docker redis image.
docker​​ ​​run​​ ​​--name​​ ​​redis-container​​ ​​redis​

