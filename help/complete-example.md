---
icon: window
---

# Complete Example

{% code lineNumbers="true" %}
```lua
-- Create a custom tab
local myTab = AddTabToSettings("My Features")

-- Add a toggle
AddToggle("feature_enabled", {
    Text = "Enable Feature",
    Default = false,
    Tab = myTab,
    Callback = function(state)
        glass:notify("Feature " .. (state and "enabled" or "disabled"), 2)
    end
})

-- Add a slider
AddSlider("feature_speed", {
    Text = "Speed",
    Min = 1,
    Max = 10,
    Default = 5,
    Tab = myTab,
    Callback = function(value)
        print("Speed:", value)
    end
})

-- Add a color picker
AddColorPicker("feature_color", {
    Text = "Color",
    Default = Color3.fromRGB(255, 0, 0),
    Tab = myTab,
    Callback = function(color)
        print("Color:", color)
    end
})

-- Add a button
AddButton("execute_feature", {
    Text = "Execute",
    Tab = myTab,
    Callback = function()
        glass:notify("Feature executed!", 2)
    end
})
```
{% endcode %}

### Notes

* All UI elements automatically save their state when modified
* The GUI supports dragging and resizing
* Press the configured keybind (default: `N`) to open settings
* Colors and positions persist between sessions via JSON file storage
