---
icon: play
---

# Buttons

{% code lineNumbers="true" %}
```lua
function AddButton(id: string, options: table): TextButton
```
{% endcode %}

Creates a button in the specified tab.

**Parameters:**

* `id` (string) - Unique identifier for the button
* `options` (table) - Configuration table with the following fields:
  * `Text` (string?) - Display text (defaults to `id`)
  * `Tab` (Frame?) - Parent tab (defaults to guiTab)
  * `Callback` (function?) - Function called when clicked: `function()`

**Returns:**

* `TextButton` - The button element

## Example:

{% code lineNumbers="true" %}
```lua
AddButton("reset_stats", {
    Text = "Reset Statistics",
    Tab = myTab,
    Callback = function()
        -- Reset logic here
        glass:notify("Stats reset!", 2)
    end
})
```
{% endcode %}
