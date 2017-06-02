Experiment in creating a Docker container to provide a workbench for the "7 command-line tools for data science" by jeroen janssens, published on 19 September 2013, and available at
  http://jeroenjanssens.com/2013/09/19/seven-command-line-tools-for-data-science.html .

The prerequisite for using this repo is a working install of a Docker application.

The steps to using this container to run the exercises described on the 2013 web page are:
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

The steps to building the container on your computer from this repo are:
1. In a terminal window copy or clone the dsatclcon repository.
2. Change directory to the dsatclcon directory
3. Assuming your cursor is in the dsatclcon directory enter the following at the shell prompt:
```sh
   $ docker build -t wlanderson/dsatclwb .
```
If the build succeeds, then the container can be run using this command:
```sh
  $ docker run -i -t wlanderson/dsatclwb
```
  
The container script here is constructed and tested on an Macintosh computer running macOS Sierra running a Docker Community Edition [https://www.docker.com/community-edition].
