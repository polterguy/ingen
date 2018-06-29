
## Introduction to InGen

InGen is the name of the software system that the feature movie _"Jurassic Park"_ is using, and
this was the Software Requirement Specification (SRS) we were given in a programming contest I
was participating in. Since I found it to be an interesting use case, providing an example
implementation for an enterprise software system - I chose to continue working on it after
the programming contest was over, to refactor it and clean it up.

The system allows guests to browse exhibits, optionally purchase tickets for exhibits, in
addition to taking tours, which are guided tours based upon speech synthesis, using Google
Translate to translate from English to any language you wish to configure the system to use.
An employee can administrate tours, exhibits, and tickets. The system features strong support
for access control, allowing you to easily create access control to any individual parts of
the system, according to which roles your employees belongs to. Below is a screenshot of how
it looks like from the frontend, meaning what a guest in your Theme Park will see.

https://phosphorusfive.files.wordpress.com/2018/06/ingen-exhibits-help-screenshot.png

The system contains roughly 2,000 lines of code, is heavily commented, and illustrates
the following features from Phosphorus Five.

1. Speech synthesis
2. Usage of MySQL
3. Usage of the help system
4. Datagrids and other CRUD types of objects
5. Clean separation between UI and business logic
6. Modular thinking, allowing you to easily add new modules to the system
7. Access control according to user's role

### DRYness of system

The system is fairly _"DRY"_, but I have not made it so DRY that it is impossible to understand.
For instance, I could have made the system even more _"DRY"_ by creating one common datagrid
widget for all datagrids used in the system, but this would have made the code more difficult
to understand - And since the purpose of the system is to provide a reference implementation
of an enterprise software system for others, I felt this would be overkill, and defeat its
main purpose. _"DRY"_ implying _"Don't Repeat Yourself"_. At the same time, I have also tried
to create it fairly DRY, to illustrate Phosphorus Five's capacity in regards to these ideas.
For instance, the Exhibits and Tours datagrids of the system is implemented as a common
reusable datagrid, for both the frontend and the backend. However, the Tickets datagrid is
simply declared inline, directly into the module that loads it. This creates a simple example
use case for you that you can study to understand how to create MySQL datagrids in your own
systems - Which of course is the Tickets datagrid. While at the same time giving you hints
in regards to how you can continue to implement extremely DRY systems, by studying the Exhibits
and Tours modules.
