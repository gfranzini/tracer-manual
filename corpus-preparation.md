# Corpus preparation {#corpus-preparation}

TRACER works with plain text files \(`.txt`\). This means that if you have marked-up texts in XML, you must remove all of the XML tags before you can use TRACER. To create and manipulate `.txt` files, use Sublime Text, as previously recommended.

To optimise the performance of TRACER, place your texts \(two or more, depending on how many you wish to analyse\) in the same `.txt` file, one under the other. Placing all texts in a single file is beneficial as TRACER will consider every line as a reuse unit to compare. To distinguish the texts, you will use different IDs \(keep reading to find out how to do this\).

### Segmentation

The first thing you need to do is to segmentise your texts by verse, paragraph, sentence, or whatever unit you believe best suits your reuse analysis. Every unit must appear on a separate line in the `.txt` file. You can use the [free NLTK service](http://textanalysisonline.com/nltk-sentence-segmentation) to segmentise your text, but this tool will use full-stops as the only cue to identify the end of a sentence. Copy and paste your unsegmentised `.txt` into NLTK’s text box. Click on the segmentation button, copy the segmentised output and paste it into a new `.txt` file. Save this new file and give it a clear name, such as `mytext-segmentised.txt`. Please note that NLTK only takes a certain number of lines, so if you have a very long text you will have to divide it into smaller chunks. Always double-check the output because sometimes formatting errors can sneak in unnoticed.

### Column layout

Next, your `.txt` must contain four columns separated by **TAB**s:

1. The **first column** contains unique sentence IDs.
2. The **second column** contains the sentence.

3. The **third column** can contain the date of the file creation in the `YYYY-MM-DD` format or the word `NULL`. If you use `NULL`, make sure it is written in upper-case.

4. The **fourth column** contains the book or section from which the sentence is taken. This information is crucial for the visualisation shown &lt;ADD IMAGE REFERENCE&gt;. The top drop-down menu you see there will list the information you provide in this fourth column.

You can achieve this column structure by using the proprietary [Microsoft Excel](https://products.office.com/en/excel) or the free [Libre Office](https://www.libreoffice.org/download/libreoffice-fresh/). The **instructions below are based on Libre Office Version 5.1.5.2**.

First, you need to import the segmentised texts stored in your `.txt` file into Excel or Libre. To do so, simply right click on the `.txt` file, click on `Open with` and select either Excel or Libre. Alternatively, open Microsoft or Libre, click on `File > Open` and select the `.txt` file. Whatever you choose, **it’s essential that you specify **`TAB`** as the field separator when importing the file**. If you don’t, TRACER won’t be able to read your file. The import window looks something like this:

![tab](/assets/libre-tab.png "Libre file import window. Select \`TAB\` as the field separator.")

Select `TAB` in the `Separator Options` section and click `OK`. You should now see something like this:

![segment](/assets/libre.png "How a segmentised text first appears in Libre Office.")

We now need to remove all blank rows. If you’re using Libre, select the entire text column, then click on the autofilter button in the toolbar \(it looks like a funnel\). This generates a clickable arrow symbol on the first cell. Click the arrow and select `EMPTY` from the list of options \(see image below\).

![empty](/assets/librefilter.png "Select all empty lines in the file.")

This will bring all blank rows to the top of the document \(if you look at the row IDs now you’ll notice that the column only lists even numbers, i.e. alternating blank rows\). Delete all of these by pressing the `SHIFT` button on your keyboard, keeping it pressed while selecting all of the rows, then release the `SHIFT` button, right-click on the selected rows and click on `DELETE`. Next, press on the arrow again and select `NOT EMPTY`. You should now see your text, one sentence per row and no blank rows. Finally, deselect the autofilter button in the toolbar and save the changes.

**IMPORTANT: Make sure you remove all blank lines from your file \(check the bottom of the file as well\) as these will not be correctly processed by TRACER and will cause the detection task to break.**

If you’re using Microsoft Excel, select the first column, click on the `FILTER` button in the toolbar. Again, click on the little arrow that is now available in the first cell. In the new pop-up window you need to do two things: first, click on the `SELECT ALL` option to deselect all options; second, scroll down to the bottom of the options pane and select `BLANKS`. This will bring all the empty rows to the top of the document \(if you look at the row IDs now you’ll notice that the column only lists even numbers in blue\). Delete all the empty rows by pressing the `SHIFT` button and keeping it pressed while selecting all the blue-numbered rows. Then, deselect the `FILTER` button in the toolbar and save the changes.

![blank](/assets/excel_filter_blanks.png "Select all blank lines in the file.")

Microsoft Excel’s filter buttons and pane. After deselecting all options within the pane, reselect `Blanks` in order to delete all blank rows.

Next, add a column to the left of your sentence column. This new column should contain sentence IDs. To automate the creation of IDs, type in the first three IDs \(one per sentence\), then select the three ID cells, hover over the bottom right corner of the third cell and finally drag the selection all the way down to the last sentence. Remember to save the changes!

> IF ID NUMBERING uses MILLIONS: 1,000,000; 1,100,00; 1,200,00 ---&gt; in the INTERLINKING section you need to have 100,000, not 1,000,000.

![ids](/assets/ID-column.png "The first three IDs are typed in manually. The rest are automatically generated by dragging the selection to the last sentence in the document. To drag, grab the bottom-right corner of the third cell in the ID column.")

The sentence IDs should be sequential and unique. The default set-up of TRACER requires IDs to be 7-digits in length and numbers below 2,000,000. If you're analysing two texts, make sure to restart the ID sequence for your second text. So, for example:

![id2](/assets/id-2.png "Required segment ID formatting. Texts to be analysed are told apart by the first two digits in the ID.")

As you can see from the image above, all IDs are 7-digits long and the two different texts to be analysed, _A_ and _B_, are distinguished via the first two digits of the ID. TRACER's default ID settings can be changed in the configuration file in the _Selection_ section, as shown below.![](/assets/IDs-config-file.png)

> **\[warning\] To update**
>
> IF ID NUMBERING uses MILLIONS: 1,000,000; 1,100,00; 1,200,00 ---&gt; in the INTERLINKING section you need to have 100,000, not 1,000,000.

However, doing so is **only recommended in consultation with the TRACER team** as it may affect the detection process and your results. Moreover, ensure that there are no new blank lines at the end of the document and that there’s no white-space between _text A_ and _text B_. Any blank lines will bring up errors.

Next, add two columns to the right of your sentence column. In the third column you can either put a date of file-creation \(in the `YYYY-MM-DD` format only\) or the case-sensitive word `NULL`. To populate the entire column with the date or `NULL` , repeat the drag action used above but from the first cell only, not the third. By dragging from the first the cell values will not increase or change as you move downwards.

![](/assets/null-column.png)

The fourth column should list the source of the text, whether it's a book, a chapter or the title of your text. This information is necessary for the text reuse visualisation to work later on. To populate this column repeat the actions described in the previous paragraph.

Save your four-column file as a `.csv` document. Finally, change the extension of the file from `.csv` to `.txt`.

**That's it, your text is now TRACER-compatible!**

The figure below provides an example of the King James Bible Version text formatted for TRACER.[^1]

!\[four-cols\]\(/assets/four\_columns.png "The King James Bible text formatted into four columns, as per TRACER’s requirements. The columns, from left to right, are: Unique ID, Bible verse, Creation date, Source. This file was opened with Sublime text editor."\)

### Where to store your texts

Place your texts in the `corpora` subfolder of TRACER’s `data` folder, as shown below:

!\[corpora\]\(/assets/corpora.png "Structure of the TRACER folder in the Mac 'Finder' view. Deposit your .txt file in a new folder under data &gt; corpora."\)

[^1]: This is a different example from the one we've been working on but it should give you an idea of the final document layout.

