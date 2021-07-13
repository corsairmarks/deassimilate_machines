# Overview

Ever been disappointed at all the wasted robots when you conquer or integrate a Machine Intelligence?  This mod is for you!  Now you can de-assimilate the Machine Units into Robots once you have discovered the Positronic AI technology.

Oh, and this mod removes the restriction on psionically assimilating cyborg pops.  They have enough organic bits left to become psionic - epecially since the cybernetic species trait can be added to psionic species by default, cybernetic is compatible with brain slugs, and cybernetic is compatible with erudite.

# Changes

Enables "Gestalt Dissociation" assimilation living standard for Machine Unit Pops.  Hive Pops continue to be eligible for deassimilation with Evolutionary Mastery, but the living standard has been renamed to be more generic.  Updates the built-in assimilation mechanisms to understand this "new" (renamed and repurposed) assimilation type.

A new event window will display when you research Positronic AI to tell you that machine deassimilation is now available.

And last, but not least, cybernetic Pops can be psionically assimilated via Transcendence.

## Compatibility

This mod has to alter a number of built-in files and objects to implement its gameplay.  Here's a list of of what is preempted/overridden and why:

* Effect `assimilation_effect` - main assimilation logic (called by `action.65`), altered so that deassimilated machines are not converted into the synthetic species for fully synthetic empires, also code de-duped
* Event `action.64` - assimilation setup event, altered to allow machine deassimilation
* Event `action.65` - main assimilation event, altered to use less duplicate code and pass two variables to its effect calls - the current number of assimiliated Pops and the total number allowed for the year
* Event `utopia.2551` - Synthetic Evolution, altered to not change synthetic leaders of other species into the empire's main species (cyborgs are still fair game, however)
* Citizenship `citizenship_assimilation` - assimilation citizenship, altered to allow machines to have this citizenship type (instead of only purge)
* Living Standard `living_standard_deassimilation` - de-assimilation living standard, altered to be selectable for machines in regualr empires that has researched Positronic AI, added alternate description for machine deassimilation versus hive deassimilation
* Living Standard `living_standard_tech_assimilation` - synth/cybernetic assimilation, altered to explicitly disallow this living standard for machines/robots

What this means to you is that this mod is not compatible with most other ascension path mods.  That is because its highly likely they are editing the same events and species rights.

### Recommended Companion Mods

* [Enable All Eligible Species Traits for Leaders](https://steamcommunity.com/sharedfiles/filedetails/?id=2499031295) will ensure your leaders get all their species-based traits when being assimilated (such as Psionic or Erudite).
* [Leader Traits: Better Randomisation]() improves leader trait randomisation (primarily from level up, but not exclusively) and toggles traits from the biological version to machine traits (and back) if a leader becomes a robot and/or returns to a biological form.
* [Retain Leaders from Integrated Subjects]() will allow you to keep Machine Unit leaders from integrated machine empire subjects by converting them to robots and setting their species to deassimilation.  Combined with Enable All Eligible Species Traits for Leaders, the leaders are converted to have synth leader traits if you have the right technology.

### When to Install

This mod can be safely added to your savegame after the game has started. It is implemented through events, effects, and species rights that alter game rules without adding object definitions. If you remove it, you will keep any machine Pops that have already been converted to robots, but any remaining machine Pops will probably revert to their default "disconnected machine" purge policy. Stellaris is fairly forgiving in situations like this - it's likely that error logs would be generated and the game would otherwise ignore the missing content. Back up your savegame before trying to remove a mod.

## Known Issues

This mod overwrites a number of core Stellaris files.  Expect to see seven errors in your error.log similar to these:

```
[17:05:43][game_singleobjectdatabase.h:147]: Object with key: assimilation_effect already exists
[17:05:43][eventmanager.cpp:355]: an event with id [action.64] already exists!  file: events/on_action_events.txt line: 8009
[17:05:43][eventmanager.cpp:355]: an event with id [action.65] already exists!  file: events/on_action_events.txt line: 8302
[17:05:43][eventmanager.cpp:355]: an event with id [utopia.2551] already exists!  file: events/utopia_on_action_events.txt line: 767
[17:05:44][game_singleobjectdatabase.h:147]: Object with key: citizenship_assimilation already exists
[17:05:44][game_singleobjectdatabase.h:147]: Object with key: living_standard_deassimilation already exists
[17:05:44][game_singleobjectdatabase.h:147]: Object with key: living_standard_tech_assimilation already exists
```

There are an overridden effect, three preempted events, and three overridden species rights.  These are necessary to implement the functionality of this mod.

## Changelog

* 1.0.0 Initial version

## Source Code

Hosted on [GitHub]()

### Development Notes

It is best to clone this repository into `<Stellaris User's Directory>/Paradox Interactive/Stellaris/mod`, and then make a connection to the `mod` folder via a `*.mod` file's `path` property.  That will ensure the game can see the files, and also that CWTools will parse them.  Also note that the README.md file exists in the `mod` directory but is symbolically linked in the root directory.