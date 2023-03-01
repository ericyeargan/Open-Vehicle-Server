FROM ubuntu:22.04

RUN echo 'APT::Install-Suggests "0";' >> /etc/apt/apt.conf.d/00-docker
RUN echo 'APT::Install-Recommends "0";' >> /etc/apt/apt.conf.d/00-docker

RUN DEBIAN_FRONTEND=noninteractive \
  apt-get update \
  && apt-get install -y \
  perl cpanminus build-essential mysql-client libdbd-mysql-perl libssl-dev zlib1g-dev openssl \
  && rm -rf /var/lib/apt/lists/*

RUN cpanm install \
Net::SSLeay \
Config::IniFiles \
Digest::MD5 \
Digest::HMAC \
Crypt::RC4::XS \
MIME::Base64 \
DBI \
DBD::mysql \
EV \
AnyEvent \
AnyEvent::HTTP \
AnyEvent::HTTPD \
HTTP::Parser::XS \
Data::UUID \
Email::MIME \
Email::Sender::Simple \
JSON::XS \
Protocol::WebSocket \
Time::Piece 

COPY server/ server/
WORKDIR server/
CMD ./ovms_server.pl

