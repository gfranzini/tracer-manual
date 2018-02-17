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

![linking](/assets/linking.png "The value of the highlighted property in the TRACER tracer\_config.xml can be changed to InterCorpusLinkingImpl, if needed.")

TRACER outputs _Linking_ results in a `.link` file in a three column structure:

`REUSE ID 1 - REUSE ID 2 - OVERLAP`

Here’s how this structure looks like in the corresponding file:

![linking-link](/assets/linking_link.png "The three-column structure in the Linking output file of the King James Version Bible text: REUSE ID 1 - REUSE ID 2 - ABSOLUTE OVERLAP.")

What does TRACER mean by _absolute overlap_? The absolute overlap is the minimal number of common features shared by the first two columns \(`REUSE ID 1` and `REUSE ID 2`\), which TRACER sets as default to `5`.[^2] This overlap number can be changed and is used to cut the long tail of reuses which would likely not be relevantmatches or reuses at all. The `.meta` _Linking_ file will provide you with an overview of the features linked:

![linking-meta](/assets/linking_meta.png "Overview of Linking results provided by the Linking .meta file.")

_Linking_ is the most time-consuming step and the step that can be best parallelised, as shown in the chart below.

![linking-chart](/assets/linking_parallel.png "Overview of the Linking step. TRACER mostly deals with Local Linking but, if necessary, can also support Distributed Linking.")

## Moving Window Linking Implementation for short reuse

The two types of _Linking_ implementation described above work well when linking text reuse units \(e.g. sentences\) of a similar size and for detecting close reuse or rewording \(i.e. where the reuse covers roughly more than 50% of the unit\). One example of where we could use these implementations is the Bible: we could, for instance, compare Mark with Luke. The reuse units, the verses, are similar in length and our knowledge of the Bible tells us that Luke copied from Mark. If, however, you’re looking for paraphrase or allusions, or if the reuse covers less than 50% of the unit, these two implementations will not perform well. That is not to say that you can’t use them. But if you do, you must lower the similarity thresholds in the `tracer_config.xml` file, and by doing so TRACER will contaminate your results with many false positives.  
For these cases, TRACER provides another _Linking_ implementation, the _Moving Window_. This approach is well-suited, if not necessary, for the detection of very small reuse; for example, to detect a four-word overlap in two sentences \(as reuse units\) of 20 and 25 words each. If we set a Moving Window of, for example, 10 words, TRACER will read the reuse unit 10 words at a time with a one-word overlap, as shown in the Latin example below:

![moving-window](/assets/moving-window-10.png "The reuse unit 100000801 is divided into 10-word chunks. The first chunk on the first line begins with the words PATRIS TUERETUR, AB OFFENSO, the second chunk on the second line skips PATRIS and begins with TUERETUR, the third chunk on the third line skips PATRIS TUERETUR and begins with AB, and so on and so forth.")

If you don’t know your data well and would like TRACER to give you a rough idea of the degree of similarity between two or multiple texts, the recommendation is to first run a detection task _without_ the Moving Window implementation in order to detect the closestmatches. Use the Moving Window only if the result-set or recall from this first analysis is too low and/or if you’d like to find smaller reuse.

To use the `MovingWindowimplementation`, you first need to segmentise your reuse units into windows. We recommend you try with windows of 10 or 15 words as these should detect most reuses. But you may, of course, run more than one detection with bigger or smaller window sizes and compare the results!  
First, ensure your corpus `.txt` file is in TRACER’s `corpora` folder. Then, in the terminal, navigate to TRACER’s main folder and type this command:

`java -cp tracer.jar eu.etrap.tracer.preprocessing.MovingAverageSegmentizerMain data/corpora/YourCorpus/yourcorpus.txt 15`

Where the `data/...yourcorpus.txt` path points to the location of your text in TRACER’s data folder and `15` tells TRACER to split reuse units into windows of 15 words. Press `ENTER` and wait a few seconds for TRACER to compute the result. This command creates a version of the `yourcorpus.txt` where reuse units are formatted into 15-word windows. This file version is automatically named `yourcorpus-W15.txt` and saved in the TRACER `corpora` folder. If you want to break the text into windows of 10 words, change the final `15` to `10` in the java command.

Next, you need to make some changes in TRACER’s configuration file. First, make sure that the `SENTENCE_FILE_NAME` property points to your new `yourcorpus-W15.txt` file \(as described in [Corpus preparation](/corpus-preparation.md)\). Next, locate the _Linking_ property in the `tracer_config.xml` file and ensure you have the right class, `MovingWindowInterCorpusLinking` or `MovingWindowIntraCorpusLinking` \(depending on whether you want to run _Inter-_ or _Intracorpus_ linking\):

![moving-window-config](/assets/moving-window-config.png "The class of the LINKING\_IMPL property in TRACER’s configuration file should read MovingWindowInterCorpusLinking or MovingWindowIntraCorpusLinking, depending on the type of Linking you’re interested in.")

Next, define the length of your Window in the _Linking_ category of the `tracer_config.xml` file, in the `intWindowSize` property:

![moving-window-size](/assets/moving-window-size-config.png "Define the size of your Moving Window in the value attribute of the intWindowSize property of the Linking category. In this case, we define a Window of 15 words.")

The value of the `intWindowSize` property mustmatch the window size you defined in the previous java command.

Save the changes and run TRACER!

## Containment measure for imbalanced length of reuse

If the text segmentation you used has created reuse units of very different lengths, chances are that TRACER will produce many false positives or not be able to match a string in text A against a string in text B at all \(= false negatives\). Here is an example of text reuse in Latin texts that was not identified by TRACER due to very different reuse unit lengths caused by text segmentation:

TEXT A \(source text\): _**In principio creavit Deus caelum et** **terram**_**.**

TEXT B \(target text\): _ubi , cum primo dicatur , **in principio creavit deus caelum et terram** , subiungit , distinxit deus lucem a tenebris , et sic de aliis :_

Despite the fact that Text B is quoting TEXT A word for word, the different length of the reuse unit \(that is, the sentence within which the text reuse appears\) coupled with configuration parameters set for this particular analysis eluded TRACER. 

To avoid this from happening, we must change the default _Scoring_ `SelectedFeatureResemblanceSimilarityImpl` property value in `tracer_config.xml` to `SelectedFeatureContainmentSimilarityImpl , as so:`![](/assets/scoring-containment.png)







 

 

[^1]: A basic explanation of _squared complexity_ is available under Wikipedia's [Big O Notation](https://en.wikipedia.org/wiki/Big_O_notation) page.

[^2]: The overlap is computed based on the preprocessing and selected features.

