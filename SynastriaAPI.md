# Synastria Server API
Documentation of the native server API available on the client side.
Consider using the helper functions in SynastriaCoreLib that takes care of a lot of error checking and such for you.

# General
## Types

### CustomGameDataType
| Name              | Value |
|-------------------|-------|
| PERK_ACQUIRED     | 1     |
| PERK_LIMIT        | 2     |
| PERK_ACTIVE       | 3     |
| PERK_PROG         | 4     |
| PERK_TASKASSIGN1  | 6     |
| PERK_TASKASSIGN2  | 7     |
| PERK_TASKPARTY    | 9     |
| PERK_OPTIONS      | 10    |
| ATTUNE_HAS        | 11    |
| MYTHIC_SELECT     | 12    |
| RESOURCE_BANK     | 13    |
| RESOURCE_LAST     | 14    |
| ATTUNE_RANDOMPROP | 15    |

## Consts
| Name              | Value                            |
|-------------------|----------------------------------|
| MAX_ITEMID        | (current max itemId in the game) |

## Functions
### GetCustomGameDataCount(typeId) -> int
### GetCustomGameDataIndex(typeId, index) -> int|string
### GetCustomGameData(typeId, index) -> int|float
### GetItemInfoCustom(itemId) -> ...|nil
### GetItemExtraCustom(itemId) -> nil|
### CustomGetRaceId() -> int
### CustomGetClassId() -> int
### CustomIsClassMask(mask) -> bool
### GetItemTagsCustom(itemId) -> int, ...

### OpenAttuneSummary()
Opens the attunement window. Note that the stats are not refreshed when the window is opened this way! To refresh the attunement stats, you have to use the spell

### OpenPerkMgr()
Opens the Perk manager window

### OpenResourceSummary()
Opens the Resource Bank window


## Events
Important! Before defining any event handler function, you should store any existing reference and make sure you call it first thing in your function. Otherwise, other addons depending on said event will break!

### OnCustomGameData(typeId, id, prev, cur)
Called at the start of sending data to the client

### OnCustomGameDataFinish()
Called after the transaction is finished and all data is available

### OnCustomGameInit()
Called after initializing the custom data the first time, for example after login


# Attunables
## Tables
### ~~ItemAttuneSkip~~
Used to contain information about unattunable items

### ItemAttuneStats
Contains key/val pairs for attunable stats for an item. Note! Only populated after the attunement summary window has been opened, and is probably not intended for use.

### ItemAttuneOverwrite
Contains key/val pairs for stats gained for attunable weapons. Not always populated, and is probably not intended for use.

### ItemAttuneAffix
Contains all affixes, and a table with the stats they would grant

## Functions
### CanAttuneItemHelper(itemId) -> int
Check if the item can be attuned by the current character, taking level, class, and armor proficiency into account

### IsAttunableBySomeone(itemId) -> bool
Check if the item can be attuned at all, ignoring class, level, etc.

### GetItemAttuneOverwrite(itemId) -> table { stat1type, stat1value }
Get a list of tables (key/val pairs) when attuning weapons

### GetAttuneStatName(statId) -> string
Returns the name of a stat, given a statId

### GetItemAttuneProgress(itemid, affixid, titanforged) -> int
Returns the attunment progress for an itemId (optional affixId, optional titanforged)
1 = Titanforged, 2 = Warforged, 3 = Lightforged

### GetItemAttuneForge(itemid) -> int
Returns the attuned forge level for an itemid
1 = Titanforged, 2 = Warforged, 3 = Lightforged

### GetAttuneAffixName(itemId, affixId) -> string
Returns the affix name

### HasAttunedAnyVariantOfItem(itemId) -> bool

### GetItemAffixMask(itemId) -> possibleMask1 (uint32), possibleMask2 (uint32), attunedMask1 (uint32), attunedMask2 (uint32), activeIndex (int)



# Perks
(Still unconfirmed. Most are probably not intended for use)
## Tables
### PerkMgrPoints
### PerkMgrPerks
### PerkMgrSets
### PerkMgrTaskHeader
### PerkMgrTaskAll
### GetPerkActive

## Functions
### GetPerkAcquired(perkId)
### GetPerkTaskProg(perkId)
### GetPerkTaskAssign1(perkId)
### GetPerkTaskAssign2(perkId)
### GetPerkLimit(perkId)
### GetPerkOptionsInfo(perkId, optionId)
### SetPerkActive(perkId)
### ~~SetPerkOptions(perkId, options)~~
Do not use: Does nothing towards the server