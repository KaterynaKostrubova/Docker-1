FROM ruby:2.6.3

RUN apt-get update && apt-get -y upgrade && apt-get install -y nodejs
RUN gem update && gem install rails bundler

ONBUILD COPY app /opt/app
ONBUILD WORKDIR /opt/app

ONBUILD EXPOSE 3000
ONBUILD RUN bundle install
ONBUILD RUN rails db:migrate
ONBUILD RUN rails db:seed