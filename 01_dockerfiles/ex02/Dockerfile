FROM ruby:2.4.2

RUN apt-get update && apt-get install -y --no-install-recommends nodejs postgresql \
sqlite3 build-essential postgresql-contrib postgresql-server-dev-all

RUN mkdir /opt/app
WORKDIR /opt/app
RUN gem install bundler
RUN gem install rails
RUN gem install rails-server
RUN gem install activerecord-postgresql-adapter
ONBUILD COPY . /opt/app/
ONBUILD RUN bundle update && if [ -f Gemfile ]; then bundle install; fi
ONBUILD RUN if [ -f config/database.yml.example ]; then mv config/database.yml.example config/database.yml; fi
ONBUILD RUN if [ -f config/example.application.yml ]; then cp config/example.application.yml config/application.yml; fi
ONBUILD RUN rake db:setup
ONBUILD RUN gem install json && if ! rails new appli; then echo "already compiled"; fi

ONBUILD EXPOSE 3000
