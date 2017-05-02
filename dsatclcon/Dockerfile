# base image
FROM ubuntu:16.04
RUN apt-get -y update

# install Tool1 jq
RUN apt-get -y install jq

# copy files needed for the app to run
COPY nyt.json /usr/local/opt/dsatcl/nyt.json

# provide a command-line terminal to carry out the exercises
# interactive terminal can be specified on the command line

