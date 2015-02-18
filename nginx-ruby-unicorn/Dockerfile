FROM nginx:1.7.9
MAINTAINER Ryan Mathews <ryan@ryanjm.com>

# Ruby Dependencies
RUN apt-get update && apt-get install -y \
  build-essential \
  zlib1g-dev \
  libssl-dev \
  libreadline6-dev \
  libyaml-dev \
  wget \
  ca-certificates \
  git \
  postgresql \
  postgresql-contrib \
  libpq-dev


# Install ruby
ENV RUBY_VERSION 2.0.0-p481
WORKDIR /tmp
RUN wget http://cache.ruby-lang.org/pub/ruby/2.0/ruby-$RUBY_VERSION.tar.gz
RUN tar -xvzf ruby-$RUBY_VERSION.tar.gz

WORKDIR /tmp/ruby-$RUBY_VERSION/
RUN ./configure --prefix=/usr/local
RUN make
RUN make install

# Install bundler
RUN gem install bundler --no-ri --no-rdoc

# Install unicorn
RUN gem install unicorn --no-ri --no-rdoc
