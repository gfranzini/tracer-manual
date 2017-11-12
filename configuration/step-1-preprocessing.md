# Step 1. Preprocessing

![](/assets/architecture.png)

With TRACER you can perform two types of preprocessing, **letter-level** and **word-level processing**.

**Letter-level preprocessing. **This can be useful to, for example, process _scriptura continua \(=continuous script\)_, a style of writing used in antiquity without spaces or marks between words, or to detect patterns of letters, such as alliteration. The letter-level preprocessing section of `tracer_config.xml` contains the following properties, which you can activate or deactivate depending on the type of detection you need to run:

![](/assets/letter_level_prep.png)

* If the value of `boolReplaceWhitespaces` is set to `true`, TRACER will ... 
* The value of `intNGramSize` is a number, and defines the number of letters TRACER ....
* If the value of `boolRemoveDiachritics` \(sic!\) is set to `true`, TRACER will remove all diacritics from your text \(assuming you're working with languages that have diacritics, such as Ancient Greek\).
* If the value of `boolMakeAllLowerCase` is set to `true`, TRACER will transform all uppercase letters in your text to lowercase. 

**Word-level preprocessing.** This is the default preprocessing technique and it is used to read sequences of words. The word-level preprocessing section of `tracer_config.xml` contains the following properties, which you can activate or deactivate depending on the type of detection you need to run:

![](/assets/word_level_prep.png)

* If the value of `boolLemmatisation` is set to `true`, TRACER will reduce all words in a text to the base-form list provided by the user in the `BASEFORM_FILE_NAME` property.

* If the value of `boolReplaceSynonyms` is set to `true`, TRACER will compare all words in a text to the synonyms list provided by the user in the `SYNONYMS_FILE_NAME` property.

* If the value of `boolReplaceStringSimilarWords` is set to `true`, TRACER will swap a word with a similar word in the text\(s\), where "similar" means character-similarity. In every detection task TRACER always computes a `ssim` file with a list of string-similar words. Here is an example entry from a `ssim` file generated on Latin texts: `abiectionem     obiectiones     8       0.8`. TRACER here tells us that these two words have 8 letters in common \(`b,i,e,c,t,i,o,n,e`\) and are therefore 80% similar to one another \(`0.8 = 80%`\)  \[**NB:** TRACER always counts from 0, not 1\]. If the value of this property is set to `true`, TRACER will replace the first word with the second word.

* If the value of `boolRemoveDiachritics` \(sic!\) is set to `true`, TRACER will remove all diacritics from your text \(assuming you're working with languages that have diacritics, such as Ancient Greek\).

* If the value of `boolMakeAllLowerCase` is set to `true`, TRACER will transform all uppercase letters or words in your text to lowercase.
* If the value of `boolReplaceWordByWordLength` is set to `true`, TRACER will replace all words with a number representing their length in characters \(so, the word _HOUSE_ would become _5_\).
* If the value of `boolReplaceByReducedString` is set to `true`, TRACER will...
* The value of `intMinWordLengthThreshold` is a number defining...
* The value of `intNGramSize` is a number defining...
* If the value of `weigthByLogLikelihoodRatio` \(sic!\) is set to `true`, TRACER will...

options include string similarity, , which can be used to detect similar words or strings to reveal OCR errors, morphological variation or even spelling errors.

Remember to always save your changes!

