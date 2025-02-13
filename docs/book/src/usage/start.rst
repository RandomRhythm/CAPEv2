===============
Starting CAPE
===============

Make sure to run it inside CAPE's root directory::

    $ cd /opt/CAPEv2

To start CAPE, use the command::

    $ python3 cuckoo.py

You will get an output similar to this::

    Cuckoo Sandbox 2.1-CAPE
    www.cuckoosandbox.org
    Copyright (c) 2010-2015

    CAPE: Config and Payload Extraction
    github.com/kevoreilly/CAPEv2

    2020-07-06 10:24:38,490 [lib.cuckoo.core.scheduler] INFO: Using "kvm" machine manager with max_analysis_count=0, max_machines_count=10, and max_vmstartup_count=10
    2020-07-06 10:24:38,552 [lib.cuckoo.core.scheduler] INFO: Loaded 100 machine/s
    2020-07-06 10:24:38,571 [lib.cuckoo.core.scheduler] INFO: Waiting for analysis tasks.

Now CAPE is ready to run and it's waiting for submissions.

``cuckoo.py`` accepts some command line options as shown by the help::

        usage: cuckoo.py [-h] [-q] [-d] [-v] [-a] [-t] [-m MAX_ANALYSIS_COUNT]

        optional arguments:
        -h, --help            show this help message and exit
        -q, --quiet           Display only error messages
        -d, --debug           Display debug messages
        -v, --version         show program's version number and exit
        -a, --artwork         Show artwork
        -t, --test            Test startup
        -m MAX_ANALYSIS_COUNT, --max-analysis-count MAX_ANALYSIS_COUNT
                                Maximum number of analyses

Most importantly ``--debug`` and ``--quiet`` respectively increase and decrease the logging verbosity.

======================================================
Starting processing data generated by virtual machine
======================================================

See ``-h`` for all latest options, for better customization::

        usage: process.py [-h] [-c] [-d] [-r] [-s] [-p PARALLEL] [-fp] [-mc MAXTASKSPERCHILD] [-md] [-pt PROCESSING_TIMEOUT] id

        positional arguments:
        id                    ID of the analysis to process (auto for continuous processing of unprocessed tasks).

        optional arguments:
        -h, --help            show this help message and exit
        -c, --caperesubmit    Allow CAPE resubmit processing.
        -d, --debug           Display debug messages
        -r, --report          Re-generate report
        -s, --signatures      Re-execute signatures on the report
        -p PARALLEL, --parallel PARALLEL
                                Number of parallel threads to use (auto mode only).
        -fp, --failed-processing
                                reprocess failed processing
        -mc MAXTASKSPERCHILD, --maxtasksperchild MAXTASKSPERCHILD
                                Max children tasks per worker
        -md, --memory-debugging
                                Enable logging garbage collection related info
        -pt PROCESSING_TIMEOUT, --processing-timeout PROCESSING_TIMEOUT
                                Max amount of time spent in processing before we fail a task

$ python3 utils/process.py -p7 auto
