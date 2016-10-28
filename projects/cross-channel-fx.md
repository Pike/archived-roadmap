Cross-Channel Firefox Localization
==================================

We want to move the localization efforts from a localization per channel to
a localization that's good to use across all channels.

Right now, we have

|  | central | aurora | beta | release | ESR |
| --- | :---: | :---: | :---: | :---: | :---: |
| **af** |   | ✓ | ✓ | ✓ | - |
| **de** | ✓ | ✓ | ✓ | ✓ | - |
| **zu** |   | ✓ | ✓ | ✓ | - |

where each checkmark stands for a single mercurial repository, and a different
state of the localization.

We want to get to

<table>
<tr>
<td></td>
<th>central</th>
<th>aurora</th>
<th>beta</th>
<th>release</th>
<th>ESR</th>
</tr>
<tr>
<th>af</th>
<td align="center" colspan="5">✓</td>
</tr>
<tr>
<th>de</th>
<td align="center" colspan="5">✓</td>
</tr>
<tr>
<th>zu</th>
<td align="center" colspan="5">✓</td>
</tr>
</table>

i.e., there's only one repository for each locale, and that has all the strings
needed to ship any of Nightly, Aurora, Beta, Release, and even ESR if we so
choose.

There are two ways to implement this:

Keep Strings in en-US
---------------------

We change the development process of Firefox to not remove strings from the
en-US files when we stop using them on central. That way, strings still used
by older channels stay in the repository, and are continously exposed to
localizers. The corresponding l10n repositories can then easily be used to
build all versions of Firefox.

**Challenge**: We do want to remove strings not used anywhere no more. That
requires to actually find those strings. That's a surprisingly hard problem,
given the various programming languages, platforms, and APIs we use to
get to localized strings.

Synthesize a cross-channel en-US repository
-------------------------------------------

Alternatively, we can create a repository that holds the en-US strings, as a 
superset of all braches. We'd then use that "fake" repository to localize
Firefox, and continued to develop Firefox as we do today. In particular, strings
no longer used on central should be removed on central, and the removal would
ride the trains.

The file structure in this repository would also match that of the l10n
repositories, i.e., we'd strip all the `locales/en-US/` directory parts.

**Challenge**: Actually creating this repository isn't trivial. We'd need to
deal with blame, changes in configuration files after the fact, and we'd want
stable sorting of entities in case of back-outs.

**Pros**:
* There's a long-standing ask for a en-US-only repository by localizers and
tool authors.
* In the first scenario, we'd still want to run statistics and reports on the
state of the localization against beta, and that'd suggest strings and files to
be removed that are not in beta.

Next Experiment
---------------

We should try and see how a synthesized repo looks like and feels. Axel would
like to see an experiment to create that repo, going back to what's currently
ESR, aka 45, and roll the version control system forward, with the created
branches from there.

- [X] initial blame for 45 at merge day to aurora
- [ ] rolling forward central 46 and aurora 45
- [ ] rolling forward 47, 46, 45
- [ ] rolling forward 48, 47, 46, 45
- [ ] rolling forward 49, 48, 47, 46, 45
- [ ] rolling forward 50, 49, 48, 47, 45
- [ ] rinse and repeat 'til 52, aka, today.
