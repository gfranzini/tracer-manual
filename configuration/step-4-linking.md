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

**Remember** that Edition A and Edition B are actually stored in the same `.txt` file, one under the other, as described in [Corpus preparation](/corpus-preparation.md). The _Inter/Intra_ parameter can be changed in the TRACER `tracer_config.xml`:

![linking](/assets/linking.png "The value of the highlighted property in the TRACER \`tracer\_config.xml\` can be changed to \`InterCorpusLinkingImpl\`, if needed.")

TRACER outputs _Linking_ results in a `.link` file in a three column structure:

`REUSE ID 1 - REUSE ID 2 - OVERLAP`

Here’s how this structure looks like in the corresponding file:

![linking-link](/assets/linking_link.png "The three-column structure in the Linking output file of the King James Version Bible text: \`REUSE ID 1 - REUSE ID 2 - ABSOLUTE OVERLAP\`.")

What does TRACER mean by _absolute overlap_? The absolute overlap is the minimal number of common features shared by the first two columns \(`REUSE ID 1` and `REUSE ID 2`\), which TRACER sets as default to `5`.[^2] This overlap number can be changed and is used to cut the long tail of reuses which would likely not be relevantmatches or reuses at all. The `.meta` _Linking_ file will provide you with an overview of the features linked:

![linking-meta](/assets/linking_meta.png "Overview of Linking results provided by the Linking \`.meta\` file.")

_Linking_ is the most time-consuming step and the step that can be best parallelised, as shown in the chart below.

![linking-chart](/assets/linking_parallel.png "Overview of the Linking step. TRACER mostly deals with Local Linking but, if necessary, can also support Distributed Linking.")

## Moving Window Linking Implementation for short reuse

The two types of Linking implementation described above work well when linking text reuse units
(e.g. sentences) of a similar size and for detecting close reuse or rewording (i.e. where the reuse covers
roughly more than 50% of the unit). One example of where we could use these implementations is
the Bible: we could, for instance, compareMark with Luke. The reuse units, the verses, are similar in
length and our knowledge of the Bible tells us that Luke copied fromMark. If, however, you’re looking
for paraphrase or allusions, or if the reuse covers less than 50% of the unit, these two implementations
will not perform well. That is not to say that you can’t use them. But if you do, you must lower the
similarity thresholds in the tracer_config.xml file, and by doing so TRACER will contaminate
your results with many false positives.
For these cases, TRACER provides another Linking implementation, the Moving Window. This approach
is well-suited, if not necessary, for the detection of very small reuse; for example, to detect
a four-word overlap in two sentences (as reuse units) of 20 and 25 words each. If we set a Moving
Window of, for example, 10 words, TRACER will read the reuse unit 10 words at a time with a one-word
overlap, as shown in the Latin example below:






## Containment measure for imbalanced length of reuse



[^1]: A basic explanation of _squared complexity_ is available under Wikipedia's [Big O Notation](https://en.wikipedia.org/wiki/Big_O_notation) page.

[^2]: The overlap is computed based on the preprocessing and selected features.

