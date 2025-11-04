---
icon: slider
---

# Sliders

{% code lineNumbers="true" %}
```lua
function AddSlider(id: string, options: table): Frame
```
{% endcode %}

Creates a slider control in the specified tab.

**Parameters:**

* `id` (string) - Unique identifier for the slider
* `options` (table) - Configuration table with the following fields:
  * `Text` (string?) - Display text (defaults to `id`)
  * `Min` (number?) - Minimum value (default: 0)
  * `Max` (number?) - Maximum value (default: 100)
  * `Default` (number?) - Initial value (default: 50)
  * `Step` (number?) - Value increment step (default: 1)
  * `Tab` (Frame?) - Parent tab (defaults to guiTab)
  * `Callback` (function?) - Function called when value changes: `function(value: number)`

**Returns:**

* `Frame` - The slider frame element

## Example:

{% code lineNumbers="true" %}
```lua
AddSlider("walk_speed", {
    Text = "Walk Speed",
    Min = 16,
    Max = 200,
    Default = 50,
    Step = 1,
    Tab = combatTab,
    Callback = function(value)
        LocalPlayer.Character.Humanoid.WalkSpeed = value
        glass:notify("Speed set to " .. value, 2)
    end
})
```
{% endcode %}
