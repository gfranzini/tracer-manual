# TRACER: Quick overview {#tracer-overview}

TRACER is a suite of 700 algorithms, whose features can be combined to create the optimal model for detecting those words, sentences and ideas that have been reused across texts. Created by Marco Büchler during the eTRACES project at the University of Leipzig, TRACER is designed to facilitate research in automatic text reuse detection and many have made use of it to identify plagiarism in a text, as well as verbatim and near verbatim quotations, paraphrase and even allusions. The thousands of feature combinations that TRACER supports allow to investigate not only contemporary texts, but also historical texts. **TRACER is a command line engine**. The reason it does not come with a user-interface is to boost computing speed. TRACER can use large and remotely-accessible servers, which facilitate the computation of large data-sets. The reuse results _can_ be visualised in a more readable format via TRAViz \(see [_Step 6.Postprocessing_](/configuration/step-6-postprocessing.md)\).

![architecture](/assets/architecture.png "This image shows one text reuse detection task in TRACER (left-to-right). Each task is split into six steps.")

## Current state

**TRACER is language independent** and has been successfully tested on Ancient Greek, Arabic, Coptic, English, German, Hebrew, Latin and Tibetan. The [_Publications_](/external-reports.md) section of this manual lists reports written by TRACER users. We continuously seek new languages to work with. TRACER has been used on both historical and modern texts. A list of bug reports and current developments is available [here](http://www.etrap.eu/redmine/projects/tracer/).

## Under the hood

**This manual provides a user-friendly guide to text reuse detection for both novice and expert users**. For this reason, it does not give an accurate description of the roughly 700 algorithms constituting TRACER but only the necessary knowledge in order to perform simple text reuse detection tasks. Those who wish to study TRACER’s algorithms in detail should consult [TRACER’s Javadoc](http://www.etrap.eu/tracer/doc/javadoc/).

