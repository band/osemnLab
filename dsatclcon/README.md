Experiment in creating a Docker container to provide a workbench for the "7 command-line tools for data science" by jeroen janssens, published on 19 September 2013, and available at
  http://jeroenjanssens.com/2013/09/19/seven-command-line-tools-for-data-science.html .

The prerequisite for using this repo is a working install of a Docker application. The container script here is constructed and tested on an Macintosh computer running macOS Sierra running a Docker Community Edition. [NEED TO ADD URL]

The steps to using this repo to run the exercises described on the 2013 web page are
1. Copy or clone the dsatclcon repository.
2. In a terminal window move to the dsatclcon directory
3. Assuming your cursor is in the dsatclcon directory enter the following at the command prompt:
```sh
   $ docker build -t wlanderson/dsatclex .
   $ docker run -i -t wlanderson/dsatclex /bin/bash
```
4. This leaves you at a root login command prompt "#".
5. From here you can type in commands to work with the specified command-line tools.

