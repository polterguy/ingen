
## Access control

Access to the system, and its sub-modules, can easily be controlled by using for instance
_"Peeples"_. The most important access object you highly likely want to create, is to
grant module access to all users. This can be done by adding the following access object
to your access object list.

```hyperlambda
*
  p5.module.allow:/modules/programming-contest/
```

Then you can open up for additional access to other parts of the system, based upon what
roles your users belongs to. If you have a role in your system called _"employee"_ for instance,
and you want to grant this role access to the Ticket system's backend parts, you can accomplish
that with the following access object.

```hyperlambda
superuser
  ingen.module.allow:/tickets/backend/
```

By default, all users, including the _"guest"_ user (randomly visiting user) have access to
all of your _"frontend"_ parts - While only a _"root"_ account have access to anything else.
By intelligently creating access objects, following the syntax of _"module-name/xxx-end"_,
where _"xxx-"_ is either _"frontend"_, _"backend"_ or _"common"_, you can easily grant or
deny access to specific parts of your system. The system will check if it has access to
evaluate files before evaluating them when a user tries to evaluate some file in the
system. If you create your own modules, you'll have to make sure yourself that you check
if the user has access to your module inside of your own code. See any of the pre-distributed
modules for examples of how to do this. Basically, there is a helper Active Event called
**[ingen.access.\_throw-if-no-access]** for this purpose, which will throw an exception
if a user tries to evaluate a file, in a module, he does not have access to.

When the system loads its Jumbo Buttons, it will check to see if the user
has access to the module, and only load the jumbo button(s) for your modules,
if access is granted.
