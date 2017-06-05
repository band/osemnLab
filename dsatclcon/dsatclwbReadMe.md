# Data Science at the command line. Introductory exercises.
2017-06-05, William L. Anderson

The goal of this container is to provide a terminal command line prompt that enables someone to reproduce most of the examples provided in a 2013 internet post by Jeroen Janssens entitled ["7 command-line tools for data science"](http://jeroenjanssens.com/2013/09/19/seven-command-line-tools-for-data-science.html). The material in this website post was incorporated in an expanded 2014 book titled ["Data Science at the Command Line"](http://datascienceatthecommandline.com/).

Once finished with the exercises the container can be thrown away. Further experiments can be tried with the tools, but additional system and software packages may need to be installed. This particular container is provisioned to support the examples as shown in Janssens post. All required tools and dependencies are installed in the container.

### Notes

These notes reflect changes to the commands in Janssens 2013 post so that they can be executed in this container. 

Running this container will position you in the "/" directory as user
"root" at a command line prompt "bash-4.3# "
Suggestion: create a directory in which to do your work (e.g., ~/workbench):
```sh
bash-4.3# mkdir ~/workbench && cd ~/workbench
```

## Tool 1. jq - sed for JSON
- The json data does not need to be downloaded from NYT. The API has changed and the URL for this example may not work.
     
- Data files in json format are available in /usr/local/opt/dsatcl/ .
     Suggestion: copy the json file nyt.json to your working directory; e.g.
```sh
bash-4.3# cp /usr/local/opt/dsatcl/nyt.json .
```

## Tool 2. json2cvs
- The webpage expects the file 'million.json' to be captured from the last Tool 1 example.
     
## Tool 3. cvskit
- The webpage expects the file 'million.csv' to be captured
     from the previous Tool 2 example.

- Note: To exit from sqlite3 shell use .quit or .q .

- Use 'csvjson' to convert million-header.csv back to json, and then pass it through "jq '.'"  for pretty-printing.

## Tool 4. scrape - HTML extraction
- Replace webpage command with this one:
```sh
$ curl -s 'https://en.wikipedia.org/wiki/List_of_countries_and_territories_by_border/area_ratio' | scrape -b -e 'table.wikitable > tr:not(:first-child)' | more
```
- Notice changes: (1) "http://" replaced by "https://".  (2) "head" replaced by "more" ("head" yields a output error).

## Tool 5. xml2json
- Replace "http://" with "https://" in webpage command.

## Tool 6. sample
Works just as advertised. No surprises. The delay is noticeable.

## Tool 7. Rio - adding R tools to the pipeline
Replace the first curl command with this one:
```sh
$ curl -s 'https://raw.githubusercontent.com/pydata/pandas/master/pandas/tests/data/iris.csv' > iris.csv
```
[Note: the URL for raw github content has changed.]

- The first Rio command works but now yields a different output.

- The second Rio command output is similar to what is shown.

- The third Rio command works, however the current container does not provide
  a way to view the resultant ".png" file.
