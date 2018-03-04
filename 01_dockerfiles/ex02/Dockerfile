FROM ruby

RUN apt-get update && apt-get install -y --no-install-recommends nodejs postgresql \
sqlite3 build-essential postgresql-contrib postgresql-server-dev-all

RUN mkdir /opt/app
WORKDIR /opt/app
RUN gem install bundler rails rails-server activerecord-postgresql-adapter postgresql sqlite3
ONBUILD COPY . /opt/app/
ONBUILD RUN if [ -f config/database.yml.example ]; then mv config/database.yml.example config/database.yml; fi
ONBUILD RUN if [ -f config/example.application.yml ]; then cp config/example.application.yml config/application.yml; fi
ONBUILD RUN if [ -f Gemfile ]; then bundle update && bundle install; fi
ONBUILD RUN if ! rails db:create; then echo "create failed"; fi
ONBUILD RUN if ! rails db:migrate; then echo "migrate failed"; fi

ONBUILD EXPOSE 3000
