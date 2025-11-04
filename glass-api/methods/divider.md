---
icon: horizontal-rule
---

# Divider

{% code lineNumbers="true" %}
```lua
function AddDivider(textOrOptions: string | table?, tab: Frame?): Frame
```
{% endcode %}

Creates a visual divider/separator in the settings GUI with optional centered text.

**Parameters:**

* `textOrOptions` (string | table?) - Either:
  * A string containing the divider text (optional, empty for line-only)
  * A table with configuration options
  * `nil` for a simple line divider
* `tab` (Frame?) - Optional target tab frame (default: `guiTab`)

## Example:

{% code title="Using options table" lineNumbers="true" %}
```lua
AddDivider({
    Text = "Advanced Features",
    Tab = buttonsTab
})
```
{% endcode %}

**Or**

{% code title="Divider in specific tab" lineNumbers="true" %}
```lua
AddDivider("Visual Options", guiTab)
AddDivider("Automation", toggleTab)
```
{% endcode %}
