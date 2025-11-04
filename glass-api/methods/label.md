---
icon: tag
---

# Label

{% code lineNumbers="true" %}
```lua
function AddLabel(id: string | any, options: boolean | table?): (Frame, TextLabel)
```
{% endcode %}

Creates a new labeled text element within the GUI, supporting multiple input formats for flexibility.

**Parameters:**

* `id` (`string`) — The label text or identifier.\
  When `options` is a table, this may serve as the label’s ID instead.
* `options` (`boolean | table?`) —
  * If `boolean`, determines whether the label text wraps (`true` = wrap text).
  * If `table`, supports extended configuration:
    * `Text` (`string?`) — The label text to display.
    * `DoesWrap` (`boolean?`) — Whether the text should wrap.
    * `Tab` (`Instance?`) — The parent GUI tab to attach the label to.

**Returns:**

* `Frame` — The container frame holding the label.
* `TextLabel` — The `TextLabel` instance displaying the text.

## Example:

{% code lineNumbers="true" %}
```lua
AddLabel("MyLabel", {
    Text = "This is a label made with table options",
    DoesWrap = true,
    Tab = buttonsTab
})
```
{% endcode %}
