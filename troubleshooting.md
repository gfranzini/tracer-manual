# Troubleshooting

This section contains a list of encountered errors with solutions. Should your TRACER error not be in this list, please report it [here](http://www.etrap.eu/redmine/projects/tracer).

> These error reports can be accessed &lt;OUT FILE&gt;

## General recommendation

Should none of the solutions in this page work for you or if you can't figure out what the error might be, the general recommendation is to always delete any existing `TRACER_DATA` folder \(which stores the results of previous analyses\) before running new analyses. Why? Because it _could be_ that existing computed files are creating conflicts with the settings you changed for a new analysis.

---

## `java.lang.NoClassDefFoundError: Xmx600m`

![](/assets/wrong-Java.png)This error appears if the version of Java installed on your computer is not the one required by TRACER, which is Java 8. To fix the error, download and install Java 8. Once installed, open the terminal and type `java -version` and press `ENTER` to check you have the correct version installed; the version number should start with a `1` and the second number should be an `8`.  If your second number is not `8`, then installation of Java 8 was not successful.

Once Java 8 is installed on your computer you can re-run TRACER.

---

## `Unparseable date: """`

![](/assets/unparseable-date.png)

This error is caused by the presence of a sequence of characters or absence of text in the **second column** of the corpus file. The term `date` is misleading and does not, in this case, indicate that the problem is with dating information \(which can be added in the third column of the corpus file\). The problem here is that TRACER does not provide information about the specific issue with the text, so the user has to check the corpus file in a text editor and correct anything that might seem incorrect or problematic. In order to fix this error, the user has to correct, save and re-run TRACER. If the error persists, then more corpus cleaning is needed.

---

## `Out of memory`

If TRACER generates an `out-of-memory` error, the problem is likely caused by the _Scoring_ threshold set in the configuration file. If the _Scoring_ threshold is too low, such as `0.1`, TRACER needs more time and memory to compute the results, as a low _Scoring_ threshold leads to a large number of results. To solve the issue, increase the memory value contained in the TRACER execution command from `Xmx600m` \(600 MB of memory\) to, for example, `Xmx1g` \(1 GB of memory\).

---

## Empty `.score` and/or `.link` files \(0KB\)

It might happen that TRACER runs a detection successfully but produces empty `.link` and `.score` files. There are two potential reasons for this:

1. You might have the wrong value in the _Linking_ implementation property: `INTER` instead of `INTRA` corpus linking:

`<property name="LINKING_IMPL" value="eu .etrap.tracer.linking.IntraCorpusLinkingImpl "/>`

1. Your ID numbering might be incorrect. Again, in the _Linking_ section of the configuration file, you’ll notice the following property:

`<property name="intWorkNumbering " value ="1000000" />`

The value is set to a 7-digit ID. This means that your IDs should be 7-digits long. If you would rather work with shorter digits, you must change this value in the configuration file accordingly. If possible, please avoid using IDs above 2.000.000, as these require extra steps in order to be processed.

---





