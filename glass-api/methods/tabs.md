---
icon: browsers
---

# Tabs

```lua
function AddTabToSettings(tabName: string): Frame
```

Creates a new tab in the settings GUI.

**Parameters:**

* `tabName` (string) - The name of the tab to create

**Returns:**

* `Frame` - The scrolling frame container for the tab content

## Example:

```lua
local myTab = AddTabToSettings("Custom Tab")
```

Notes:

* If a tab with the same name already exists, it will return the existing tab and show a warning
* Tabs are automatically added to the horizontal scrolling tab bar
* The tab content area is a ScrollingFrame that auto-resizes based on content

