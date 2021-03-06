dd-easy-sword2-to-dataverse
===========================
[![Build Status](https://travis-ci.org/DANS-KNAW/dd-easy-sword2-to-dataverse.png?branch=master)](https://travis-ci.org/DANS-KNAW/dd-easy-sword2-to-dataverse)

Transforms EASY SWORD2 deposit directories into Dataverse datasets.

SYNOPSIS
--------

    dd-easy-sword2-to-dataverse run-service


DESCRIPTION
-----------
Service that watches an inbox directory for new deposit directories. Each deposit directory that appears is checked for conformity 
to DANS BagIt Profile (SIP) and subsequently added as a dataset to the configured Dataverse.

ARGUMENTS
---------

    Options:
    
      -h, --help      Show help message
      -v, --version   Show version of this program
    
    Subcommand: run-service - Starts EASY SWORD2 To Dataverse as a daemon that services HTTP requests
      -h, --help   Show help message
    ---

INSTALLATION AND CONFIGURATION
------------------------------
Currently this project is built as an RPM package for RHEL7/CentOS7 and later. The RPM will install the binaries to
`/opt/dans.knaw.nl/dd-easy-sword2-to-dataverse` and the configuration files to `/etc/opt/dans.knaw.nl/dd-easy-sword2-to-dataverse`. 

To install the module on systems that do not support RPM, you can copy and unarchive the tarball to the target host.
You will have to take care of placing the files in the correct locations for your system yourself. For instructions
on building the tarball, see next section.

BUILDING FROM SOURCE
--------------------
Prerequisites:

* Java 8 or higher
* Maven 3.3.3 or higher
* RPM

Steps:
    
    git clone https://github.com/DANS-KNAW/dd-easy-sword2-to-dataverse.git
    cd dd-easy-sword2-to-dataverse 
    mvn clean install

If the `rpm` executable is found at `/usr/local/bin/rpm`, the build profile that includes the RPM 
packaging will be activated. If `rpm` is available, but at a different path, then activate it by using
Maven's `-P` switch: `mvn -Pprm install`.

Alternatively, to build the tarball execute:

    mvn clean install assembly:single
