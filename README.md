# Format for Open Interactive Math Exercises

The goal of this repository to facilitate the development of a well-documented open import/export format for online, interactive math exercises.

## What is the purpose of this open file format?
The first purpose of this file format is to make it possible to export exercises created in Grasple to a text file, and to define the format in which exercises need to be written in order to automatically import them into Grasple. 

The longer term goal is to achieve interoperability between different practice and assessment platforms, by establishing a standard in which online interactive exercises that include math can be exchanged between different practice and assessment platforms. 

## How can I use this format?
You can use this format to write transformer scripts so that you can take a Grasple exercise and import it in another application, or write an import script so that you can transform an exercise from another application into an exercise that Grasple can run. 

It might well be that you run into issues where the features of these applications do not perfectly overlap. If you run into such issues, please let us know. This format is an attempt to make it easier to import and export learning resources between applications, to stimulate interoperability between educational applications. 

#### Do be aware! For now this is an experimental format, v0.0.1, so please be aware that things can and will change! 

## Where to start?

The first version of the format is defined using the [JSON Schema vocabulary](http://json-schema.org/) and is captured in the following schemas:

- [exercises.schema.json](./exercise.schema.json): the main schema for different type of exercises. You probably want to start here.
- [parameter.schema.json](./parameter.schema.json): a schema to define different types of parameters
- [content-types.schema.json](./content-types.schema.json): common definitions of types used in the other two schemas. 

#### Note: the current version of the format is `v0.0.1` and is published to sollicit feedback from the community. Please keep in mind that this format can (and most likely will) change in the future.

If you want you can look at some example exercises that are exported using the format described in the json schema's.
[Find the example exercises here](https://github.com/grasple/open-format-schemas/tree/main/examples)

## Providing feedback
If you have any feedback please feel free to create a pull request with proposed changes, create an issue with your feedback, or comment on [this commit](https://github.com/grasple/open-format-schemas/commit/76b6177c8d74227e33e79442d70ee7044016d9c8).

## What features are included in the format?
Some notable features in the format are:

- The possibility to compose a question of multiple sub questions
- The possibility to navigate through sub questions based on the correctness of previous answers
- Specifying  parameters are constructed as objects to describe their intention in one pre-defined format, instead of specifying parameters in code which can take many different forms. 

## Why is a standardised file format such as QTI not used?
The current standard for exercises in education is the Question and Test Interoperability specification (QTI), maintained by IMS Global. 
The latest production version is QTI 2.0

There are several advantages to using QTI, the most prominent being that it enjoys fairly wide support, facilitated by IMS Global, which is a world-wide consortium of educational organisations and vendors. 

However, there are also factors that limit the usability of the current QTI standard, specifically for math-related exercises. 
i) Most importantly, there is only limited support for math in QTI 2.0. There is no native LaTeX support and functionalities such as parametrization and answer rules that are very useful for math related fields, are not included in the 2.0 specification. 
ii) Furthermore, as QTI needs to support a wide variety of exercise types and applications, the standard is still quite loose, which leads to different interpretation and implementations of the specification, making automatic import difficult. 

Therefore, we want to define a specification that includes such features that are essential for math-related fields. 

## Why are the parameters specified like a configuration file instead of generated by code? 
An approach used by many practice and assessment platforms is to generate parameters using code (either using a self-developed language or an open coding language). 
The advantage of this approach is that there are lots of possibilities, and you are only constrained by the possibilities of the coding language.  

The advantage of less constraints also forms the downside to this approach. From our experience, code used to generate parameters in exercises can become quite complex. This complexity can lead to unwanted situations in which only a single person understands the code, or where small changes have many unintended consequences. 

An alternative approach is to specify the generation of parameters using a limited set of rules. By specifying parameters according to a strict set of rules it becomes easier to trace the origin of the value of parameters. Moreover, the use of one consistent format should make it easier to share exercises with others. 

Of course, this setup is open for debate and we hope to hear your feedback about it!

## Why a JSON and not XML format?
Both XML and JSON are frequently used on the web. XML has some great properties that make it work well for web documents. As a downside it can become quite hard to read. 
Although it is absolutely subjective, some people find JSON files easier to read. 
Both can be used. For now we’ve gone for JSON, but we’re open to hearing other opinions. In this debate we’re in favor of: ‘strong opinions, weakly held’. 
