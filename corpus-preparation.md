# Corpus preparation

This section describes how to prepare your texts for TRACER \(subsection _The text\(s\)_\) and what other types of data you need \(subsection _Supporting linguistic files_\).

## The text\(s\)

TRACER works with plain text files \(`.txt`\). This means that if you have marked-up texts in XML, you must remove all of the XML tags before you can use TRACER. To create and manipulate `.txt` files, use Sublime Text, as previously recommended.

To optimise the performance of TRACER, place your texts \(two or more, depending on how many you wish to analyse\) in the same `.txt` file, one under the other. Placing all texts in a single file is beneficial as TRACER will consider every line as a reuse unit to compare. To distinguish the texts, you will use different IDs \(keep reading to find out how to do this\).

### Segmentation

The first thing you need to do is to segmentise your texts by verse, paragraph, sentence, or whatever unit you believe best suits your reuse analysis. Every unit must appear on a separate line in the `.txt` file. You can use the [free NLTK service](http://textanalysisonline.com/nltk-sentence-segmentation) to segmentise your text, but this tool will use full-stops as the only cue to identify the end of a sentence. Copy and paste your unsegmentised `.txt` into NLTK’s text box. Click on the segmentation button, copy the segmentised output and paste it into a new `.txt` file. Save this new file and give it a clear name, such as `mytext-segmentised.txt`. Please note that NLTK only takes a certain number of lines, so if you have a very long text you will have to divide it into smaller chunks. Always double-check the output because sometimes formatting errors can sneak in unnoticed.

### Column layout

Next, your `.txt` must contain four columns separated by **TAB**s:

1. The **first column** contains unique sentence IDs.
2. The **second column** contains the sentence.

3. The **third column** can contain the date of the file creation in the `YYYY-MM-DD` format or the word `NULL`. If you use `NULL`, make sure it is written in upper-case.

4. The **fourth column** contains the book or section from which the sentence is taken. This information is crucial for the visualisation shown IMAGE REFERENCE. The top drop-down menu you see there will list the information you provide in this fourth column.

You can achieve this column structure by using the proprietary [Microsoft Excel](https://products.office.com/en/excel) or the free [Libre Office](https://www.libreoffice.org/download/libreoffice-fresh/). The **instructions below are based on Libre Office Version 5.1.5.2**.

First, you need to import the segmentised texts stored in your `.txt` file into Excel or Libre. To do so, simply right click on the `.txt` file, click on `Open with` and select either Excel or Libre. Alternatively, open Microsoft or Libre, click on `File > Open` and select the `.txt` file. Whatever you choose, **it’s essential that you specify **`TAB`** as the field separator when importing the file**. If you don’t, TRACER won’t be able to read your file. The import window looks something like this:

![](/assets/libre-tab.png)Libre file import window. Select `TAB` as the field separator.



Select `TAB` in the `Separator Options` section and click `OK`. You should now see something like this:

![](/assets/libre.png)How a segmentised text first appears in Libre Office.

## Supporting linguistic files



