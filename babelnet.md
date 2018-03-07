# BabelNet API \[internal use only\]

As well as using WordNets for synonym look-up, we can use the [BabelNet API](http://babelnet.org/) to generate lists of hyponyms, cohyponyms and hypernyms.

The BabelNet look-up script can be started with the following command:

```java -Xmx70g -cp tracer.jar eu.etrap.tracer.preprocessing.external.semantic.BabelNetTestMain ../lemma-list.txt EN >babelnet-queries.log```

Where:

* `-Xmx70g` defines the memory to be used on the server; with a 70 gigabyte memory the BabelNet API look-up can take up to three days to compute.

* `lemma-list.txt` \(a better file name might be `lemma-babelnet.txt`\) is a modified version of TRACER's `lemma.txt` file containing only the base-form of every word in the text and its PoS tag \(so, a two column file separated by a TAB\). Place the `lemma.list.txt` in the TRACER's `data/corpora/...` directory and define its path in the command above.

* `babelnet-queries.log` is the log.

The script crunches two parameters: the `lemma-list.txt` and the language code \(e.g. `EN` if you are working with English texts, `DE` if you are working with German texts, etc.\). All generated files will be placed in the TRACER directory.

With `cat babelnet-queries.log | grep "PROCESSING WORD" | wc -l` you see the total number of processed words out of the total number of base-forms in `lemma-list.txt`.

