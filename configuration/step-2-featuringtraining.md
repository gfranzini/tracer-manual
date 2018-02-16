# Step 2. Featuring/Training

![](/assets/architecture.png)

Now that we’ve preprocessed the text, we can proceed to breaking it down into units or _features_ that can be compared \(e.g. words, bigrams, trigrams\). For this reason, this step is known as _Featuring_ or _Training_. The chart below provides an overview of _Featuring_. TRACER can perform two types of featuring, _Syntactic_ and _Semantic_. _Syntactic_ dependency parsing is not always accurate because parsers \(and the TRACER parser\) are not yet able to infer dependencies. But if TRACER takes manually annotated data from treebanks, for example, then the parser would be able to produce usable results.

> \*\*\[danger\] Explain SEMANTIC DEPENDENCY PARSING\*\*

![featuring](/assets/featuring-overview.png "Overview of Featuring.")

As you can see, there exists also a third type of Featuring implementation, Non-statistic Approaches. These aren’t part of TRACER. Among these, Verba dicendi featuring could be used for fragmentary texts but it’s not a stable feature; Surface Features, for example quotation marks, are also an unstable feature as they don’t always occur in historical texts; for Canonical References, please consult the research of Dr Matteo Romanello; for Signal Processing see \[SC08\].

