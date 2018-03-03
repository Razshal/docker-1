FROM ruby:2.4.2

RUN mkdir /opt/app
WORKDIR /opt/app
RUN mkdir install
RUN mkdir finalapp
WORKDIR /opt/app/install
RUN gem install rails
RUN gem install rails-server
ONBUILD COPY . /opt/app/install
ONBUILD RUN if [ -f Gemfile ]; then bundle install --binstubs; fi
ONBUILD RUN rails new ../finalapp
ONBUILD WORKDIR /opt/app/finalapp
ONBUILD EXPOSE 3000
