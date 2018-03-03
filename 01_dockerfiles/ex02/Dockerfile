FROM ruby:2.4.2

RUN apt-get update && apt-get install -y --no-install-recommends nodejs && apt-get install postgresql -y --no-install-recommends


RUN mkdir /opt/app
WORKDIR /opt/app
RUN gem install bundler
RUN gem install rails
RUN gem install rails-server
ONBUILD COPY . /opt/app/
ONBUILD RUN bundle update && if [ -f Gemfile ]; then bundle install; fi
ONBUILD RUN if [ -f config/database.yml.example ]; then mv config/database.yml.example config/database.yml; fi
ONBUILD RUN bundle config && gem install rake && if [ -f Rakefile ]; then rake; fi
ONBUILD RUN gem install json && rails new appli
ONBUILD WORKDIR /opt/app/appli

ONBUILD EXPOSE 3000
