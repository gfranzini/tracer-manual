# Step 1. Preprocessing

![](/assets/architecture.png)

With TRACER you can perform two types of preprocessing, **letter-level** and **word-level processing**.

## Letter-level preprocessing

Letter-level preprocessing can be useful to, for example, process _scriptura continua \(=continuous script\)_, a style of writing used in antiquity without spaces or marks between words, or to detect patterns of letters, such as alliteration. The letter-level preprocessing section of `tracer_config.xml` contains the following properties, which you can activate or deactivate depending on the type of detection you need to run:

![](/assets/letter_level_prep.png)

* If the value of `boolReplaceWhitespaces` is set to `true`, TRACER will add whitespaces in a specified interval of characters. The interval is specified in the next property, `intNGramSize`.

* The value of `intNGramSize` is a number \(`int` stands for _integer_\), and defines the word-size in characters. If the value is `5`, TRACER will add a space every 5 characters, for example: `ABCDEFGIHJ` will become `ABCDE` `FGHIJ` .

* If the value of `boolRemoveDiachritics` \(sic!\) is set to `true`, TRACER will remove all diacritics from your text \(assuming you're working with languages that have diacritics, such as Ancient Greek\).

* If the value of `boolMakeAllLowerCase` is set to `true`, TRACER will transform all uppercase letters in your text to lowercase.

## Word-level preprocessing {#word-level-preprocessing}

Word-level preprocessing is the default preprocessing technique and it is used to process words. The word-level preprocessing section of `tracer_config.xml` contains the following properties, which you can activate or deactivate depending on the type of detection you need to run:

![](/assets/word_level_prep.png)

* If the value of `boolLemmatisation` is set to `true`, TRACER will reduce all words in a text to the base-form list provided by the user in the `BASEFORM_FILE_NAME` property.

* If the value of `boolReplaceSynonyms` is set to `true`, TRACER will compare all words in a text to the synonyms list provided by the user in the `SYNONYMS_FILE_NAME` property.

* If the value of `boolReplaceStringSimilarWords` is set to `true`, TRACER will swap a word with a similar word in the text\(s\), where "similar" means character-similarity. In every detection task TRACER always computes a `ssim` file with a list of string-similar words. Here is an example entry from a `ssim` file generated on Latin texts: `abiectionem     obiectiones     8       0.8`. TRACER here tells us that these two words have 8 letters in common \(`b,i,e,c,t,i,o,n,e`\) and are therefore 80% similar to one another \(`0.8 = 80%`\)  \[**NB:** TRACER always counts from 0, not 1\]. If the value of this property is set to `true`, TRACER will replace the first word with the second word.

* If the value of `boolRemoveDiachritics` \(sic!\) is set to `true`, TRACER will remove all diacritics from your text \(assuming you're working with languages that have diacritics, such as Ancient Greek\).

* If the value of `boolMakeAllLowerCase` is set to `true`, TRACER will transform all uppercase letters or words in your text to lowercase.

* If the value of `boolReplaceWordByWordLength` is set to `true`, TRACER will replace all words with a number representing their length in characters \(so, the word _HOUSE_ would become _5_\).

* > If the value of `boolReplaceByReducedString` is set to `true`, TRACER will...
* The value of `intMinWordLengthThreshold` is tied to the `boolReplaceStringSimilarWords` property and defines the minimum word length \(in characters\) that both words have to have in order for the replacement to happen. The default number is set to `5` characters but it can be changed to any value. This feature is language-dependent so it's up to the user to decide what works best for their language. For English, the lower this value is the more noise TRACER will generate.


* > **[danger] For danger**
>
> The value of `intNGramSize` is a number defining...

* > If the value of `weigthByLogLikelihoodRatio` \(sic!\) is set to `true`, TRACER will...

If users want to detect non-literal text reuse, the value of the property `boolReplaceSynonyms` needs to be `true`. And although the name of the property misleadingly suggests that TRACER can only work with synonyms, this is not the case. Users can supply TRACER with lists of hyponyms, cohyponyms or even hypernyms if they so wish. The image below explains what these are and their relation to one another.

![hyper-hypo-cohyponym](/assets/hyper-hypo-cohyponym.png "Linguistic tree illustrating relationships between terms describing colour. Source: Wikimedia Commons.")

## Customising parameters or _properties_

To change preprocessing properties simply enable/disable them in the `tracer_config.xml` as you see fit. For example, to switch off `lemmatisation`, replace its corresponding value true with the value `false` and save the changes. When all the changes have been made, rerun TRACER and a new folder within `TRACER_DATA` will be produced with the updated results.[^1] Lemmatisation helps to, for example, discriminate nouns fromverbs \(e.g. the word ‘power’, which can be both a verb and a noun\). Lemmatisation is especially important when we wish to analyse paraphrases and allusions. If we wanted to find direct quotations \(verbatim or near verbatim\), lemmatisation is not going to be useful so we would switch its value in the `tracer_config.xml`file back to `false`.

## Understanding Preprocessing

[^1]: Results are never overwritten.

