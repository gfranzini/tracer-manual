# Configuration

TRACER’s configuration file is its control tower. This is where you define the parameters of your detection tasks. To open TRACER’s configuration file, `tracer_config.xml`, open a terminal window, change directory to your TRACER folder \(with `cd` \) and type:

`vim conf/tracer_config.xml`

  
Press `ENTER` and you should now see the following screen:



  


Properties aremade up of a namespace and a class . For example:

  
  


To point TRACER to your corpus or texts, locate the eighth property, `SENTENCE_FILE_NAME`:

  


As you can see, the default corpus of TRACER is the `KJV.txt` Bible file \(King James Version \). If you want to work with a different text, you must first format it in accordance with TRACER requirements and store it the `corpora` sub-folder of TRACER \(see section 4.2\).

