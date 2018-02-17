# Results and computed files

For every detection task TRACER computes a number of files, including, [as previously seen](/configuration/step-5-scoring.md), the text reuse results in a `.score` file. This page describes all of these.


## Where to find TRACER results
The results of every TRACER run are automatically stored in a newly generated folder called `TRACER_DATA` under TRACER's `data > corpora > Bible`:


If you’re working with your own texts –not TRACER’s default Bible data– the `TRACER_DATA` folder would be created in your relevant directory (e.g. `data > corpora > MyTexts`).

TRACER organises the results to reflect any changes the user makes to the configuration parameters
(more about configuration customisations in section 5.3). It creates a deep folder structure with long
but self-explanatory folder names. Figure 5.3 below is the extension of Figure 5.2.

As you can see, the first run of TRACER produced a folder with a very long name:

01¡02¡WLP¡lem_true_syn_true_ssim_false_redwo_false¡ngram_5¡
LLR_true_toLC_false_rDia_false_w2wl_false¡wlt_5
Here’s how you read it (see also section 5.3.1 and section 5.3.2):





Every run of TRACER automatically produces a number of files, which can be viewed in the
corpora
directory. For example, running TRACER on the
KJV.txt
file will automatically produce the following
files (also depending on the parameters set in the
tracer_config.xml
file, as already described in
section 6.4):
KJV.txt.inv
inv
stands for
inv
erted list
. This file works like a word index and is the heart of any retrieval system. It





## How to read TRACER result files

The `.score` file contains all computed reuse pairs. The first two columns list the IDs of the aligned reuse units, the third column displays the number of shared features \(absolute overlap\) and the fourth column the degree of similarity \(weighted overlap\). A similarity of `0.1` is 10%, of `0.2` is 20% and so on until `1` = 100%. In the example below, the two sentences have two features in common for a total similarity of 50%:

`1101991    1300887    2.0    0.5`

**NB:** The `.score` file lists results bidirectionally and thus redundantly. The two results below, for example, represent the same reuse alignment but the order of the IDs is inverted:

`1102581    1300887    2.0    0.5`
`1300887    1102581    2.0    0.5`



