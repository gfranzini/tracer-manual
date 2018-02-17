# Results and computed files

For every detection task TRACER computes a number of files, including, [as previously seen](/configuration/step-5-scoring.md), the text reuse results in a `.score` file. This page describes all of these.

## Where to find TRACER results

The results of every TRACER run are automatically stored in a newly generated folder called `TRACER_DATA` under TRACER's `data > corpora > Bible`:

![folder-structure](/assets/tracer_data.png "The folder path and location of the text reuse results produced by TRACER.")

If you’re working with your own texts –not TRACER’s default Bible data– the `TRACER_DATA` folder would be created in your specified directory \(e.g. `data > corpora > MyTexts`\).

TRACER organises the results in a deep folder structure with long folder names that describe the parameters used for a particular analysis. For every new analysis, TRACER creates a separate folder.

![folder-name](/assets/tracer_data_sub.png "The folder structure within TRACER_DATA. Long folder names are used to reflect the property settings in the TRACER tracer_config.xml file. This system allows users to better locate their results, especially when running TRACER multiple times with modified parameters.")

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
The _Preprocessing_ folder in TRACER_DATA includes the following files:





### Computed files for Featuring/Training

> **[warning] To update**
>
> Describe files

### Computed files for Selection

> **[warning] To update**
>
> Describe files

### Computed files for Linking

> **[warning] To update**
>
> Describe files

### Computed files for Scoring

The `.score` file contains all computed reuse pairs. The first two columns list the IDs of the aligned reuse units, the third column displays the number of shared features \(absolute overlap\) and the fourth column the degree of similarity \(weighted overlap\). A similarity of `0.1` is 10%, of `0.2` is 20% and so on until `1` = 100%. In the example below, the two sentences have two features in common for a total similarity of 50%:

`1101991    1300887    2.0    0.5`

**NB:** The `.score` file lists results bidirectionally and thus redundantly. The two results below, for example, represent the same reuse alignment but the order of the IDs is inverted:

`1102581    1300887    2.0    0.5`  
`1300887    1102581    2.0    0.5`