
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
the most important module.

#### Frontend exhibits plugins

The exhibit module has basic plugin support, allowing you to either append your own custom
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
          src:Clicked!
```

Whenever an exhibit is being viewed in your system, the above Active Event will be automatically
invoked, and whatever results it returns (if any), will be appended at the bottom of the
exhibit's main surface. Such frontend exhibits plugins are expected to return one or more
widget, since the results of such events, will be injected into the widget collection when
an exhibit is being viewed.

Basically, all Active Events in your system that starts with the name
**[ingen.exhibits.plugins.frontend.]** will be invoked and assumed to be frontend exhibits
plugins.

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
          src:Clicked!
```

While the frontend plugin system can actually handle any types of widgets, the backend
plugin system expects something that fits into a _"button strip"_, which implies a button,
select dropdown, or a text type of input widget.

### Tickets module

The tickets module serves as a plugin for the exhibits module, in addition to that it
has an administrative interface, only accessible for administrators of the system by default.
This module allows the user to purchase tickets to exhibits. The tickets module features
PayPal support for purchasing tickets, but this can be easily changed as you see fit.

### Tours module

This module allows a guest to take tours. Each exhibit in the system can have as many
tours as you wish. When a guest takes a tour, it will be automatically translated to
his language of choice, using Google Translate, for then to be spoken out loud using
speech synthesis. The idea with it, it to put QR codes around your Theme Park, for then
to allow guests to take guided tours using their own smart phones.

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
top/bottom sides.

### Settings module

This is a simple module that allows an administrator to edit his settings.

