# Step 5. Scoring

![](/assets/architecture.png)

The _Scoring_ step of TRACER assigns a weight to a reuse pair based on an internal scoring metric. To calculate the resemblance score, TRACER uses the formula:

![](/assets/scoring-formula.png)

The extension of the file in which the scores are recorded is `.score`. This file contains four columns of data, for example:

`4000237   4010258   13.0   1.0`

The first two numbers represent two aligned sentences, a sentence in _Text A_ with the ID `4000237` and its reused version in _Text B_ with the ID `4010258`. The third number is an _**absolute overlap**_, indicating that the two sentences share 13 features \(e.g. 13 words, if the user set the _Featuring_ to `WordBased`\). The fourth number is the _**weighted overlap**_ or the percentage of similarity between the two sentences - in this case, `1.0` means 100% similar, indicating that _Text B_ reused _Text A_ word-for-word \(verbatim\); a weighted overlap of `0.9` is 90%, `0.8` is 80% and so on.



