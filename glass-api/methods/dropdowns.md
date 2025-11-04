---
icon: square-caret-down
---

# Dropdowns

{% code lineNumbers="true" %}
```lua
function AddMultiSelectDropdown(id: string, options: table): Frame
```
{% endcode %}

Creates a multi-select dropdown menu in the specified tab.

**Parameters:**

* `id` (string) - Unique identifier for the dropdown
* `options` (table) - Configuration table with the following fields:
  * `Text` (string?) - Display text (defaults to `id`)
  * `Items` (table) - Array of items with format: `{Name: string, Value: any}`
  * `Tab` (Frame?) - Parent tab (defaults to guiTab)
  * `Callback` (function?) - Function called when selection changes: `function(selected: table)`
    * `selected` is a dictionary where keys are the selected values and values are `true`

**Returns:**

* `Frame` - The dropdown frame element

## Example:

{% code lineNumbers="true" %}
```lua
local players = {}
for _, plr in ipairs(game.Players:GetPlayers()) do
    table.insert(players, {Name = plr.DisplayName, Value = plr})
end

AddMultiSelectDropdown("target_players", {
    Text = "Target Players",
    Items = players,
    Tab = combatTab,
    Callback = function(selected)
        for player, enabled in pairs(selected) do
            if enabled then
                print("Selected:", player.Name)
            end
        end
    end
})
```
{% endcode %}
