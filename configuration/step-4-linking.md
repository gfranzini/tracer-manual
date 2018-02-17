# Step 4. Linking

![](/assets/architecture.png)

In the _Linking_ stage, TRACER creates links between the features defined in previous steps. Unlike other TRACER steps, which are all linear, _Linking_ is of squared complexity depending on the feature frequency and it is, therefore, the most computationally- and time-intensive task in the detection process.[^1] Through Linking TRACER will deliver results based purely on the parameters set in previous steps. It is up to us to interpret those results and filter out what is good and what is bad.

## Types of Linking

TRACER can perform two types of Linking, _Intralinking_ and _Interlinking_.

### Intralinking

_Intralinking_ looks for text reuse within the same text or work \(i.e. self-reuse\). Given _Work A_ below, TRACER will look for a sentence that repeats itself either word-for-word or non-literally in Work A. Intralinking can be used, for example, to analyse a Bible and see how one Gospel reuses another.

![](/assets/intralinking.jpeg)

### Interlinking

Interlinking looks for matches between different texts or works. Given _Work A_ and _Work B_ below, TRACER will look for a sentence that repeats itself in a different work, not in the same work. Interlinking can be used, for example, to compare different Bibles or Bible translations.

![](/assets/interlinking.jpeg)

Remember that Edition A and Edition B are actually stored in the same `.txt` file, one under the other, as described in [Corpus preparation](/corpus-preparation.md). The _Inter/Intra_ parameter can be changed in the TRACER `tracer_config.xml`:

![linking](/assets/linking.png "The value of the highlighted property in the TRACER \`tracer\_config.xml\` can be changed to \`InterCorpusLinkingImpl\`, if needed.")

TRACER outputs _Linking_ results in a `.link` file in a three column structure:

`REUSE ID 1 - REUSE ID 2 - OVERLAP`

Here’s how this structure looks like in the corresponding file:

![](/assets/linking_link.png)

What does TRACER mean by _absolute overlap_? The absolute overlap is the minimal number of common features shared by the first two columns \(REUSE ID 1 and REUSE ID 2\), which TRACER sets as default to 5. This overlap number can be changed and is used to cut the long tail of reuses which would likely not be relevantmatches or reuses at all. The `.meta` _Linking_ file will provide you with an overview of the features linked:

[^1]: A basic explanation of _squared complexity_ is available under Wikipedia's [Big O Notation](https://en.wikipedia.org/wiki/Big_O_notation) page.

