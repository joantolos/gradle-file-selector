# Gradle Producer - Consumer

## Goal

The goal for this POC is to learn about tasks and Groovy scripting with Gradle.

## Layout
  
There are two modules, producer and consumer:

* **Producer:** Creates random files with a timestamp included on the name, and store them into an output file.
* **Consumer:** Read the files which had been moved into the resources and log the file content on the console.

## Producer

There is a gradle task named **produceFiles** that creates the random files and store them into _/output_ folder

## Consumer

There is a gradle task named **consumeFile** that opens the _selected file_ and log the content on console. The files are located under it's own _/resources/input_ folder.

## Gradle task

The goal is to have a gradle task into the main module that will do all the work:

1. Use the producer module to create the files
1. Move the selected file from the producer output into the consumer input
  * The selected file is the latest one (using the timestamp on the name), that matches a name prefix
1. Use the consumer module to log the files content

## How to use it

    gradle process -Pstarting=File-Type-A
   
This execution examples does the following:
 
1. Generates a random number of files which names start with: _File-Type-A, File-Type-B and File-Type-C_
1. Then selects the latest generated one starting with _File-Type-A_ (the property for the gradle task) and moves it into the input folder of the consumer module.
1. The consumer module reads the file and print the content on console.