# Overview

Ever been disappointed at all the wasted robots when you conquer or integrate a Machine Intelligence?  This mod is for you!  Now you can de-assimilate the Machine Units into Robots once you have discovered the Positronic AI technology.

Now also featuring an enhancement for machine empires - robot Pops not also gain bonus trait points from the relevant machine-trait-point-boosting technologies and ascension perk.  Thus robot Pops will be just as useful as machine Pops to machine empires.

This mod removes the restriction on psionically assimilating cyborg pops.  They have enough organic bits left to become psionic - especially since the cybernetic species trait can be added to psionic species by default, cybernetic is compatible with brain slugs, and cybernetic is compatible with erudite.

# Changes

Enables "Gestalt Dissociation" assimilation living standard for Machine Unit Pops.  Hive Pops continue to be eligible for deassimilation with Evolutionary Mastery, but the living standard has been renamed to be more generic.  Updates the built-in assimilation mechanisms to understand this "new" (renamed and repurposed) assimilation type.

A new event window will display when you have Positronic AI and communications with a Machine Intelligence to tell you that machine deassimilation is available.

Overrides the robomodding series of technologies for machine empires (Machine Template System (machine), Binary Motivators, and Nanite Assemblers) and the Synthetic Age ascension perk to all grant both machine and robot trait points.

And last, but not least, cybernetic Pops can be psionically assimilated via Transcendence.

## Compatibility

Built for Stellaris version 3.4 "Cepheus."  Not compatible with achievements.

This mod has to alter a number of built-in files and objects to implement its gameplay.  Here's a list of of what is preempted/overridden and why:

* Ascension Perk `ap_synthetic_age` - Synthetic Age in order to grant trait points to both machines and robots
* Effect `assimilation_effect` - main assimilation logic (called by `action.65`), altered so that deassimilated machines are not converted into the synthetic species for fully synthetic empires, also code de-duped
* Event `action.64` - assimilation setup event, altered to allow machine deassimilation
* Event `action.65` - main assimilation event, altered to use less duplicate code and pass two variables to its effect calls - the current number of assimilated Pops and the total number allowed for the year
* Event `utopia.2551` - Synthetic Evolution, altered to not change synthetic leaders of other species into the empire's main species (cyborgs are still fair game, however)
* Citizenship `citizenship_assimilation` - assimilation citizenship, altered to allow machines to have this citizenship type (instead of only purge)
* Living Standard `living_standard_deassimilation` - deassimilation living standard, altered to be selectable for machines in regular empires that have researched Positronic AI, added alternate description for machine deassimilation versus hive deassimilation
* Living Standard `living_standard_tech_assimilation` - synth/cybernetic assimilation, altered to explicitly disallow this living standard for machines/robots
* Living Standard `living_standard_psi_assimilation` - psionic assimilation, altered to explicitly disallow this living standard for machines/robots
* Species Control `population_control_yes` - deassimilating machines must have population controls
* Species Control `population_control_no` - deassimilating machines are not allowed to reproduce
* Species Control `colonization_control_yes` - deassimilating machines mush have colonization controls
* Species Control `colonization_control_no` - deassimilating machines are not allowed to colonize
* Technology `tech_robomodding_m` - Machine Template System (machine) in order to grant trait points to both machines and robots
* Technology `tech_binary_motivators` - Binary Motivators in order to grant trait points to both machines and robots
* Technology `tech_nanite_assemblers` - Nanite Assemblers in order to grant trait points to both machines and robots

What this means to you is that this mod is not compatible with most other assimilation-altering mods and citizenship mods.  That is because its highly likely they are editing the same events and species rights.

