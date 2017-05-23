FROM alpine:edge
LABEL maintainer "William L Anderson <band@acm.org>"

ENV WORKBENCH_PACKAGES bash curl git jq sqlite
ENV INSTALL_PACKAGES python python-dev py-pip build-base libxml2-dev libxslt-dev

RUN apk add --update --no-cache $WORKBENCH_PACKAGES && \
    rm -fr /var/cache/apk/*

# install Tool1 (jq) data file
COPY nyt.json /usr/local/opt/dsatcl/nyt.json

# install Tool2: json2csv (convert JSON to CSV)
RUN cd /tmp && \
    curl -L https://github.com/jehiah/json2csv/releases/download/v.1.2.0/json2csv-1.2.0.linux-amd64.go1.8.tar.gz | tar -zx && \
    cp -v /tmp/json2csv-1.2.0.linux-amd64.go1.8/json2csv /usr/local/bin

# install Tool3 (csvkit)
RUN apk add --update --no-cache python \
    python-dev \
    py-pip \
    build-base && \
    pip install --upgrade pip && \
    pip install csvkit && \
    rm -fr /var/cache/apk/*

CMD ["/bin/bash"]
