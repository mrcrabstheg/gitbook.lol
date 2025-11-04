---
icon: toggle-on
---

# Toggles

{% code lineNumbers="true" %}
```lua
function AddToggle(id: string, options: table): Frame
```
{% endcode %}

Creates a toggle switch in the specified tab.

**Parameters:**



* `id` (string) - Unique identifier for the toggle
* `options` (table) - Configuration table with the following fields:
  * `Text` (string?) - Display text (defaults to `id`)
  * `Tooltip` (string?) - Hover tooltip text (default: "")
  * `Default` (boolean?) - Initial state (default: false)
  * `Tab` (Frame?) - Parent tab (defaults to toggleTab)
  * `Callback` (function?) - Function called when toggled: `function(state: boolean)`

**Returns:**

* `Frame` - The toggle frame element

## Example:

{% code lineNumbers="true" %}
```lua
AddToggle("auto_farm", {
    Text = "Auto Farm",
    Tooltip = "Automatically farms resources",
    Default = false,
    Tab = myTab,
    Callback = function(state)
        if state then
            print("Auto farm enabled")
        else
            print("Auto farm disabled")
        end
    end
})
```
{% endcode %}
