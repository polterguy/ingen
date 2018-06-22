# Programming Contest

A programming contest initiated by the mods at [/r/shittyprogramming](https://www.reddit.com/r/shittyprogramming/comments/8t2j1l/shittyprogramming_deathmatch_is_tonight_8pm_est/).
The idea is to implement the best solution for a specification we're given in the shortest possible time frame.
Neither me nor [my opponent](https://github.com/fascinatedBox/) knows what we're supposed to implement,
and the contest will last for some 2-3 hours, streamed in front of a live audience.

[Read more about its details here](https://gaiasoul.com/2018/06/22/shitty-programming-death-match-tonight/).


## Specification

Introduction

### Purpose

This document describes requirements for a system to manage the day to day operations of a new InGen
project to create a theme park located on the island of Isla Nubar.  InGen prides itself on creating
unimaginable experiences for our guests and this should be reflected in our own management systems
internally as well as those which face our customers.

### Scope

InGen seeks to build a singular web based application with multiple views into the various sub-systems
which run the operations of the park.  These will include consoles for our security, operations and
research teams internally as well as ticket management and exhibit kiosks for our guests.

The system is mission critical and must be fast as well as secure.  Previous Unix based systems had
to be scrapped entirely due to massive security flaws in the architecture of the system.  The new
system must meet the strictest security concerns.

Most importantly the system will need to be well designed, look beautiful and delight guests of all ages.

### Description

#### Features

The system will be comprised of web based interfaces for Guests and Internal Employees.
Guest Facing systems will consist Kiosks which can run the Ticketing and Exhibit Information
applications.

Internal systems will have an interface that allow InGen Employees to view applications for Security,
Operations and Research.

#### System Features

#### Core System

The core system should allow employees to log in and select an internal application or run a kiosk.

#### Security

The security system should show the real-time status of security sub-systems and allow for management
of the systems where applicable.

#### Animal Paddocks

The Animal Paddock sub-system should allow for the monitoring and management of several animal
paddocks located throughout the island.

Animal Paddocks should include fields for:

* __Paddock Energy Status__ - To indicate if the Paddock is energized and working
* __Paddock Location__ - To show the physical location of the paddock on the island
* __Paddock Criticality__ - To show the criticality and potential danger of a failure

Animal Paddocks should include actions for:

* Enabling/Disable Paddock Energy
* Alerting the User if a _"Level 1"_ Criticality Paddock becomes de-energized unexpectedly

Animal Paddocks should show:

* A list of all entries
* A form to edit entries and fields
* A map of all paddocks and their energy states

#### Door Locks

The Door Locks sub system should show secure doors status as well as being able to remotely lock
and unlock the door.

Door Locks should include fields for:

* __Door location__ - To show the physical location of the door
* __Door Lock Status__ - To indicate if the door is locked or unlocked
* __Door Ajarness Level__ - To display the level of openess of the door.

Door Locks should include actions for:

* Remotely locking and unlocking the door
* Alerting the user if all doors become unlocked

Door locks display should contain views for:

* A list of all entries and fields
* A form to edit entries and fields
* A map displaying doors and their states

#### Security Cameras

The security cameras sub-system should show locations and image feeds of security cameras.

Security Cameras should include fields for:

* __Camera Location__ - To show the physical location of the camera

Security Cameras should contain views for:

* A list of all entries and fields
* A form to edit entries and fields
* An image based stream of the camera source

#### Operations

The operations sub-system should show a console that allows employees to monitor for potential
issues in park operations.

#### Weather

The weather sub-system should show an interface of current and predicted weather around Isla Nubar.
No information will be stored for this sub-system.

Weather should contain views for:

* A real time feed of weather information sourced from an external vendor.

#### Vehicle Tours

The park will employ a number of automated vehicles for tours of the island. The Vehicle Tours
system should manage and track these vehicles.

Vehicle Tours should include fields for:

* __Vehicle Information__ - Name, Make, Model and other fields to identify the vehicle
* __Vehicle Maintenance Status__ - To show whether the vehicle is active, reporting for maintenance on being maintained.
* __GPS Location__ - To show the real-time physical location of the vehicle on the island
* __Speed__ - To Track Vehicle Speed
* __Door Ajarness__ - To show if a door is open

Vehicle Tours should include actions for:

* Starting and stopping a vehicle tour
* Recalling a vehicle for maintenance

Vehicle Tours should contain views for:
* A list of all entries and fields
* A form to edit entries and fields

#### Research

Research systems should show information about experiments and lab procedures as well as relevant
information from associated IoT sensors.  These may include thermometers, gyroscopic, or other
biological sensors

#### Experiments

Experiments will show a list of experiments, as well as real-time information from sensors.

Experiments should include fields for:

* __Experiment information__ - Including Researcher names, experiment description, expected results, etc.
* __Sensor list__ - A list of IoT sensors and their end-point information

Experiments should contain views for:

* A list of all entries and fields
* A form to edit entries and fields
* An enhanced form view to show sensors and their information

#### Guest Systems

Guest Systems include all systems to manage systems used by guests as well as interfaces for the
guests themselves.

#### Ticketing

Ticketing will allow guests to purchase passes for exhibits as well as allow internal employees to
manage exhibits.

Ticketing should include fields for:

* __Exhibit information__ - To contain information about the various exhibits
* __Exhibit cost__ - The amount of money it costs
* __Exhibit times__

Ticketing should include actions for:

* Purchasing a quantity of tickets

Ticketing should contain views for:

* (Internal Only) A list of all entries and fields
* (Internal Only) A form to edit entries and fields
* Browsing exhibits and purchasing tickets (CRYPTO ONLY)

#### Exhibit Kiosks

Exhibit Kiosks are intended to provide information to guests for exhibits.  These kiosks are
available in the museum and walking portions of the part, NOT FOR ANIMAL PADDOCKS.  The system
will also allow internal employees to manage information for the kiosk.

Exhibit Kiosks should include fields for:

* __Kiosk Information__ - Including animal or display name, details

Exhibit Kiosks should contain views for:

* A list of all entries and fields
* A form to edit entries and fields
* Displaying static or interactive data on the kiosk

External Interfaces
Security Camera Feeds
Vehicle GPS
Laboratory Temperature Sensors
Weather
Paddock Fence

Non-functional Requirements

Appendix
Maps
