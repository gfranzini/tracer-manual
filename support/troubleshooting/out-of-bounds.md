# Out of bounds exception

Here is another error reported by a TRACER user \(line Z\).

 `START TO PROCESS LEVEL 1 (PRE-PROCESSING)`

```
Preprocessing baseform graph in data/corpora/LLCT2/LLCT2.lemma ... Total number of loaded word forms is 749 eu.etrap.tracer.TracerException: java.lang.ArrayIndexOutOfBoundsException: 1 at eu.etrap.tracer.preprocessing.graph.AbstractWordGraphHandler.loadInputFile(AbstractWordGraphHandler.java:136) at eu.etrap.tracer.preprocessing.graph.BaseFormWordGraphPreprocessingImpl.preprocessing(BaseFormWordGraphPreprocessingImpl.java:48) at eu.etrap.tracer.preprocessing.WordGraphPreparer.prepareBaseformGraph(WordGraphPreparer.java:107) at eu.etrap.tracer.preprocessing.WordGraphPreparer.prepare(WordGraphPreparer.java:70) at eu.etrap.tracer.AbstractTracerFrameWork.process(AbstractTracerFrameWork.java:151) at eu.etrap.tracer.Tracer.process(Tracer.java:56) at eu.etrap.tracer.Tracer.main(Tracer.java:69) Caused by: java.lang.ArrayIndexOutOfBoundsException: 1 at eu.etrap.tracer.preprocessing.graph.AbstractWordGraphHandler.loadInputFile(AbstractWordGraphHandler.java:113) ... 6 more Message: java.lang.ArrayIndexOutOfBoundsException: 1
```

As this error message indicates in line X, the source of the problem is the `.lemma` file. In this particular use case, five entries in the file were missing one of three columns of data required. Adding the missing information in the third column fixed the issue.

