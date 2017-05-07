# Workflow Challenge

A common tool used in any organization that processes data is a workflow
manager. A workflow manager is a kind of system for executing multitudes of
tasks, often with interdependencies or failure modes. They come in all shapes
and sizes. Some are quite simple, perhaps using a declarative language to
repeat a specific task at a regular interval.  Others approach general purpose
programming languages, have sophisticated schedulers and can distribute tasks
over a multitude of computers.

Today we're going to attempt to write a simple workflow manager to do some
simple web scraping.

## Requirements

  * You may use whatever programming language you feel most comfortable with.
  * Submissions should include directions for how to compile, run and test the
    program as well as the source code.
  * You may use any packages in your languages standard library to complete the
    challenge.
  * Your submission should include tests.

## Workflow

The program you write should take an input file which describes a workflow. The
input file can be whatever you like, but it should be easily understandable and
editable by a human.

Within that file we're going to describe the following workflow:

  1. The first operation should be to fetch the document
     [here](https://raw.githubusercontent.com/enigma-io/workflow-interview-challenge/master/inventory.tsv).
  2. The TSV (Tab Delimited Values) document should be saved to disk as a JSON
     format file.
  3. The minimum, maximum and median values found in the third column should be
     saved to a separate JSON file.
  4. The final step should print the total number of bytes written to disk in
     steps 2 and 3.

## Responsibilities

You are expected to implement the core functionality of the workflow manager.
The tasks described in the workflow should be made available for all workflows
as a sort of standard library and can be implemented using other software
packages or modules. For instance: if you were using Python you might integrate
with the [requests](http://docs.python-requests.org/en/master/) library to
provide the first task's functionality.

The workflow manager should handle failures in any step by aborting the entire
workflow and exiting. An error describing what went wrong and what step was
being attempted should be printed to the console.

If the entire workflow completes successfully, the workflow manager should exit
indicating success.

The first operation described above requires network I/O and is thus more
likely to fail. To increase the likelihood that the workflow will succeed, the
manager should support a way to describe a number of retries. In this example
the first operation should be attempted three (3) times before giving up.

The second and third operations do not have to happen in any particular order
and this should be expressable to the workflow manager. With this knowledge the
workflow manager should attempt to run these steps in parallel.

The workflow should be idempotent, meaning that repeated attempts to execute
the workflow should product identical results and not complain about existing
files.
