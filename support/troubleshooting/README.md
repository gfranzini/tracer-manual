# Troubleshooting

This section contains a list of encountered errors with solutions. Should your TRACER error not be in this list, please report it [here](http://www.etrap.eu/redmine/projects/tracer).

As [previously mentioned](../../manual/execution-of-tracer.md), the `.out` file produced by TRACER when executed documents the detection process. Should a detection task fail, the `.out` file will show users where the process stopped allowing them to more easily locate the source of the error. Users familiar with Java may wish to consult TRACER's Javadoc to help locate errors. To do so, navigate to your TRACER folder in the terminal and type `ant javadoc`. Open the generated `index.html` file in a browser to see all TRACER classes and packages.

**This** _**Troubleshooting**_ **section lists errors encountered by users and their respective solutions**.

## General recommendation

Should none of the solutions in this page work for you or if you can't figure out what the error might be, the general recommendation is to always delete any existing `TRACER_DATA` folder \(which stores the results of previous analyses\) before running new analyses. Why? Because it _could be_ that existing computed files are creating conflicts with the settings you changed for a new analysis.

