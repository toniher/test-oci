FROM debian:bookworm

ARG PERLBREW_ROOT=/usr/local/perl
ARG PERL_VERSION=5.40.0
# Enable perl build options. Example: --build-arg PERL_BUILD="--thread --debug"
ARG PERL_BUILD=--thread

# Base Perl and builddep
RUN set -x; \
  apt-get update && apt-get upgrade -y; \
  apt-get install -y perl bzip2 zip curl \
  build-essential procps
#RUN apt-get build-dep perl

# Clean cache
RUN apt-get clean
RUN set -x; rm -rf /var/lib/apt/lists/*

# Workdir place
RUN mkdir -p /project
WORKDIR /project

#ENTRYPOINT ["./entrypoint.sh"]

