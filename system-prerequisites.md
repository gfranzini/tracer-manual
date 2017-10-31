# System prerequisites

To use TRACER you must first ensure that you have **Java **\(version 8 or later\), **a text editor** and **unzip software** running on your computer.

## Install Java

The pre-compiled version of TRACER requires version 8 or higher of Java. To check your Java version, open the terminal or command line and type:

`java -version`

Press `ENTER`. The resulting message should looks something like this:

`java version "1.8.0_51"`

If the second number in the sequence is lower than 8, a[ new Java package needs to be installed](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html). Download the package for your operating system, install, restart the computer, open the terminal and re-type the command above. Your version should have changed to 8.

If TRACER is downloaded from its GitLab repository \(see [_Download and installation_](/download-and-installation.md)\) and compiled _locally_ the earlier Java 6 version is sufficient. Nevertheless, the use of the latest Java compiler, such as JDK 8 or later, is recommended.

## Install Apache Ant

Apache Ant is a build system used to create an executable program. Among its many benefits[^1], Ant allows to execute sequences of tasks from an XML file, typically called `build.xml`. Apache Ant is used to compile TRACER’s source code into an executable program \(see _Compiling TRACER_\).

If you install TRACER on a Linux system, you can use package managers such as `dnf` or `apt-get` to install Apache Ant. The benefit of using your system’s package manager is that new releases of Ant will be automatically installed when performing an update. To install Apache Ant with `apt-get` type the following command:

[^1]: For a full list of Apache Ant's capabilities, see [http://ant.apache.org/manual/index.html](http://ant.apache.org/manual/index.html)

