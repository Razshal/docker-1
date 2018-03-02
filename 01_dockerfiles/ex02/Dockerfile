FROM ruby

RUN echo "deb http://packages.dotdeb.org stable all\ndeb-src http://packages.dotdeb.org stable all\ndeb http://dotdeb.thefox.com.fr stable all\ndeb-src http://dotdeb.thefox.com.fr stable all" > /etc/apt/sources.list.d/dotdeb.list
RUN wget https://www.dotdeb.org/dotdeb.gpg && apt-key add dotdeb.gpg
RUN apt-get update \
&& apt-get install -y --no-install-recommends postgresql-client \
&& apt-get install -y --no-install-recommends sqlite3 \
&& apt-get install -y --no-install-recommends redis-server \
&& rm -rf /var/lib/apt/lists/*

WORKDIR /opt/app
RUN gem install rails
ONBUILD COPY ./* ./
ONBUILD RUN if [ -f Gemfile ]; then bundle install; fi

EXPOSE 3000
