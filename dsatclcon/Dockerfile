# base image
FROM ubuntu:latest
# update not needed with "latest" layer, but no harm
RUN apt-get -y update

# install Tool1: jq (sed for jSON)
RUN apt-get -y install jq
# copy files needed for the Tool1 exercise
COPY nyt.json /usr/local/opt/dsatcl/nyt.json

# install Tool2: json2csv (convert JSON to CSV)
#   first install Go
RUN apt-get -y install golang git
#   install json2csv via go
RUN go get github.com/jehiah/json2csv
# install directly
RUN curl -L https://github.com/jehiah/json2csv/releases/download/v.1.2.0/json2csv-1.2.0.linux-amd64.go1.8.tar.gz | tar -zx
RUN cp json2cvs-1.2.0.linux-amd64.go1.8/json2csv /usr/local/bin

# execute this command when the container is run;
#  i.e., start up in a bash shell
CMD ["/bin/bash"]
