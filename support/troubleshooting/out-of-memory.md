# Out of memory

If TRACER generates an `out-of-memory` error, the problem is likely caused by the _Scoring_ threshold set in the configuration file. If the _Scoring_ threshold is too low, such as `0.1`, TRACER needs more time and memory to compute the results, as a low _Scoring_ threshold leads to a large number of results. To solve the issue, increase the memory value contained in the TRACER execution command from `Xmx600m` \(600 MB of memory\) to, for example, `Xmx1g` \(1 GB of memory\).

