
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

## we can run redis-cli and connect to our Redis server with the following command:
docker-compose​​ ​​run​​ ​​--rm​​ ​​redis​​ ​​redis-cli​​ ​​-h​​ ​​redis​

## Let’s list our currently defined networks using the command:
docker​​ ​​network​​ ​​ls​

## Generating a welcome controller in our Rails app with a single index action:
docker-compose​​ ​​exec​​ ​​web​​ ​​bin/rails​​ ​​g​​ ​​controller​​ ​​welcome​​ ​​index

## To see which container was closed ans the code run:
docker ps -la

## Run docker-compose in Verbose mode
docker-compose --verbose up

## Rails Server Not Starting?
On starting Rails, it’s possible you may encounter the same issue mentioned earlier. If Rails thinks the server is already running, you’ll need to delete tmp/pids/server.pid on your local machine. We’ll see a better way to handle this in Chapter 9.

## Up the postgres container
docker-compose​​ ​​up​​ ​​-d​​ ​​database​

## Check the logs for the an specific container
docker-compose​​ ​​logs​​ ​​database

## Run a command to start the Postgres client
docker-compose​​ ​​run​​ ​​--rm​​ ​​database​​ ​​psql​​ ​​-U​​ ​​postgres​​ ​​-h​​ ​​database​

## To create our development and test databases using the standard Rails command bin/rails db:create, targeting the command at our web service:
docker-compose​​ ​​run​​ ​​--rm​​ ​​web​​ ​​bin/rails​​ ​​db:create

## Restarting the rails server
docker-compose​​ ​​up​​ ​​-d​​ ​​--force-recreate​​ ​​web​

## Create a database
docker-compose​​ ​​exec​​ ​​web​​ ​​\​ ​​bin/rails​​ ​​g​​ ​​scaffold​​ ​​User​​ ​​first_name:string​​ ​​last_name:string​

## Migrate the DB
docker-compose​​ ​​exec​​ ​​web​​ ​​bin/rails​​ ​​db:migrate​

## Webpacker requires Yarn and a current version of Node. This requires an update to our Docker image:
- Allow apt to work with https-based sources​
​RUN apt-get update -yqq && apt-get install -yqq --no-install-recommends \​ ​apt-transport-https​

- Ensure we install an up-to-date version of Node​
- See https://github.com/yarnpkg/yarn/issues/2888​
​​RUN curl -sL https://deb.nodesource.com/setup_8.x | bash - 

- Ensure latest packages for Yarn​
​​RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -​  
​​RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | \​​
  tee /etc/apt/sources.list.d/yarn.list​ 

- Install packages​
​RUN apt-get update -yqq && apt-get install -yqq --no-install-recommends \​​
nodejs \​
​​yarn​    

​