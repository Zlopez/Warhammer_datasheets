# CA Design
This document contains Clean Architecture design for Warhammer_datasheet app. The Clean
Architecture design forbids use of the dependency injection. This means that the lower layer
shouldn't import anything from the higher layer. The layers are sorted like this from the lowest:

* Entities
* Use cases
* Controllers

There is exception for the Use cases which can use abstract classes from the Controllers layers. 
There are also Requests and Responses, these are used for communication of the outer world with
use cases.

## Entities
Entities are the core of the application, they represents models that the application
is working with.

### Model
This entity represents the model on datasheet. It contains **Name**, **Movement**,
**Weapon skill**, **Ballistic skill**, **Strength**, **Toughness**, **Wounds**,
**Attacks**, **Leadership**, **Saving throw**, **Point value**.

### Damage table
This entity represents damage table on datasheet. It contains **Name**, **Wounds range**,
**Movement**, **Weapon skill**, **Ballistic skill**, **Strength**, **Toughness**, **Wounds**,
**Attacks**, **Leadership**, **Saving throw**.

### Weapon
This entity represents weapon on datasheet. It contains **Name**, **Point value** and
list of weapon profiles.

### Weapon profile
This entity represents weapon profile. It contains **Name**, **Range**, **Type**, **Strength**,
**Armour piercing**, **Damage**, **Abilities**.

### Ability
This entity represents ability. It contains **Name**, **Aura**, **Description**.

### Datasheet
This entity represents unit datasheet. It contains **Name**, **Power level**,
**Battlefield role**, list of models with allowed number of them, list of damage tables,
**Additional info**, list of weapons, **Wargear options**, **Transport**, list of abilities,
list of faction keywords, list of keywords.

## Use Cases
Use cases represents the user use cases and their implementation.

### Create Database
This use case creates the new database.

### Load Database
This use case loads existing database.

### Save Database
This use case saves the provided database.

### Insert Update Datasheet
This use case represents the action for inserting new datasheet into DB or updating
the existing one. It will check if the entity exists in DB and then execute
appropriate action.

### Delete Datasheet
This use case deletes datasheet from the DB. It also removes any model entity attached to it.

### List Datasheets
This use case lists datasheets in DB and apply any requested filter.

### Insert Update Weapon
This use case represents the action for inserting new weapon into DB or updating
the existing one. It will check if the entity exists in DB and then execute
appropriate action.

### Delete Weapon
This use case deletes weapon from the DB.

### List Weapons
This use case lists weapons in DB and apply any requested filter.

### Insert Update Ability
This use case represents the action for inserting new ability into DB or updating
the existing one. It will check if the entity exists in DB and then execute
appropriate action.

### Delete Ability
This use case deletes ability from the DB.

### List Abilities
This use case lists abilities in DB and apply any requested filter.

## Controllers
Controllers represents wrappers for the third party libraries. This layer also contains
abstract classes that should be used by use case to communicate with the Controllers.

### DB
This is abstract class for database, it contains methods that should be implemented by every
other DB controller - Insert, Update, Delete, List, Create, Save, Load.

## Requests
Requests are used to communicate with use case, they are used to validate the input data
and provide us with unified communication channel for the use cases. There is one request for 
each use case. Each request has methods that are used to fill the request and method send, which
will sent the request.

## Responses
Each request sent to use case is followed by response. Response could be either Success or Failure.

### Response
Abstract class. Contains bool method that will return True if the use case was successful and False 
if there was any failure.

### Failure Response
Inherits from Response and adds error method, which returns the error encountered during use case.

### Success Response
Inherits from Response and adds data method, which returns the data retrieved if any. There is one
Success response class per use case.
