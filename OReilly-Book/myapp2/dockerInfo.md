
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