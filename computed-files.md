# Results and computed files

For every detection task TRACER computes a number of files, including, [as previously seen](/configuration/step-5-scoring.md), the text reuse results in a `.score` file. This page describes all of these.

## How to read TRACER result files

The .score file contains all computed reuse pairs. The first two columns list the IDs of the aligned reuse units, the third column displays the number of shared features \(absolute overlap\) and the fourth column the degree of similarity \(weighted overlap\). A similarity of `0.1` is 10%, of `0.2` is 20% and so on until `1` = 100%.



1101991    1300887    2.0    0.5

1300887    1101991    2.0    0.5

1102581    1300887    2.0    0.5

1300887    1102581    2.0    0.5

1104023    1301050    3.0    0.6

