# System prerequisites

To use TRACER you must first ensure that you have **Java **\(version 8 or later\), **a text editor** and **unzip software** running on your computer.

## Install Java {#install-java}

The pre-compiled version of TRACER requires version 8 or higher of Java. To check your Java version, open the terminal or command line and type:

`java -version`

Press `ENTER`. The resulting message should looks something like this:

`java version "1.8.0_51"`

If the second number in the sequence is lower than 8, a[ new Java package needs to be installed](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html). Download the package for your operating system, install, restart the computer, open the terminal and re-type the command above. Your version should have changed to 8.

If TRACER is downloaded from its GitLab repository \(see [_Download and installation_](/download-and-installation.md)\) and compiled _locally_ the earlier Java 6 version is sufficient. Nevertheless, the use of the latest Java compiler, such as JDK 8 or later, is recommended.

## Install Apache Ant \(Linux\)

Apache Ant is a build system used to create an executable program. Among its many benefits[^1], Ant allows to execute sequences of tasks from an XML file, typically called `build.xml`. Apache Ant is used to compile TRACER’s source code into an executable program \(see _Compiling TRACER_\).

**If you install TRACER on a Linux system**, you can use package managers such as `dnf` or `apt-get` to install Apache Ant. The benefit of using your system’s package manager is that new releases of Ant will be automatically installed when performing an update. To install Apache Ant with `apt-get` type the following command:

`sudo apt-get install ant`

If your Linux distribution uses `dnf` then type the following command:

`sudo dnf install ant`

If you're a Linux user, the installation instructions above should suffice in helping you run Apache Ant and you can therefore skip the rest of this section. If, however, you prefer to install Ant manually, then please read on.

## Install Apache Ant \(Windows and Mac OS\)

Apache Ant is a regularly updated software. At the time of writing these guidelines \(May 2017\), the latest version of Ant is 1.10.1. The following instructions are based on this version. **Please ensure your Ant version is always up-to-date**. Navigate to the [Apache Ant download page](/ant.apache.org/bindownload.cgi). There, the _Current Release of Ant_ section lists different download options in archive formats. Select the `.zip` format. For the Ant 1.10.1 version, select [`apache-ant-1.10.1-bin.zip`](/mirror.synyx.de/apache//ant/binaries/apache-ant-1.10.1-bin.zip). The `bin` substring in the file name indicates that a pre-compiled binary and executable Java program is included in this release of Ant. Please store this file in a dedicated folder on your machine, such as `/Users/johnsmith/Tools`. If you want to make Apache Ant available for more than one user on your machine \(e.g. make it accessible from a server\), you should not install Ant in a personal home folder \(e.g. `/Users/johnsmith`\) but in an openly accessible folder, such as `/opt/apache-ant`. The instructions below are based on the installation of Ant in a personal folder.

### Unpacking Apache Ant

The download file can be extracted by navigating to the download folder, right clicking the `apache-ant-1.10.1-bin.zip` file and selecting `Extract`. Alternatively, the extraction can be processed via the command line. To do so, open a terminal and use the `cd` command to change to your download folder. For example:

`cd / Users / johnsmith / Tools`

To unzip the file, type:

`unzip apache−ant−1.10.1−bin.zip`

After unzipping the file, a new folder `apache-ant-1.10.1` is created. You can verify its existence by typing:

`ls -l`

For Windows users \(see [_Command line cheat-sheet_](/command-line.md)\) the command is not `ls -l` but:

`dir`

Under Mac OS X and Linux distributions, it is also necessary to set the access rights so that the program can be also executed. You can set the necessary rights by typing:

`chmod−R 755 *`

## Install Sublime Text Editor

Install [Sublime Text](https://www.sublimetext.com/) \(free\).

## Install Zip software

Make sure you also have unzip software, such as [WinZip](http://www.winzip.com/mac/en/) or [7-Zip](http://www.7-zip.org/), installed on your computer. The TRACER package you download has to be unzipped to be used.

[^1]: For a full list of Apache Ant's capabilities, see [http://ant.apache.org/manual/index.html](http://ant.apache.org/manual/index.html)

