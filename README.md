# InGen Dinosaur Theme Park Software System

This system was the specification given to me and my opponent by the mods at
[/r/shittyprogramming](https://www.reddit.com/r/shittyprogramming/comments/8t2j1l/shittyprogramming_deathmatch_is_tonight_8pm_est/)
in a programming contest that was held in June of 2018. The idea was to implement a better IT
system for a _"Jurassic Park"_ type of theme park. We were supposed to code for three hours, and
[here is how my implementation looked like when when we were finished](https://github.com/polterguy/ingen/tree/v1.1).


<p align="center">
<a href="https://www.youtube.com/watch?v=i82lruH0f8I">
<img alt="The InGen Dinosaur Theme Park Software System" title="The InGen Dinosaur Theme Park Software System" src="https://phosphorusfive.files.wordpress.com/2018/06/screen-shot-2018-06-23-at-21-37-22.png" />
</a>
</p>


Since I thought it was a nice specification and use case for [Phosphorus Five](https://github.com/polterguy/phosphorusfive),
I finished it after the contest was done, and implemented a working example of a Theme Park
_"kiosk"_ system, intended to run on either fullscreen touch screen _"kiosks"_, and/or be launched
through usage of QR codes inside a Theme Park. The system is created with the intentions of not being publicly
available on the general internet, but rather accessible through the LAN of some Theme Park.
It allows you to view the exhibits, and order tickets for such exhibits - In addition to that
it features a backend administrative dashboard, where an administrator can edit and manage
the exhibits and the system's parameters in general.

The original specification was heavily centered around _"Jurassic Park"_ problems, which is probably
not that useful for an actual system. So I chose to implement it after the contest was finished,
as a more general _"Theme Park"_ type of system. It features PayPal integration for accepting
payments, and allowing public visitors to browse the exhibitions of the theme park, to see what
type of exhibits they can sign up for. In addition, it allows the guests to take _"guided tours"_
in the theme park, launched through QR codes, which will use speech synthesis and Google Translate
such that a guest can use his smartphone and headset to get information about the exhibits he
is visiting.

The system hence functions as a use case for what you can expect to be able to create with Phosphorus
Five and Hyperlambda. The system is rendered responsively, and runs just as well on phones and tablets,
as it does on Windows, Linux and OS X machines. The system is heavily modularised, and allows for
creating extension modules easily. Its intentions is to serve as an example _"use case"_ for
Phosphorus Five.

## Installation

1. [Download and install Phosphorus Five](https://github.com/polterguy/phosphorusfive).
2. [Download InGen's Zip file](https://github.com/polterguy/ingen/releases).
3. Install the InGen ZIP file through the _"Desktop"_ module of Phosphorus Five, by clicking the upload button.
