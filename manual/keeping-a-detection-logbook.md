# Keeping a detection logbook

By now, the reader will have realised that multiple detection tasks are needed per work-pair in order to tease out as many text reuse styles from the texts as possible. To help keep track of these experiments, we recommend the creation of a logbook to record each and every task with the respective result-set. We find this helps to avoid duplicating analyses and more easily identify the optimal settings for a particular detection task. An example logbook might look something like this:

## WORD-BASED FEATURING

| **Task N** | **Preprocessing** | **Selection** | **Scoring** | **Result** |
| :--- | :--- | :--- | :--- | :--- |
| 1 | syn-repl.; lemmatiz. | local-max-feat-freq.; 0.6 feat-dens. | 0.5 sim-thresh. | 5 reuses |
| 2 | ... | ... | ... | ... |
| 3 | ... | ... | ... | ... |

## BIGRAM FEATURING

| **Task N** | **Preprocessing** | **Selection** | **Scoring** | **Result** |
| :--- | :--- | :--- | :--- | :--- |
| 1 | ... | ... | ... | ... |
| 2 | ... | ... | ... | ... |

## TRIGRAM FEATURING

| **Task N** | **Preprocessing** | **Selection** | **Scoring** | **Result** |
| :--- | :--- | :--- | :--- | :--- |
| 1 | ... | ... | ... | ... |
| 2 | ... | ... | ... | ... |

