L20n
====

L20n is an implementation-independent specification for localization.

L20n implementations **MUST**
* use ftl as file format
* support multiple localizations at runtime
* fall back from failing strings to fallback localizations
* never error on the API level

L20n implementations **SHOULD**
* respond to language change requests instantly

As l10n-drivers team, we're currently developing a l20n implementation in
JavaScript with bindings to (X)HTML, XUL, XBL and browser-based JavaScript.

Other implementations are worked on independently, for example
in Rust and Java.
