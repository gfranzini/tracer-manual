# Download and installation {#download-and-installation}

There are two ways to download and install TRACER.

### Option 1

Download and unzip TRACER from http://www.etrap.eu/tracer/ to a folder on your computer. TRACER zipped is some 107MB in size, unzipped it’s roughly 500MB. Additionally, in order to run TRACER needs between 5GB and 10GB of space. It is therefore important that you locate a folder on your computer with 10GB of space in which TRACER can be installed and computed. Do not store and run TRACER on a USB drive as this will result in very slow computing times.

### Option 2









You can clone the most recent releases of TRACER from our git repository. However, please be aware that the most recent version might be unstable. Once you’ve obtained an account you can download the latest version from here or by using git.

# Compiling TRACER {#compiling-tracer}

To compile TRACER, please navigate to the

tracer

folder containing the

build.xml

file, which

includes all instructions on how to create the executable TRACER program, as well as the TRACER

Javadocs.

To compile the software, in the command line type:

ant

which starts the build process. Depending on the disc type and the file system, this process can take

between five and twenty seconds. Once the build process is complete, the

tracer.jar

file is created.

The

.jar

files is TRACER’s executable program and currently measures 33MB in size.

TRACER’s build file

build.xml

contains a number of targets

5

that aren’t executed in order to speed

up the build process. However, you can visualise all targets by typing:

ant

−

p verbose

which lists, among others,

javadoc

. If you now type:

ant javadoc

you’ll create TRACER’s Javadoc in the folder

doc/web/javadoc/Tracer-1.0/

. There, click on

the

index.html

file to view the Javadoc in a web browser.

