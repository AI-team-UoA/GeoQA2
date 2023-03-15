# GeoQAV2 (Template-Based Geospatial Question Answering)

GeoQAV2 is an end-to-end geospatial QA system which answers questions over the knowledge graph [YAGO2geo](https://yago2geo.di.uoa.gr/). GeoQAV2 is built using reusable components as part of the component-oriented [Qanary](https://github.com/WDAqua/Qanary/) question answering methodology.

## Prerequisites:
1. Java 11
2. [Maven](https://maven.apache.org)
3. [Stardog Triplestore](http://stardog.com/), version 7.5.0

## Setup GeoQAV2

1. Create a Stardog database named `qanary`. All the triples generated by the components will be stored in this database.
2. Clone the code: `git clone https://github.com/dharmenpunjani/GeoQAV2`
3. Compile, test and package: `mvn clean install -Ddockerfile.skip=true`

## Run GeoQAV2

Qanary is a component-based framework for building QA systems. After compilation finishes, `.jar` files will have been generated in the corresponding folders of the Qanary components. To enable a component you need enter its target directory and execute the corresponding `.jar` file.

1. Enter the root of the codebase.
2. Run the pipeline component: `java -jar qanary_pipeline-template/target/qa.pipeline-{COMPONENT_VERSION}.jar`
3. Run any components you are interested in, for example: `java -jar qanary_component-TagMeDisambiguateYago/target/qanary_component-TagMeDisambiguate-{COMPONENT_VERSION}.jar`

After running corresponding components, you can see a Springboot application running on http://localhost:12345/#/overview that shows the status of currently running components. The port 12345 can be set to any other port of your choice in the `application.properties` file.

You should run the following components to use complete pipeline:
- qanary_pipeline-template
- qanary_component-TagMeDisambiguateYago
- qanary_component-ConceptIdentifierYago
- qanary_component-PropertyIdentifierYago
- qanary_component-RelationDetection
- qanary_component-GeoSparqlGenerator

Now your pipeline is ready to use. Go to http://localhost:12345/startquestionansweringwithtextquestion. Here you can find a User Interface to interact for asking questions via web interface, and then select the components you need to include in the pipeline via checking a checkbox for each component. Press the start button and you are ready to go!


An endpoint containing data can be found at http://pyravlos2.di.uoa.gr:8080/yago2geo/