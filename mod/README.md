**_IMPORTANT UPDATE:_** This mod is no longer required for [Assimilate All the Pops](https://steamcommunity.com/sharedfiles/filedetails/?id=2908463208). Additionally, the synthetic evolution improvements have also been moved to Assimilate All the Pops! (your initial synthetic species will have traits similar to your previous organic species).

# Overview

Ever been disappointed at all the wasted Pops when you conquer or integrate a Machine Intelligence?  This mod is for you!  Now you can de-assimilate the Machine Units into Robots once you have discovered the Positronic AI technology.

This mod also features an enhancement for machine empires - robot Pops also gain bonus trait picks and points from the machine-boosting relevant technologies and traditions.  Thus robot Pops will be just as useful as machine Pops to machine empires.

# Changes

Adds the "Machine Dissociation" assimilation living standard for Machine Unit Pops. Coupled with an override of the "Assimilation" citizenship, this enables you to convert machines into robots as a regular, non-gestalt empire (as long as you have Positronic AI).

An event window will display when you have Positronic AI and communications with a Machine Intelligence to tell you that machine deassimilation is available.

Overrides the robomodding series of technologies for machine empires (Machine Template System, Binary Motivators, and Nanite Assemblers), the Synthetic Age tradition, and the Solid State Actuators tradition to grant both machine and robot trait picks/points.

## Compatibility

Built for Stellaris version 3.7 "Canis Minor."  Not compatible with achievements.

This mod has to alter a number of built-in game objects to implement its gameplay.  Here's a list of of what is overridden and why:

* Effect `assimilation_effect` - main assimilation logic (called by `action.65`), altered so that deassimilated machines are not converted into the synthetic species for fully synthetic empires, also code de-duped
* Citizenship `citizenship_assimilation` - Assimilation, altered to allow machines to be deassimilated by non-gestalt empires
* Species Population Control `population_control_yes` - deassimilating machines must have population controls
* Species Population Control `population_control_no` - deassimilating machines are not allowed to reproduce
* Species Colonization Control `colonization_control_yes` - deassimilating machines must have colonization controls
* Species Colonization Control `colonization_control_no` - deassimilating machines are not allowed to colonize
* Technology `tech_robomodding_m` - Machine Template System in order to grant machine empires trait points to both machines and robots
* Technology `tech_binary_motivators` - Binary Motivators in order to grant machine empires trait points to both machines and robots
* Technology `tech_nanite_assemblers` - Nanite Assemblers in order to grant machine empires trait points to both machines and robots
* Tradition `tr_synthetics_synthetic_age` - Synthetic Age in order to grant machine empires trait picks for both machines and robots
* Tradition `tr_synthetics_solid_state_actuators` - Solid State Actuators in order to grant machine empires trait points for both machines and robots

This mod is explicitly compatible with all of my other mods, including those that also modify assimilation or other species rights.

### When to Install

This mod can be safely added to your savegame after the game has started. It is implemented through events, effects, and species rights that alter game rules without adding object definitions. If you remove it, you will keep any machine Pops that have already been converted to robots, but any remaining machine Pops will probably revert to their default "disconnected machine" purge policy. Stellaris is fairly forgiving in situations like this - it's likely that error logs would be generated and the game would otherwise ignore the missing content. Back up your savegame before trying to remove a mod.

### Recommended Companion Mods

* [Assimilate All the Pops](https://steamcommunity.com/sharedfiles/filedetails/?id=2908463208) allows empires to have multiple assimilation types - go forth and create those erudite, psionic cyborgs
* [Leader Traits: All Eligible Species Traits](https://steamcommunity.com/sharedfiles/filedetails/?id=2499031295) will ensure your leaders get all their species-based traits when being assimilated (such as Psionic or Erudite)
* [Leader Traits: Enhanced Randomisation](https://steamcommunity.com/sharedfiles/filedetails/?id=2553806265) improves leader trait randomisation (primarily from level up, but not exclusively) and toggles traits from the biological version to machine traits (and back) if a leader becomes a robot and/or returns to a biological form
* [Retain Leaders from Integrated Subjects](https://steamcommunity.com/sharedfiles/filedetails/?id=2553818684) will allow you to keep Machine Unit leaders from integrated machine empire subjects by converting them to robots and setting their species to deassimilation; combined with Leader Traits: All Eligible Species Traits, the leaders are converted to have synth leader traits if you have the right technology
* [corsairmarks's Leader Traits MOD Chinese patch](https://steamcommunity.com/sharedfiles/filedetails/?id=2558494770) by Hua Zhang - Chinese localisation

## Known Issues

This mod overwrites several core Stellaris game objects.  Expect to see eight errors in your error.log similar to these.  All are necessary to implement the functionality of this mod.

```
[03:46:46][technology.cpp:1154]: Duplicate technology: tech_robomodding_m
[03:46:46][technology.cpp:1154]: Duplicate technology: tech_binary_motivators
[03:46:46][technology.cpp:1154]: Duplicate technology: tech_nanite_assemblers
[03:46:47][game_singleobjectdatabase.h:165]: Object with key: assimilation_effect already exists, using the one at  file: common/scripted_effects/deassimilate_machines_scripted_effect_overrides.txt line: 6
[03:46:47][game_singleobjectdatabase.h:165]: Object with key: citizenship_assimilation already exists, using the one at  file: common/species_rights/citizenship_types/10_deassimilate_machines_citizenship_type_overrides.txt line: 6
[03:46:47][game_singleobjectdatabase.h:165]: Object with key: military_service_full already exists, using the one at  file: common/species_rights/military_service_types/10_deassimilate_machines_military_service_overrides.txt line: 11
[03:46:50][game_singleobjectdatabase.h:165]: Object with key: tr_synthetics_synthetic_age already exists, using the one at  file: common/traditions/11_deassimilate_machines_synthetics_traditions_overrides.txt line: 2
[03:46:50][game_singleobjectdatabase.h:165]: Object with key: tr_synthetics_solid_state_actuators already exists, using the one at  file: common/traditions/11_deassimilate_machines_synthetics_traditions_overrides.txt line: 70
```

## Changelog

* 1.0.0 Initial version
* 1.0.1 Support updated flag from Full Military Service for Battle Thralls (now known as Special Leadership Privileges for Battle Thralls and Bio-Trophies)
* 1.0.2 Support Gestalt Dissociation when the player also has Transcendence (psionic assimilation)
* 1.0.3 Code refactoring - no functionality changes
* 1.1.0 Update for Stellaris version 3.1 "Lem" - no changes to what the mod does, just integrated a few minor underlying game changes
* 2.0.0 Update for Stellaris version 3.2 "Herbert"
    * Synthetic Age override accounts for Aquatic robots
* 3.0.0 Update for Stellaris version 3.3 "Libra" - no changes to what the mod does, just integrated a few minor underlying game changes
* 3.1.0 Override game objects that grant MACHINE trait points, in order to have them grant the same amount of ROBOT trait points
    * 3 technologies: Machine Template System (machine version), Binary Motivators, and Nanite Assemblers
    * 1 ascension perk: Synthetic Age
* 4.0.0 Update for Stellaris version 3.4 "Cepheus"
    * Use memory optimization feature for effects and triggers
    * Update code to account for hired (mercenary) fleets
* 4.1.0 Code refinement for more precise checks
* 5.0.0 Update for Stellaris version 3.6 "Orion" (and changes from version 3.5 "Fornax")
    * Integrate underlying game changes
    * Paradox has refined Psionics and Cybernetics to be mutually exclusive - you can assimilate between types, but Psionic removes Cybernetic and vice versa
    * Remove override of Synthetic Age ascension perk - it no longer affects MACHINE/ROBOT trait points
    * Add overrides of two Synthetics traditions in order to provide MACHINE and ROBOT bonuses for machine Empires
    * Refactor `species_rights` overrides to follow new file paths
    * Creating a brand-new living standard for Machine Dissociation instead of using a workaround with the existing living standard Hive Dissociation
    * No longer requires Utopia (but still requires Synthetic Dawn)
* 5.0.1 Fix bug which caused each year deassimilating machines to create a new mechanical species, rather than finding the existing one
* 6.0.0 Add support for Civic: Organic Zealots
    * Add a compatibility trigger for other mods to check whether this one is active
    * Consume the compatibility triggers from other mods
    * Remove old compatibility global flag
* 7.0.0 Move assimilation overhaul (for multi-assimilation) to the more appropriate mod, [Assimilate All the Pops](https://steamcommunity.com/sharedfiles/filedetails/?id=2908463208)
    * This mod is now more compatible with other mods due to fewer overwrites
    * Support cybernetic deassimilation from Civic: Organic Zealots
* 7.0.1 Bugfix: adjust `tr_synthetics_synthetic_age` to account for possible restrictions from Civic: Organic Zealots, courtesy of reporting by [MrFunEGUY](https://steamcommunity.com/profiles/76561198025143641/myworkshopfiles/?appid=281990)
* 7.0.2 Bugfix: machine deassimilation was not allowed after an empire gained access different form of assimilation - thanks [wagnerleung0079](https://steamcommunity.com/profiles/76561198261183621)
* 8.0.0 Update for Stellaris version 3.7 "Canis Minor" - integrated underlying game changes

## Source Code

Hosted on [GitHub](https://github.com/corsairmarks/deassimilate_machines)

### Development Notes

It is best to clone this repository into `<Stellaris User's Directory>/Paradox Interactive/Stellaris/mod`, and then make a connection to the `mod` folder via a `*.mod` file's `path` property.  That will ensure the game can see the files, and also that CWTools will parse them.  Also note that the README.md file exists in the `mod` directory but is symbolically linked in the root directory.