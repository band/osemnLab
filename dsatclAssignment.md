# Data Science at the command line. Introductory exercises.
### iSchool, UTexas at Austin, S17INF382R: Data Science Informatics
2017-04-16, William L. Anderson

These exercises are taken directly from a 2013 internet post by Jeroen
Janssens entitled "7 command-line tools for data science".
(http://jeroenjanssens.com/2013/09/19/seven-command-line-tools-for-data-science.html)
The material in this website was incorporated in an expanded 2014 book titled
"Data Science at the Command Line" (http://datascienceatthecommandline.com/).

The notes below reflect changes to the commands in the 2013 internet post so that they can be executed on a Ubuntu 16.04.2 LTS virtual machine. All required tools and dependencies are installed on the VM.

##### The Assignment:
Execute the commands on the webpage and make notes of your observations (what did you notice?), your results, and any thoughts you may have regarding the exercise. Submit your notes as a text file.


Suggestion: create a directory in which to do your work (mine is ~/local/osemn).


## Tool 1. jq - sed for JSON

- The json data does not need to be downloaded from NYT. The API has changed and the URL for this example may not work.
     
- Data files in json format are available in /usr/local/opt/dsatcl.
     Suggestion: copy the json file to your working directory.

## Tool 2. json2cvs
- The webpage expects the file 'million.json' to be captured from the last example. If you have some difficulty with this step this file can also be copied to your working directory from
     /usr/local/opt/dsatcl/million.json
     
## Tool 3. cvskit
- The webpage expects the file 'million.csv' to be captured
     from the previous Tool 2 example. If you need it, this file is
     also available in /usr/local/opt/dsatcl/. (Again, it is best to
     copy it to your working directory.)

- Note: To exit from sqlite3 shell use .quit or .q .

- Use 'csvjson' to convert million-header.csv back to json, and then pass it through "jq '.'"  for pretty-printing.

## Tool 4. scrape - HTML extraction
- Replace webpage command with this one:
```sh
$ curl -s 'http://en.wikipedia.org/wiki/List_of_countries_and_territories_by_border/area_ratio' | scrape -b -e 'table.wikitable > tr:not(:first-child)' | more
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

- The third Rio command works, however it seems the only way to view the image is to login to the server with an X11 xterm. Then simple image viewers (like gpicview) can render the image in another window.
