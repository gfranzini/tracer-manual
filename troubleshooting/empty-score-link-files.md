# Empty `.score` and/or `.link` files \(0KB\)

It might happen that TRACER runs a detection successfully but produces empty `.link` and `.score` files. There are two potential reasons for this:

1. You might have the wrong value in the _Linking_ implementation property: `INTER` instead of `INTRA` corpus linking:

`<property name="LINKING_IMPL" value="eu .etrap.tracer.linking.IntraCorpusLinkingImpl "/>`

1. Your ID numbering might be incorrect. Again, in the _Linking_ section of the configuration file, you’ll notice the following property:

`<property name="intWorkNumbering " value ="1000000" />`

The value is set to a 7-digit ID. This means that your IDs should be 7-digits long. If you would rather work with shorter digits, you must change this value in the configuration file accordingly. If possible, please avoid using IDs above 2.000.000, as these require extra steps in order to be processed.