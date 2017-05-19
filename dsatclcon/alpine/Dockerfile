FROM alpine:edge
RUN apk update
RUN apk add bash
RUN apk add curl git

# install Tool1 (jq)
RUN apk add jq
COPY nyt.json /usr/local/opt/dsatcl/nyt.json

# install Tool2: json2csv (convert JSON to CSV)
RUN cd /tmp && curl -L https://github.com/jehiah/json2csv/releases/download/v.1.2.0/json2csv-1.2.0.linux-amd64.go1.8.tar.gz | tar -zx
RUN cp -v /tmp/json2csv-1.2.0.linux-amd64.go1.8/json2csv /usr/local/bin

# install Tool3 (csvkit)
RUN apk add python \
    python-dev \
    py-pip
RUN pip install --upgrade pip
RUN pip install csvkit
RUN apk add sqlite

CMD ["/bin/bash"]
