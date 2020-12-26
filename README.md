# Warhammer Datasheets
This repository contains Warhammer datasheets in open document spreadsheet format.

## Repository structure
The repository follows structure divided by game, edition and faction. See bellow
tree for example.

```
root
+-- Warhammer_40k
|   +-- 9th_edition
|       +-- Necrons.ods
+-- W40k_Kill_team
    +-- 1st_edition
        +-- Space_marines.ods
```

## Document format structure
The documents have different structure based on the game they are created for.

### Warhammer 40k
The standard Warhammer 40k faction document has the following sheets:

* Units
This sheet contains data about units **Name**, **Army faction**, **Power Level**,
**Battlefield role**, **Wargear options**, **Transport**

* Models
This sheet contains data about models **Name**, **Point value**

* Model profiles
This sheet contains model profiles **Movement**, **Weapon skill**,
**Ballistic skill**, **Strength**, **Toughness**, **Wounds**, **Attacks**, **Leadership**,
**Saving throw**  
Most of the units have only one profile, but this is useful for damage tables.

* Abilities
This sheet contains data about abilities **Name**, **Aura**, **Description**

* Weapons
This sheet contains data about weapons **Name**, **Point value**

* Weapon profiles
This sheet contains weapon profiles **Range**, **Type**, **Strength**,
**Armour piercing**, **Damage**, **Abilities**

* Wargear
This sheet contains wargear other than weapons **Name**, **Description**, **Point value**

* Keywords
This sheet contains list of keywords **Keyword**, **Faction**

* Models_Units
This sheet contains map of models to units **Unit**, **Model**, **Minimum size**

* Weapons_Models
This sheet contains map of weapons to models **Model**, **Weapon**

* Profiles_Models
This sheet contains map of profiles to models **Model**, **Model profile**

* Profiles_Weapons
This sheet contains map of profiles to weapons **Weapon**, **Weapon profile**

* Abilities_Units
This sheet contains map of abilities to units **Unit**, **Ability**

* Wargear_Units
This sheet contains map of wargear to units **Unit**, **Wargear**

* Keywords_Units
This sheet contains map of keywords to units **Unit**, **Keyword**
