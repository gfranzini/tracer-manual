# Troubleshooting

This section contains a list of encountered errors with solutions. Should your TRACER error not be in this list, please report it [here](http://www.etrap.eu/redmine/projects/tracer).

As [previously mentioned](/execution-of-tracer.md), the `.out` file produced by TRACER when executed documents the detection process. Should a detection task fail, this file will show users where the process stopped allowing them to more easily locate the source of the error. This _Troubleshooting_ page was set-up because the error messages in the `.out` file are not always intuitive for users who are not familiar with Java.


> ant javadoc
>
> Once it runs through, you find in doc/javadoc the Javadocs with ALL classes. Just open the index.html in your LOCAL browser. There you find all available classes in their packages.


## General recommendation

Should none of the solutions in this page work for you or if you can't figure out what the error might be, the general recommendation is to always delete any existing `TRACER_DATA` folder \(which stores the results of previous analyses\) before running new analyses. Why? Because it _could be_ that existing computed files are creating conflicts with the settings you changed for a new analysis.