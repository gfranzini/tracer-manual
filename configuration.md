# Configuration

TRACER’s configuration file is its control tower. This is where you define the parameters of your detection tasks. To open TRACER’s configuration file, open the conf subfolder of your TRACER folder and open the `tracer_config.xml` file in a text editor. You should now see something like this:

![](/assets/config-file.png)

The file begins with a list of properties. Properties are  made up of a namespace and a class . For example:![](/assets/namespace-class.png)

Properties 2-7 are the six steps of the TRACER [architecture described earlier](/tracer-overview.md). The image below is a reminder of that architecture.

![](/assets/architecture.png)

Properties 8-10 define the paths to the texts or corpus to be analysed and to other supporting files. The eighth property in your configuration file, `SENTENCE_FILE_NAME`, is set to `KJV.txt` as default. _KJV_ stands for _King James Version _\(of the Bible\) and is an example text to analyse stored in `data/corpora/Bible`. If you want to work with a different text, you must [first format it in accordance with TRACER requirements](/corpus-preparation.md), store it the `corpora` subfolder of TRACER and change the path in the configuration file from `data/corpora/Bible/KJV.txt` to `data/corpora/MyFolder/MyText.txt`.

