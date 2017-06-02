Experiment in creating a Docker container to provide a workbench for the "7 command-line tools for data science" by jeroen janssens, published on 19 September 2013, and available at
  http://jeroenjanssens.com/2013/09/19/seven-command-line-tools-for-data-science.html .

The prerequisite for using this repo is a working install of a Docker application. The container script here is constructed and tested on an Macintosh computer running macOS Sierra running a Docker Community Edition. [NEED TO ADD URL]

The steps to using this container to run the exercises described on the 2013 web page are
1. In a terminal window carry out the following commands
```sh
  $ mkdir ~/workbench
  $ cd ~/workbench
```
2. Assuming your cursor is in the working directory enter the following at the command prompt:
```sh
   $ docker pull wlanderson/dsatclwb
   $ docker run -i -t wlanderson/dsatclwb
```
3. This leaves you at a root login command prompt "#".

4. From here you can type in commands to work with the specified command-line tools.

