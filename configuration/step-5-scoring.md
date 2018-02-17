# Step 5. Scoring

![](/assets/architecture.png)

The _Scoring_ step of TRACER assigns a weight to a reuse pair based on an internal scoring metric. The resemblance score is calculated as follows:

![](/assets/scoring-formula.png)

> **\[warning\] To update**
>
> EXPLAIN FORMULA\*\*

The extension of the file in which the scores are recorded is `.score`. This file contains four columns of data, for example:

`4000237   4010258   13.0   1.0`

The first two numbers represent two aligned sentences, a sentence in _Text A_ with the ID `4000237` and its reused version in _Text B_ with the ID `4010258`. The third number is an _**absolute overlap**_, indicating that the two sentences share 13 features \(e.g. 13 words, if the user set the _Featuring_ to `WordBased`\). The fourth number is the _**weighted overlap**_ or the percentage of similarity between the two sentences - in this case, `1.0` means 100% similar, indicating that _Text B_ reused _Text A_ word-for-word \(verbatim\); a weighted overlap of `0.9` is 90%, `0.8` is 80% and so on.

The _Scoring_ section of the `tracer_config.xml` file contains three categories:

![scoring](/assets/scoring-config.png "The three Scoring implementations in TRACER.")

* `FullWordWeightedResemblanceSimilarityImp`: this class computes similarities including all words in the sentence and assigns the same weight to every word. This implementation was designed to deliver results in a human-readable way \(i.e. for GUIs\). `Full-weighted` means that the similarity score is multiplied by the feature overlap in order to convey some form of confidence; the value of this property here is no longer a scale between `0` and `1` but the weight depends on the length of the segmented unit the user chose.

* `SelectedFeatureWordClass2WeightedOverlapImpl`: with this implementation selected features are transformed into word classes, and the word classes are weighed. More weight is given to content classes \(verbs, nouns, etc.\) than to, for instance, articles.

* `SelectedFeatureResemblanceSimilarityImpl`: given selected features from a reuse pair \(_max pruning_ without function words\) this Scoring implementation compares the selected features and gives all words the same weight. The value of this property can range between `0` and `1`. If the user sets a high value, such as `0.9`, TRACER will return reuse pairs that are 90% similar \(near-verbatim\).

## _Containment_ measure for imbalanced length of reuse

If the text segmentation you used has created reuse units of very different lengths, chances are that TRACER will produce many false positives or not be able to match a string in text A against a string in text B at all \(= false negatives\). Here is an example of text reuse in Latin texts that was not identified by TRACER due to very different reuse unit lengths caused by text segmentation:

{% panel %}
TEXT A \(source text\): _**In principio creavit Deus caelum et** **terram**_**.**

TEXT B \(target text\): _ubi , cum primo dicatur , **in principio creavit deus caelum et terram** , subiungit , distinxit deus lucem a tenebris , et sic de aliis :_
{% endpanel %}

Despite the fact that Text B is quoting TEXT A word for word, the different length of the reuse unit \(that is, the sentence within which the text reuse appears\) coupled with configuration parameters set for this particular analysis eluded TRACER.

To avoid this from happening, we must change the default _Scoring_ `SelectedFeatureResemblanceSimilarityImpl` property value in `tracer_config.xml` to `SelectedFeatureContainmentSimilarityImpl`, as so:

![scoringContainment](/assets/scoring-containment.png "The default Scoring Resemblance measure in the tracer_config.xml file is commented out and replaced by the alternative Scoring Containment measure to address imbalanced reuse length.")

