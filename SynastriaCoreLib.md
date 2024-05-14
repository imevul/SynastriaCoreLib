```lua
local CONST_ADDON_NAME = 'MyAddon'
MyAddon = LibStub('AceAddon-3.0'):NewAddon(CONST_ADDON_NAME)

local SynastriaCoreLib = LibStub('SynastriaCoreLib-1.0')
SynastriaCoreLib.RegisterCallback(MyAddon, SynastriaCoreLib.Events.ItemAttuned, 'OnItemAttuned')
SynastriaCoreLib.RegisterCallback(MyAddon, SynastriaCoreLib.Events.CustomGameData, 'OnCustomGameData')

function MyAddon:OnItemAttuned(itemId)
end

function MyAddon:OnCustomGameData(typeId, id, prev, cur)
end
```