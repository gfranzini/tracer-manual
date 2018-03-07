# BabelNet \[internal use only\]

As well as using WordNets for synonym look-up, we can use the BabelNet API to generate lists of hyponyms, cohyponyms and hypernyms.  

The BabelNet look-up script can be started with the following command:

`java -Xmx70g -cp tracer.jar eu.etrap.tracer.preprocessing.external.semantic.BabelNetTestMain ../lemma-list.txt EN >babelnet-queries.log`

Where:

* -Xmx70g defines the memory to be used on the server; with a 70g memory, it can take up to three days for the computation 

* `babelnet-queries.log` is the log.

  


The script crunches two parameters: the lemma-list and the language code \(e.g. EN\).

The lemma-list I created from the basform mapping file ../lemma\_pos.txt . It is next to the original file. All produced files will be placed in the same folder /roedel/gfranzini/2018-tracer-HarryPotter.

With

root@roedel:/roedel/gfranzini/2018-tracer-HarryPotter\# wc -l lemm-list.txt

22796 lemm-list.txt

you see the number of total baseforms \(given different pos tags\).

With

root@roedel:/roedel/gfranzini/2018-tracer-HarryPotter/tracer\# cat babelnet-queries.log \| grep "PROCESSING WORD" \| wc -l

35

you see the total number of processed words out of the 22796.

