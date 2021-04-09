FROM ruby:2.7.2

RUN apt-get update -yqq
RUN apt-get install -yqq --no-install-recommends nodejs yarn

COPY . /usr/src/app/

WORKDIR /usr/src/app
RUN bundle install