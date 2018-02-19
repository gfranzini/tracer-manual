# Error: Unable to access jarfile tracer.jar

When compiling TRACER with Apache Ant, it is important you use the command `ant` \*only\* and not `ant verbose` or other Ant commands. Although using `ant verbose` or similar will produce a successful build of TRACER, the execution of TRACER after this build will return the following error:

```
C:\Users\*anonymous*\Downloads\tracer>java -Xmx600m -Deu.etrap.medusa.config.ClassConfig=conf/tracer_config.xml -jar tracer.jar

Error: Unable to access jarfile tracer.jar
```

This is because the `tracer.jar` file generated from the Ant build is not complete \(it should be some 33MB in size\).





