Open Data Portals Collaboration and Relatedness Analysis Service
=====================
...



mongodb installation [one time only]
------------------------------------

https://docs.mongodb.com/master/administration/install-community/


Spotlight Installation [one time only]
--------------------------------
 .......


Service installation [one time only]
--------------------
```
$ virtualenv venv

$ source venv/bin/activate

$ pip install -r requirements.txt
```

Service configuration
--------------------

config.py [setting Stanford NER credinalities]







Running the service:
--------------------

[1] Start mongod
```
$ sudo mongod start
```
[2] Start Spotlight:
```
$ cd ~/spotlight

$ java -Xmx5G -Xms5G -jar dbpedia-spotlight-latest.jar en http://localhost:2222/rest
```
[3] Start collecting and analyzing a givin CKAN portal data) FULL PIPELINE:
```
$ python collect-Network-components.py 'http://data.gov.ie' 'localhost' 27017 'rtpa' 'datasetIDS' 'rtpaF' 0 True
```
arg 1: open data portal (ckan) ex: http://data.gov.ie

arg 2: mongodb host ex: localhost

arg 3: mongodb port ex: 27017 (int)

arg 4: database name ex: rtpa

arg 5: collection name to store dataset ids ex: datasetIDS

arg 6: colection name to store dataset catalogues and related analysis data ex: rtpaF

arg 7: (Optional) start from index in case collection was interupted ex: 2000, default is 0 (int)

arg 8: (Optional) Run Named Entity Recognition process or not ex: True, default False

arg 9: (Optional) Build Network or not ex: net, By default it will not run unless requested


[4] Start websevice and visulization:
```
$ python rtpa-publisher-network-builder.py
```



Last Update
------------
16 August 2017