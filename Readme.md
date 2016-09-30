Tech Roadmap
============

We're structuring the roadmap by the lifecycle of a localization project.

Project Management
------------------

- [ ] no downtime on project changes
- [ ] single source of truth of current and past projects
- [ ] a group maintains the set-up, no single source-of-failure

L12y
----

We strongly recommend to use [L20n](l20n/Readme.md) for all projects.

mozilla.org uses .lang files.

Other projects should use XLIFF, or even .po (gettext).

Dashboard
---------

- [ ] just ONE SINGLE dashboard
- [ ] response times should be quick
- [ ] support variety of file formats directly
    - [ ] ftl (l20n)
    - [ ] XLIFF
    - [ ] .po
    - [x] DTD
    - [x] .properties
    - [ ] .lang

Localization
------------

- [ ] all projects should be available in at least one translation tool

Projects
========

These are the projects we're working on right now, in addition to general bug
fixes.

- [ ] [land in gecko](https://github.com/Pike/cl-next/projects/2), used in Firefox and Firefox for Android.
- [ ] [elmo-pontoon merger](projects/toolchain-merger.md)
- [ ] [cross-channel firefox l10n](projects/cross-channel-fx.md)
