# Results and computed files

For every detection task TRACER computes a number of files, including, [as previously seen](/configuration/step-5-scoring.md), the text reuse results in a `.score` file. This page describes all of these.

## Where to find TRACER results

The results of every TRACER run are automatically stored in a newly generated folder called `TRACER_DATA` under TRACER's `data > corpora > Bible`:

![](/assets/tracer_data.png)

If you’re working with your own texts –not TRACER’s default Bible data– the `TRACER_DATA` folder would be created in your specified directory \(e.g. `data > corpora > MyTexts`\).

TRACER organises the results in a deep folder structure with long folder names that describe the parameters used for a particular analysis. For every new analysis, TRACER creates a separate folder.

![](/assets/tracer_data_sub.png)

The folder name in the Figure above reads as follows:

`01-02-WLP-lem_true_syn_true_ssim_false_redwo_false-ngram_5-LLR_true_toLC_false_rDia_false_w2wl_false-wlt_5`  
Let's break it down:



| `01-02-WLP-` | Preprocessing step (01)-word-level (02)-Word Level Processing |
| :--- | :--- |
| `lem_true_` | Lemmatisation ENABLED |
| `syn_true_` | Synonym replacement ENABLED |
| `ssim_false_` | Replace String Similar words DISABLED |
| `redwo_false-ngram_5-LLR_true_` | Reduced words option DISABLED-to the most significant 5 letter ngram-significance is measured by the Log-Likelihood Ratio ENABLED |
| `toLC_false_` | Everything to lower case DISABLED |
| `rDia_false_` | Remove diacritics DISABLED |
| `w2wl_false-wlt_5` | Replace word by word length DISABLED-For words of 5 letters or more |

Every run of TRACER automatically produces a number of files, which can be viewed in the corpora directory. For example, running TRACER on the KJV.txt file will automatically produce the following files \(also depending on the parameters set in the  
tracer\_config.xml file, as already described in section 6.4\):  
KJV.txt.inv inv stands for inverted list  
. This file works like a word index and is the heart of any retrieval system. It

## How to read TRACER result files

The `.score` file contains all computed reuse pairs. The first two columns list the IDs of the aligned reuse units, the third column displays the number of shared features \(absolute overlap\) and the fourth column the degree of similarity \(weighted overlap\). A similarity of `0.1` is 10%, of `0.2` is 20% and so on until `1` = 100%. In the example below, the two sentences have two features in common for a total similarity of 50%:

`1101991    1300887    2.0    0.5`

**NB:** The `.score` file lists results bidirectionally and thus redundantly. The two results below, for example, represent the same reuse alignment but the order of the IDs is inverted:

`1102581    1300887    2.0    0.5`  
`1300887    1102581    2.0    0.5`

