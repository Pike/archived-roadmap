In-Tree Configuration example
=============================

```toml
basepath = "../.."

locales = [
    "en-x-testing"
]

default-locale = "en-US"

# Compare locales/en-US directories against directories in l10n
# Overlaps are allowed, but files in l10n need to uniquely map
# to one file in en-US
[[compare]]
# must not have a branding/official subdirectory, see below
source = "mail/locales/en-US/**"
target = "mail/**"

[[compare]]
# must not have a branding/official subdirectory, see below
source = "devtools/client/locales/en-US/**"
target = "devtools/client/**"
[[compare.repository]]
local = "../../mozilla"
name = "gecko"

[[include]]
file = "toolkit/locales/l10n.ini"
[[include.repository]]
local = "../../mozilla"  # common location to check out to
name = "gecko"  # system configs can specify where to find gecko
```
