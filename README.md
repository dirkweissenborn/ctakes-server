# Install #

* Download CTakes (e.g., follow ctakes user installation) to CTAKES_HOME.
* Clone this repository, cd into it and run 'mvn package'.
* To set up necessary resources, run the following:

```bash
ln -s $CTAKES_HOME/resources resources 
ln -s $CTAKES_HOME/desc desc 
```


# Running Server #

You can also start a simple REST Server with the following command (assuming you are in root dir):
```bash
java -Dctakes.umlsuser=<YOUR_UMLS_ID_HERE> -Dctakes.umlspw=<YOUR_UMLS_PASSSWORD_HERE> -Xmx5g -cp target/ctakes-server-0.1.jar:resources/ de.dfki.lt.ctakes.Server host(e.g. localhost) port(e.g. 9999) desc/path/to/desc.xml
```
You can then use the REST service via GET requests with parameters "text". E.g., in browser:
```bash
http://localhost:9999/ctakes?text=Pain in the left leg.
```

# YTex Install Notes #

* Follow YTex installation on [ctakes website](https://cwiki.apache.org/confluence/display/CTAKES/YTEX+Installation)
    * you do not need to care about optional installation steps
* requires Java-7

## Recommendations ##
* use desc/ctakes-ytex-uima/desc/analysis_engine/AggregatePlaintextUMLSProcessor.xml
* comment assertion-node, because it requires a different scala version and is therefore not supported: 
```xml
<!--node>AssertionAnnotator</node-->
```
* exchange DictionaryLookupAnnotatorDB location to the following (because it works better):
```xml
<delegateAnalysisEngine key="DictionaryLookupAnnotatorDB"> 
    <!--import location="./DictionaryLookupAnnotator.xml" /--> 
    <import location="../../../ctakes-dictionary-lookup-fast/desc/analysis_engine/UmlsLookupAnnotator.xml"/> 
</delegateAnalysisEngine>
```