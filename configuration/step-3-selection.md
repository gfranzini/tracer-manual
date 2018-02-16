# Step 3. Selection

![](/assets/architecture.png)

There are roughly **sixty different selection strategies** in TRACER,which can also be combined. Through _Selection_ we look at the idiosyncrasies or minutiae of the features we’ve computed, thus focusing on fewer features while being faster and more precise. This is the point where we create our ‘fingerprint’ with the core reuse elements we’re interested in. Algorithmically-speaking, through _Selection_ some entries in the `KJV.train` file will be kicked out. With _Selection_ we’re narrowing down the search by filtering out all irrelevant results. The challenge in this step is to find out what our core elements or minutiae are.

## Selection strategies

There aremany different selection strategies, including:

* _Pruning_: maximumor minimum.

  * Maximum pruning cuts out high frequency words \(e.g. function words\); removing high frequency words reduces computational complexity. For example, if you’re looking at a feature that occurs only 10 times you are comparing one feature with 9 others - this means that you are making 90 comparisons. This is reasonably fast. If you, however, do not prune and have a frequency of 100, you would have to make 900 comparisons. That’s slow.

  * Minimum pruning removes low frequency words \(e.g. words with a frequency of 1\). Min pruning is used to clear up more space on the desk by reducing the size of the index.

* _Term weighting_: we give features a weight. Rarer words have a higher weight.

* _Frequency classes_: you can take the frequency of the most frequent word and divided it by the frequency of the word you want to compare it to.

* _Feature dependencies_: it makes a comparison between paired features and sees if there are features that tend to co-occur.

* _RandomSelection_: random selection of features. Very good if you don’t have a clue of what to expect from your data.

* > **\[danger\] **_**Winnowing**_**: with this strategy we can pick a window... PROVIDE CLEARER EXPLANATION. The selection is made based on the rarest parts of the winnowing window - i.e. the most infrequent features. But in this way function words are not entirely removed, since sometimes they can still be useful. With the winnowing algorithm it’s possible to select features all over the reuse unit and avoid clusters. For example, “To be or not to be that is the question". It would appear that the only interesting word here is ‘question’ but we don’t want to be eliminating all of the rest. Winnowing, with its windows, allows us to pick the lowest ranked feature \(in frequency\) for every window - so there is a selected feature for every window and features are distributed evenly.**

To change the selection strategy in TRACER, locate the _Selection_ strategy in the `tracer_config.xml` file, as shown in the Figure below.





