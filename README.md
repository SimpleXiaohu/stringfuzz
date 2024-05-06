Description
===========

A collection of tools to manipulate and generate SMT-LIB 2.x problem instances.
There are four main tools:

- `stringfuzzg` to generate new instances
- `stringfuzzx` to transform existing instances
- `stringstats` to measure properties of instances
- `stringmerge` to merge several instances into one

Installing
==========

Clone this repository, and run this command inside it:

    python3 setup.py install

Running
=======

Without installing, the scripts can be run from the repository root as follows:

    python3 ./bin/stringfuzzg --help
    python3 ./bin/stringfuzzx --help
    python3 ./bin/stringstats --help

If installed, they can be run from anywhere as follows:

    stringfuzzg --help
    stringfuzzx --help
    stringstats --help

Examples
========

To create a problem with concats nested 100 levels deep:

    python3 ./bin/stringfuzzg concats --depth 100

To create the above problem and replace all characters with unprintable ones:

    python3 ./bin/stringfuzzg concats --depth 100 | python3 ./bin/stringfuzzx unprintable

To create and immediately feed a problem to Z3str3:

    python3 ./bin/stringfuzzg concats --depth 100 | z3str3 -in
