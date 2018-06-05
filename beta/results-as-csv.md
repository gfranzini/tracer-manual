# Visualising TRACER results in tabular format


The `.score` files produced by TRACER can be transformed into a more human-readable format with a script that prints the corresponding text segment next to the reuse ID, as well as the number of overlapping features and the percentage of similarity. In the terminal, navigate to the TRACER main folder and type:

```
java -cp tracer.jar eu.etrap.tracer.postprocessing.DefaultOutputterMain /.../filename.txt /.../filename.score
```
Where:
* `/.../filename.txt` is the path to the main text file;
* `/.../filename.score` is the score file.

The new file created will have `.expanded` as its suffix and contains four columns separated by tabs: 

`RUID 1, RUID 2, FEATUREOVERLAP, SIMTHRESHOLD, TEXT 1, TEXT 2`

This `.txt` output can be duplicated and imported into a `.csv` file for the gold standard analysis
