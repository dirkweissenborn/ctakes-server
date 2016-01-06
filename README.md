Install
-------

* Clone this repository and do 'mvn package'.
* Download CTakes resources.


Running Server
--------------

You can also start a simple REST Server with the following command (assuming you are in root dir):
```
java -Xmx5g -cp target/ctakes-server-0.1.jar:/path/to/ctakes/resources/ de.dfki.lt.ctakes.Server host(e.g. localhost) port(e.g. 9999) /path/to/desc.xml
```
You can then use the REST service via GET requests with parameters "text". E.g., in browser:
```
http://localhost:9999/ctakes?text=Pain in the left leg.
```