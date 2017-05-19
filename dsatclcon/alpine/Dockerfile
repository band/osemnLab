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
    py-pip \
    build-base
RUN pip install --upgrade pip
RUN pip install csvkit
RUN apk add sqlite

# install Tool4 (scrape) and Tool6 (sample) (from JJ's tool set)
RUN cd /tmp && git clone https://github.com/jeroenjanssens/data-science-at-the-command-line.git
RUN cd /tmp/data-science-at-the-command-line/tools && cp -v scrape sample /usr/local/bin
# Tool4 (scrape) requires two python modules
RUN apk add libxml2-dev libxslt-dev
RUN pip install lxml && pip install cssselect

# install Tool5 (xml2json)
RUN apk add nodejs nodejs-npm && \
	npm install npm@latest -g
RUN echo node: $(node -v) && echo npm: $(npm -v)
RUN npm install -g xml2json-command

CMD ["/bin/bash"]
