Install
-------

* Clone this repository and do 'mvn install'.
* Download CTakes binaries.
* Copy CTAKES_HOME/resources to root (working) dir
* Optionally, copy CTAKES_HOME/desc to root (working) dir


Running Server
--------------

You can also start a simple REST Server with the following command:
```
#start server with ctakes desc xml. Default is "desc/ctakes-clinical-pipeline/desc/analysis_engine/AggregatePlaintextFastUMLSProcessor.xml", assuming that desc is in you working directory.
mvn scala:run -DmainClass=de.dfki.lt.ctakes.Server -DaddArgs="url(e.g.:localhost)|port(e.g. 9999)|[optional:path/to/desc]"
```
You can then use the REST service via GET requests with parameters "text". E.g., in browser:
```
http://localhost:9999/ctakes?text=Pain in the left leg.
```