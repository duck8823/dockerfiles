FROM openjdk:10

WORKDIR /tmp

RUN apt-get update \
 && apt-get -y install build-essential \
                       automake \
                       zlib1g-dev \
                       libssl-dev \
 && apt-get clean \
 && wget --no-check-certificate -q https://cache.ruby-lang.org/pub/ruby/2.6/ruby-2.6.3.tar.gz \
 && tar zxvf ruby-2.6.3.tar.gz \
 && cd ruby-2.6.3 \
 && ./configure \
 && make \
 && make install \
 && cd .. \
 && rm -fr ruby-2.6.3*

