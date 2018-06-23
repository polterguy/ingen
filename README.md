# InGen Theme Park system information

This system was the specification given to me and my opponent by the mods at
[/r/shittyprogramming](https://www.reddit.com/r/shittyprogramming/comments/8t2j1l/shittyprogramming_deathmatch_is_tonight_8pm_est/).
The idea was to implement a better IT system for a _"Jurassic Park"_ type of theme park, although
the system was named _"InGen"_ for copyright reasons. We were supposed to code for three hours, and
[here is how my implementation looked like when when we were finished](https://github.com/polterguy/programming-contest/tree/v1.1).

Since I thought it was a nice specification and use case for [Phosphorus Five](https://github.com/polterguy/phosphorusfive),
I chose to finish it after the contest was done, and implement a working example of a Theme Park
_"kiosk"_ system, intended to run on either fullscreen touch screen _"kiosks"_, and/or be launched
through usage of QR code. The system is created with the intentions of not being publicly
available on the general internet, but rather accessible through the LAN of some Theme Park.
It allows you to view the exhibits, and order tickets for such exhibits - In addition to that
it features a backend administrative dashboard, where an administrator can edit and manage
the exhibits and the system's parameters in general.

The original specification was heavily centered around _"Jurassic Park"_ problems, which if probably
not that useful for an actual system. So I chose to implement it after the contest was finished,
as a more general _"Theme Park"_ type of system. It features PayPal integrationfor accepting
payments, and allowing public visitors to browse the exhibitions of the theme park, to see what
type of exhibits they can join.

The system hence functions as a use case for what you can expect to be able to create with Phosphorus
Five and Hyperlambda. The system is rendered responsively, and runs just as well on phones and tablets,
as it does on Windows, Linux and OS X machines. Below is a screenshot of the system.

<img alt="Screenshot of the InGen Theme Park system" src="https://phosphorusfive.files.wordpress.com/2018/06/ingen-theme-park-kiosk-system.png" style="margin-left:auto;margin-right:auto;display:block;" />
