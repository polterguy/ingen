## General architecture

Out of the box the system contains 5 core modules, these are listed below.

* Exhibits
* Tickets
* Tours
* Images
* Settings

### Exhibits module

This is the main module in the system, and allows guests to browse exhibits, and optionally
if the ticket module is enabled, also allows guests to purchase tickets to specific exhibits.
The exhibits module is kind of like a _"micro CMS"_, and allows an administrator or employee
to edit the exhibits in the system, using a basic Markdown editor, with support for embedding
YouTube videoes and images. The exhibits module is kind of the _"core"_ of the system, and
the most important module. The exhibits module features strong plugin support, both in its
backend, and in its frontend parts.

#### Frontend exhibits plugins

The exhibit module has strong plugin support, allowing you to either append your own custom
widgets to an exhibit as it is being viewed by a guest - In addition to that it allows you
to create your own custom plugin buttons which will be appended into the editor as an
exhibit is being edited. Both the tickets module and the images module takes advantage of
this, and actually serves as plugins to exhibits. If you'd like to create your own frontend
plugin for viewing an exhibit, you can accomplish that with something resembling the following.

```hyperlambda
/*
 * Creates a frontend exhibit plugin.
 *
 * This just creates a simple button, which once clicked, changes its text.
 */
create-event:ingen.exhibits.plugins.frontend.frontend-plugin
  return
    button
      innerValue:Click me!
      onclick
        set-widget-property:x:/../*/_event?value
          innerValue:Clicked!
```

Whenever an exhibit is being viewed in your system, the above Active Event will be automatically
invoked, and whatever results it returns (if any), will be appended at the bottom of the
exhibit's main surface. Such frontend exhibits plugins are expected to return one or more
widgets, since the results of such events, will be injected into the widget collection when
an exhibit is being viewed.

Basically, all Active Events in your system that starts with the name
**[ingen.exhibits.plugins.frontend.]** will be invoked and assumed to be frontend exhibits
plugins. The last `frontend-plugin` part of your Active Event should be a unique and
descriptive name for your plugin.

#### Backend exhibits plugins

To create a backend exhibit editor plugin, you can create an active event like the following
illustrates.

```hyperlambda
/*
 * Creates a backend exhibit plugin.
 *
 * This just creates a simple button, which once clicked, changes its text.
 */
create-event:ingen.exhibits.plugins.editor.backend-plugin
  return
    button
      innerValue:Click me!
      onclick
        set-widget-property:x:/../*/_event?value
          innerValue:Clicked!
```

While the frontend plugin system can actually handle any types of widgets, the backend
plugin system expects something that fits into a _"button strip"_, which implies a button,
select dropdown, or a text type of input widget. Normally I'd say only a button is an
adequate plugin type here though, but feel free to experiment if you wish.

### Tickets module

The tickets module serves as a plugin for the exhibits module, in addition to that it
has an administrative interface, only accessible for administrators of the system by default.
This module allows the user to purchase tickets to exhibits. The tickets module features
PayPal support for purchasing tickets, but this can be easily changed as you see fit.
An administrator can through its backend accept tickets and mark these as _"used"_.

When a guest orders tickets, the system will by default ask the guest to sign up for
the Theme Park's marketing newsletter, collecting the customer's email address in the
process.

### Tours module

This module allows a guest to take tours. Each exhibit in the system can have as many
tours as you wish. When a guest takes a tour, it will be automatically translated to
his language of choice, using Google Translate, for then to be spoken out loud using
speech synthesis. The idea with it, is to put QR codes around your Theme Park, for then
to allow guests to take guided tours, using their own smart phones and headsets.

### Images module

This module serves only as a plugin for the backend parts of the exhibits editor, and allows
an administrator to select an image, to embed into the Markdown as he is editing his exhibit.
Notice, this module has one interesting Active Event called **[ingen.imaging.\_auto-crop-resize]**.
This event is consumed such that it creates 3 versions of each image you upload.

* 800x600 pixels
* 600x300 pixels
* 160x120 pixels

All images are automatically cropped to the above 4/3 ratio when an image is uploaded. A
process that might include clipping the image, either at its left/right sides, or at its
top/bottom sides. The images can be found in your _"/ingen/media/images/"_ folder in your
installation. Beneath this folder are the _"medium"_ folder and the _"thumbs"_ folder
for medium sized images and small images. The large images are stored directly into the main
_"images"_ folder. However, the system will automatically administrate its images, and
delete the correct files, if you choose to delete an image.

### Settings module

This is a simple module that allows an administrator to edit his settings. Also the settings
module allows you to easily create plugins, which will be automatically injected into the
settings form, when an administrator chooses to view or edit the settings of the system.
These Active Event are expected to start out with **[ingen.settings.plugins.]**, for then
to have some unique and descriptive name at the end of them. Such Active Events are expected
to return a widget or a collection of widget, that will be injected into the settings form,
when the form is loaded. Below is an example that will create a checkbox in the settings
form for you.

```hyperlambda
create-event:ingen.settings.plugins.foo-bar

  /*
   * Returning widget necessary to include settings checkbox for
   * the "foo bar" widget in the settings module.
   */
  return
    label
      widgets
        input
          type:checkbox
          .data-field:ingen.settings.foo-bar-module
          oninit

            /*
             * Checking if foo bar module is turned on.
             */
            select-data:x:/*/*/ingen.settings.foo-bar-module
            if:x:/-/*/*?value
              =:bool:true
              set-widget-property:x:/../*/_event?value
                checked

        span
          innerValue:Foo bar
```

The above will create a checkbox for a _"Foo bar"_ module, allowing an administrator to
change its value. Notice, all settings will be automatically saved in the p5.data database
when the settings form is saved, with the name of the node being the **[.data-field]**
value. The above settings type for instance can be retrieved using the following code
from within your _"Foo bar"_ module.

```hyperlambda
/*
 * Selects the "Foo bar" module's checkbox setting.
 */
select-data:x:/*/*/ingen.settings.foo-bar-module
```

Out of the box the system contains 3 different settings.

* CSS skin file to use
* Whether or not the tickets module is enabled
* Whether or not a guest can browse tours without accessing tours through a direct link

All of the above are Active Events that are declared in the relevant parts of the system,
that returns plugins to the settings module's UI.
