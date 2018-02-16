# Step 2. Featuring/Training

![](/assets/architecture.png)

Now that we’ve preprocessed the text, we can proceed to breaking it down into units or _features_ that can be compared \(e.g. words, bigrams, trigrams\). For this reason, this step is known as _Featuring_ or _Training_. The chart below provides an overview of _Featuring_. TRACER can perform two types of featuring, _Syntactic_ and _Semantic_. _Syntactic_ dependency parsing is not always accurate because parsers \(and the TRACER parser\) are not yet able to infer dependencies. But if TRACER takes manually annotated data from treebanks, for example, then the parser would be able to produce usable results.

> \*\*\[danger\] Explain SEMANTIC DEPENDENCY PARSING\*\*

![featuring](/assets/featuring-overview.png "Overview of Featuring.")

As you can see, there exists also a third type of _Featuring_ implementation, _Non-statistic Approaches_. These aren’t part of TRACER. Among these, _Verba dicendi_ featuring could be used for fragmentary texts but it’s not a stable feature; _Surface Features_, for example quotation marks, are also an unstable feature as they don’t always occur in historical texts; for _Canonical References_, please consult the research of [Dr Matteo Romanello](https://www.researchgate.net/profile/Matteo_Romanello); for _Signal Processing_ see [Seo and Croft \(2008\)](/references.md).

## Features

TRACER supports 10 different features or featuring units, from words as features to 10-gram features. Generally, features of 3-4 grams are sufficient for text reuse analyses. The _n_ in 'n-gram' could be a character or a word.

* **Word-based featuring**: good for paraphrase detection. With this type of featuring one should also lemmatise and activate synonym replacement.
* **Bigram featuring**: good to detect verbatim and near-verbatim text reuse. Lemmatisation and synonym replacement with this N-gram approach might not work or be necessary.
* **Trigram featuring**: good to detect verbatim and near-verbatim text reuse. Lemmatisation and synonym replacement with this N-gram approach might not work or be necessary.

### Feature density

The _Selection_ step in TRACER asks users to define a _Feature density_ for every detection task. By default TRACER sets the feature density to 0.5 \(=50%\), meaning that it will return only reuse pairs that are at least 50% similar or \(share 50% of their features\). For more information about Feature density, see [Step 3. Selection](/configuration/step-3-selection.md).

## Types of Featuring

### Overlapping

### Non-overlapping

### Shingling or hash-breaking?

#### Hash-breaking

#### Shingling

Both bigram and trigram shingling work to detect the example reuse above in strings 1 and 2. It doesn’t matter what method we use. What changes, however, is _performance_.

## Customising parameters or _properties_



