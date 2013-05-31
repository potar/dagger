Introduction
============

Developers have a lot of work when trying to repeat complex errors which tend to occur on Plone production site so I decided to create  a so-called `dagger` (three packages that help you do it much faster) -  a tool for a Plone developer.

Structure
---------

As I mentioned, it includes three packages:

* `collective.error.detector` - https://github.com/potar/collective.error.detector
* `collective.request.player` - https://github.com/potar/collective.request.player
* `collective.recipe.logger` - https://github.com/potar/collective.recipe.logger

These packages are stand-alone products, so you can use them separately from the `dagger`.

How it works
------------

The main idea is that collective.error.detector gets requests and sends them to collective.recipe.logger, 
then a super user gets the logs of requests and replays them on a devel configuration.

Usage
-----

You have to do several steps:

1. Install `collective.recipe.logger` onto your production site.

2. Run the program daemon and check its status. E.g.:

    -  ``$bin/logger start``
    -  ``$bin/logger status``

3. Install `collective.error.detector` into your production site.

4. Get the requests logs (``parts/logger/storage``) and replay them on non-production configuration. 
   It may be another buildout configuration or you can create an appropriate zeoclient.zeoclient.

You can use the buildout options (`demo-storage` and `before-storage`) for replaying requests better.

Requirements
------------

* Plone 4.0
* Plone 4.1
* Plone 4.2

Author
------
Taras Poburynnyi
