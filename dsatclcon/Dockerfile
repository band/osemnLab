# base image
FROM ubuntu:latest
# update not needed with "latest" layer, but no harm
RUN apt-get -y update

# install Tool1 jq
RUN apt-get -y install jq

# copy files needed for the app to run
COPY nyt.json /usr/local/opt/dsatcl/nyt.json

# execute this command when the container is run;
#  i.e., start up in a bash shell
CMD ["/bin/bash"]
