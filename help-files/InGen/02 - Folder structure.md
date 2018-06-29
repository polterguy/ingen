
## The folder structure of InGen

Hyperlambda has no OOP mechanisms, which I personally find to be one of its most interesting
features. This implies that instead of structuring the code into classes, namespaces and
types - Hyperlambda allows you to structure the code into files and folders, and such take
advantage of the file system to perform encapsulation and create modularity.

The main folder for InGen hence is the _"modules"_ folder. This folder contains all _"modules"_
that the system itself contains. An example of such a module can be the _"exhibits"_ module,
or the _"tours"_ module. This allows you to easily create new modules, by simply creating your
own module, and put it into the _"modules"_ folder of the main InGen app's folder. Each module
can have one ormore of the following folders.

* __backend__ - Intended for backend parts for your module
* __frontend__ - Intended for the frontend parts of your module
* __common__ - Intended for commonalities between the backend and the frontend

The frontend is what a random guest or visitor that is not logged into the system is supposed
to see, while the backend is for administrators and _"super users"_ in your system - Such
as employees in your Theme Park. The the common folder is for commonalities between the backend
and the frontend.

Your backend, frontend, and common folder again, can have a _"startup"_ folder. This folder
will have all of its Hyperlambda files automatically evaluated during installation, and/or
when the server (re) starts. Typically you'll find Active Events related to the module, and/or
extension widgets necessary to have the module function correctly here. In additions your
backend, frontend, and common folders can also optionally have a _"jumbo-buttons"_ folder,
which are Jumbo Buttons that are to be displayed on the main surface for the app. A Jumbo
Button is the large buttons you see when you initially start the app.

How you structure your module besides from the _"startup"_ folder(s) inside of your backend,
frontend, and common folders, is your own business - But the convention I'm using, is to
create one _"ui"_ folder, which is for the user interface parts - And a _"model"_ folder,
which is for your interaction with your database, and/or your business model. This allows
me to create a structure for my modules, that are surprisingly similar to a conventional
OOP structure, without OOP, and with much more easily understood code, while also making
it much easier to add new modules to the app in general. This allows you to (almost)
create an x-copy deployment for adding new sub-modules to your app.

Feel free to browse around the files/folder structure of the app with for instance Hyper IDE,
to become acquainted with its file and folder structure.
