compare-locales
===============

This program creates stats and to-dos for localization projects.

In scope:
* Run compare-locales for de, it, fr for desktop, fennec, devtools on central
* Run multiple version of Fx in parallel (central, aurora, beta)
* Run compare-locales for www.mozilla.org for multiple locales (or a tool with similar output)
* Run compare-locales (or similar) for a gettext-based project
* Run compare-locales (or similar) on an XLIFF-based project

Out of scope:
* Run desktop and mozilla.org in parallel.
* Projects with multiple repositories per localization. Say, campaign with snippets and mozilla.org and a system add-on. We should stitch that on top.

Known requirements from desktop and thunderbird today:

* Spread various top-level directories
    mozilla-central/toolkit/locales/en-US
    comm-central/mail/locales/en-US
* Folded en-US dirs
    browser/locales/en-US
    browser/branding/official/en-US
* L10n structure different from en-US

Possible enhancements:
* Support for multiple occurrences of locale code.
    chrome/locales/en-US/browser/en-US/
* Single-file mappings
    en-US/firefox-ios.xliff
* POSIX locale codes (unicode?)
    en_BG/LC_MESSAGES/