This mod is explicitly compatible with my mod [Special Leadership Privileges for Battle Thralls and Bio-Trophies](https://steamcommunity.com/sharedfiles/filedetails/?id=2496357447) despite both mods affecting full military service.

### Recommended Companion Mods

* [Leader Traits: All Eligible Species Traits](https://steamcommunity.com/sharedfiles/filedetails/?id=2499031295) will ensure your leaders get all their species-based traits when being assimilated (such as Psionic or Erudite).
* [Leader Traits: Enhanced Randomisation](https://steamcommunity.com/sharedfiles/filedetails/?id=2553806265) improves leader trait randomisation (primarily from level up, but not exclusively) and toggles traits from the biological version to machine traits (and back) if a leader becomes a robot and/or returns to a biological form.
* [Retain Leaders from Integrated Subjects](https://steamcommunity.com/sharedfiles/filedetails/?id=2553818684) will allow you to keep Machine Unit leaders from integrated machine empire subjects by converting them to robots and setting their species to deassimilation.  Combined with Leader Traits: All Eligible Species Traits, the leaders are converted to have synth leader traits if you have the right technology.
* [corsairmarks's Leader Traits MOD Chinese patch](https://steamcommunity.com/sharedfiles/filedetails/?id=2558494770) by Hua Zhang - Chinese localisation

### When to Install

This mod can be safely added to your savegame after the game has started. It is implemented through events, effects, and species rights that alter game rules without adding object definitions. If you remove it, you will keep any machine Pops that have already been converted to robots, but any remaining machine Pops will probably revert to their default "disconnected machine" purge policy. Stellaris is fairly forgiving in situations like this - it's likely that error logs would be generated and the game would otherwise ignore the missing content. Back up your savegame before trying to remove a mod.

## Known Issues

This mod overwrites a number of core Stellaris game objects.  Expect to see seventeen errors in your error.log similar to these for many types of game object.  All are necessary to implement the functionality of this mod.

```
[15:38:58][technology.cpp:1176]: Duplicate technology: tech_robomodding_m
[15:38:58][technology.cpp:1176]: Duplicate technology: tech_binary_motivators
[15:38:58][technology.cpp:1176]: Duplicate technology: tech_nanite_assemblers
[15:38:58][game_singleobjectdatabase.h:147]: Object with key: assimilation_effect already exists, using the one at  file: common/scripted_effects/deassimilate_machines_overrides_scripted_effects.txt line: 2
[15:38:58][game_singleobjectdatabase.h:147]: Object with key: citizenship_assimilation already exists, using the one at  file: common/species_rights/01_deassimilate_machines_citizenship_types_overrides.txt line: 2
[15:38:58][game_singleobjectdatabase.h:147]: Object with key: living_standard_deassimilation already exists, using the one at  file: common/species_rights/02_deassimilate_machines_living_standards_overrides.txt line: 1
[15:38:58][game_singleobjectdatabase.h:147]: Object with key: living_standard_tech_assimilation already exists, using the one at  file: common/species_rights/02_deassimilate_machines_living_standards_overrides.txt line: 36
[15:38:58][game_singleobjectdatabase.h:147]: Object with key: living_standard_psi_assimilation already exists, using the one at  file: common/species_rights/02_deassimilate_machines_living_standards_overrides.txt line: 68
[15:38:58][game_singleobjectdatabase.h:147]: Object with key: military_service_full already exists, using the one at  file: common/species_rights/03_deassimilate_machines_military_service_overrides.txt line: 7
[15:38:58][game_singleobjectdatabase.h:147]: Object with key: population_control_yes already exists, using the one at  file: common/species_rights/06_deassimilate_machines_species_controls_overrides.txt line: 5
[15:38:58][game_singleobjectdatabase.h:147]: Object with key: population_control_no already exists, using the one at  file: common/species_rights/06_deassimilate_machines_species_controls_overrides.txt line: 69
[15:38:58][game_singleobjectdatabase.h:147]: Object with key: colonization_control_yes already exists, using the one at  file: common/species_rights/06_deassimilate_machines_species_controls_overrides.txt line: 114
[15:38:58][game_singleobjectdatabase.h:147]: Object with key: colonization_control_no already exists, using the one at  file: common/species_rights/06_deassimilate_machines_species_controls_overrides.txt line: 176
[15:38:59][eventmanager.cpp:361]: an event with id [action.64] already exists!  file: events/on_action_events_1.txt line: 8008
[15:38:59][eventmanager.cpp:361]: an event with id [action.65] already exists!  file: events/on_action_events_1.txt line: 8313
[15:39:00][eventmanager.cpp:361]: an event with id [utopia.2551] already exists!  file: events/utopia_on_action_events.txt line: 769
[15:39:00][game_singleobjectdatabase.h:147]: Object with key: ap_synthetic_age already exists, using the one at  file: common/ascension_perks/10_deassimilate_machines_ascension_perk_overrides.txt line: 2
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

## Source Code

Hosted on [GitHub](https://github.com/corsairmarks/deassimilate_machines)

### Development Notes

It is best to clone this repository into `<Stellaris User's Directory>/Paradox Interactive/Stellaris/mod`, and then make a connection to the `mod` folder via a `*.mod` file's `path` property.  That will ensure the game can see the files, and also that CWTools will parse them.  Also note that the README.md file exists in the `mod` directory but is symbolically linked in the root directory.