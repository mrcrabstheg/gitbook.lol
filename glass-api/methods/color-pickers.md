---
icon: palette
---

# Color Pickers

{% code lineNumbers="true" %}
```lua
function AddColorPicker(id: string, options: table): Frame
```
{% endcode %}

Creates a color picker with HSV selection in the specified tab.

Parameters:

* `id` (string) - Unique identifier for the color picker
* `options` (table) - Configuration table with the following fields:
  * `Text` (string?) - Display text (defaults to `id`)
  * `Default` (Color3?) - Initial color (default: Color3.fromRGB(255, 255, 255))
  * `Tab` (Frame?) - Parent tab (defaults to guiTab)
  * `Callback` (function?) - Function called when color changes: `function(color: Color3)`

**Returns:**

* `Frame` - The color picker frame element

## Example:

{% code overflow="wrap" lineNumbers="true" %}
```lua
AddColorPicker("esp_color", {
    Text = "ESP Color",
    Default = Color3.fromRGB(0, 255, 0),
    Tab = espTab,
    Callback = function(color)
        -- Update ESP color
        for _, highlight in pairs(highlights) do
            highlight.FillColor = color
        end
    end
})
```
{% endcode %}
