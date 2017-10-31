# Troubleshooting

This section contains a list of encountered errors with solutions. Should your TRACER error not be in this list, please report it [here](http://www.etrap.eu/redmine/projects/tracer).

---

## `java.lang.NoClassDefFoundError: Xmx600m`

![](/assets/wrong-Java.png)This error appears if the version of Java installed on your computer is not the one required by TRACER, which is Java 8. To fix the error, download and install Java 8. Once installed, open the terminal and type `java -version` and press `ENTER` to check you have the correct version installed; the version number should start with a `1` and the second number should be an `8`.  If your second number is not `8`, then installation of Java 8 was not successful.

Once Java 8 is installed on your computer you can re-run TRACER.

---

## `Unparseable date: """`

![](/assets/unparseable-date.png)

> SOLUTION NOT AVAILABLE YET

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

