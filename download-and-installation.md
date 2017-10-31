# Download and installation {#download-and-installation}

You can download or clone the most recent release of TRACER from our GitLab repository by creating a free GitLab account. **However, please be aware that the most recent version might be unstable**.

# Compiling TRACER {#compiling-tracer}

To compile TRACER, please navigate to the TRACER folder containing the `build.xml` file, which includes all instructions on how to create the executable TRACER program. To compile the software, in the command line type:

`ant`

And press `ENTER`. This starts the build process. Depending on the disc type and the file system, this process can take between five and twenty seconds. Once the build process is complete, the `tracer.jar`file is created. The` .jar` file is TRACER’s executable program and currently measures 33MB in size.

TRACER’s build file `build.xml` contains a number of targets[^1] that aren’t executed in order to speed up the build process. However, you can visualise all targets by typing: 

`ant−p verbose`

which lists, among others, TRACER's Javadoc. If you now type:

`ant javadoc`

you’ll create TRACER’s Javadoc in the folder `doc/web/javadoc/Tracer-1.0/`. There, click on the `index.html` file to view the Javadoc in a web browser.

[^1]: A _target_ is a procedure or pipeline. Compiling code is, for example, one target. A target can consist of one or more tasks.

