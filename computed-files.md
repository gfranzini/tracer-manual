# Results and computed files

For every detection task TRACER computes a number of files, including, [as previously seen](/configuration/step-5-scoring.md), the text reuse results in a `.score` file. This page describes all of these.

## Where to find TRACER results

The results of every TRACER run are automatically stored in a newly generated folder called `TRACER_DATA` under TRACER's `data > corpora > Bible`:

![folder-structure](/assets/tracer_data.png "The folder path and location of the text reuse results produced by TRACER.")

If you’re working with your own texts –not TRACER’s default Bible data– the `TRACER_DATA` folder would be created in your specified directory \(e.g. `data > corpora > MyTexts`\).

TRACER organises the results in a deep folder structure with long folder names that describe the parameters used for a particular analysis. For every new analysis, TRACER creates a separate folder.

![folder-name](/assets/tracer_data_sub.png "The folder structure within TRACER\_DATA. Long folder names are used to reflect the property settings in the TRACER tracer\_config.xml file. This system allows users to better locate their results, especially when running TRACER multiple times with modified parameters.")

The folder name in the Figure above reads as follows:

`01-02-WLP-lem_true_syn_true_ssim_false_redwo_false-ngram_5-LLR_true_toLC_false_rDia_false_w2wl_false-wlt_5`  
Let's break it down:

| Abbreviation in folder name | Meaning of abbreviation |
| :--- | :--- |
| `01-02-WLP-` | Preprocessing step \(01\)-word-level \(02\)-Word Level Processing |
| `lem_true_` | Lemmatisation ENABLED |
| `syn_true_` | Synonym replacement ENABLED |
| `ssim_false_` | Replace String Similar words DISABLED |
| `redwo_false-ngram_5-LLR_true_` | Reduced words option DISABLED-to the most significant 5 letter ngram-significance is measured by the Log-Likelihood Ratio ENABLED |
| `toLC_false_` | Everything to lower case DISABLED |
| `rDia_false_` | Remove diacritics DISABLED |
| `w2wl_false-wlt_5` | Replace word by word length DISABLED-For words of 5 letters or more |

This folder represents the first step in your detection task, _Preprocessing_. The other five steps of the detection process are all nested within this folder.  So, if you open the _Preprocessing_ folder, you’ll find the second folder in the sequence, the _Featuring/Training_ folder. Within the _Featuring/Training_ folder, you’ll find the _Selection_ folder, and so on until you reach the final _Scoring_ folder. In each and every folder you’ll find the relevant files resulting from the settings you specified in the `tracer_config.xml` file.

### Computed files for Preprocessing

> **[warning] To update**
>
> Explain here in which folder these files are stored.

#### `.inv`

`inv` stands for _inverted list_. This file works like a word index and is the heart of any retrieval system. It shows you the position of a given word in a given textual segment/unit. For example, the row `114    4003870    2` in an `.inv` TRACER file means that word `114` can be found in segment `4003870` in position `2`.


#### `.wnc`
`wnc` stands for _words number complete_. This file gives more information about the word types in the corpus including frequency, rank and word length. IDs are frequency-sorted.

#### `.meta`
This file provides an overview (the "metadata" as it were) of the corpus segmentation:

* `SENTENCES`: lines.
* `WORD_TYPES`: number of unique words as dictionary entries.
* `WORD_TOKENS`: occurrences of a word; every word in a text, no matter how many times it occurs.
* `SOURCES`: for example, a book.
* `SSIM_THRESHOLD`: degree of similarity required to consider two words as similarly written.
* `SSIM_EDGES`: number of links or word pairs satisfying the similarity requirements stated in `SSIM_THRESHOLD`.
* `BOW_WORD_TOKENS`: tokens or unique words that appear in a line.

* > **[warning] To update** 
> 
> `SSIM_`: explain

#### `.tok`
This file is a _tokenized_ version of the source text. This means that all punctuation has been removed or separated from the word (depending on the settings). The default setting in TRACER is `delete`.

#### `.tok.dist.char`

This file displays the distribution of the characters across the corpus.  This file is useful to clean up overlooked dirt in the text\(s\) under analysis. If the file contains an unexpected character, thanks to the `.char` information the user can more easily identify and remove it from the text\(s\).

#### `.tok.dist.letter.02gram`

This file displays the distribution of letter bigrams across the corpus.

#### `.ssim`
Everything comes together in this file. The first and second columns represent the two words; the third column is the overlap of letter bigrams; the fourth column is the weighted overlap `§w§` between:


by Broder’s Resemblance measure.

> **[warning] To update**
>
> Explain formula



### Computed files for Featuring/Training

> **\[warning\] To update**
>
> Describe files

### Computed files for Selection

> **\[warning\] To update**
>
> Describe files

### Computed files for Linking

> **\[warning\] To update**
>
> Describe files

### Computed files for Scoring

The `.score` file contains all computed reuse pairs. The first two columns list the IDs of the aligned reuse units, the third column displays the number of shared features \(absolute overlap\) and the fourth column the degree of similarity \(weighted overlap\). A similarity of `0.1` is 10%, of `0.2` is 20% and so on until `1` = 100%. In the example below, the two sentences have two features in common for a total similarity of 50%:

`1101991    1300887    2.0    0.5`

**NB:** The `.score` file lists results bidirectionally and thus redundantly. The two results below, for example, represent the same reuse alignment but the order of the IDs is inverted:

`1102581    1300887    2.0    0.5`  
`1300887    1102581    2.0    0.5`

