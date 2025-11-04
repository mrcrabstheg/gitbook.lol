---
icon: comment
---

# Notify

```lua
function glass:notify(message: string, lifetime: number?): nil
```

Displays a notification message to the user.

**Parameters:**

* `message` (string) - The text to display in the notification
* `lifetime` (number?) - Optional duration in seconds (default: 4)

**Returns:**

* `nil`

## Example:

{% code overflow="wrap" lineNumbers="true" %}
```lua
glass:notify("Player knocked!", 3)
glass:notify("wow a notify") -- Uses default 4 second duration
```
{% endcode %}
