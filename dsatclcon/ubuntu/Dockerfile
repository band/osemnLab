# base image
FROM ubuntu:latest
# update: latest package indexes needed for software installs
RUN apt-get -y update && apt-get install -y \
    curl \
    git \
    jq \
    python-pip \
    sqlite3 \
    software-properties-common \
    && rm -fr /var/lib/apt/lists/*

# install Tool1: jq (sed for jSON)
# copy files needed for the Tool1 exercise
COPY nyt.json /usr/local/opt/dsatcl/nyt.json

# install Tool2: json2csv (convert JSON to CSV)
RUN cd /tmp && curl -L https://github.com/jehiah/json2csv/releases/download/v.1.2.0/json2csv-1.2.0.linux-amd64.go1.8.tar.gz | tar -zx
RUN cp -v /tmp/json2csv-1.2.0.linux-amd64.go1.8/json2csv /usr/local/bin

# install Tool3: csvkit
RUN pip install --upgrade pip
RUN pip install csvkit

# install Tool4 (scrape), Tool6 (sample), Tool7 (Rio) (from JJ's tool set)
RUN cd /tmp && git clone https://github.com/jeroenjanssens/data-science-at-the-command-line.git
RUN cd /tmp/data-science-at-the-command-line/tools && cp -v scrape sample /usr/local/bin
# Tool4 (scrape) requires two python modules
RUN pip install lxml && pip install cssselect

# install Tool5: xml2json
RUN curl -sL https://deb.nodesource.com/setup_6.x | bash - && \
	apt-get update && apt-get install -y nodejs && \
	npm install npm@latest -g
Run echo node: $(node -v) && echo npm: $(npm -v)
RUN npm install -g xml2json-command

# install Tool 7 (Rio): requires R and some R packages
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
RUN add-apt-repository 'deb [arch=amd64,i386] http://cran.rstudio.com/bin/linux/ubuntu xenial/'
RUN apt-get -y update && apt-get install -y r-base \
    && rm -fr /var/lib/apt/lists/*

RUN R -e "install.packages('dplyr',repos='http://cran.revolutionanalytics.com')"
RUN R -e "install.packages('tidyr',repos='http://cran.revolutionanalytics.com')"
RUN R -e "install.packages('sqldf',repos='http://cran.revolutionanalytics.com')"
RUN R -e "install.packages('ggplot2',repos='http://cran.revolutionanalytics.com')"

# execute this command when the container is run
#  i.e., start up in a bash shell
COPY bashinit.sh /root/
CMD ["/bin/bash","--init-file","/root/bashinit.sh"]
