---
icon: keyboard
---

# Key pickers

{% code lineNumbers="true" %}
```lua
AddKeyPicker(id: string, options: table): (Frame, TextButton, KeybindData)
```
{% endcode %}

Creates a keybind picker UI element that allows users to configure keyboard shortcuts.

**Parameters:**

* `id` (string) - Unique identifier for the keybind
* `options` (table) - Configuration options:
  * `Text` (string?) - Display label (default: id)
  * `Default` (string?) - Initial key name (default: "LeftAlt")
  * `Mode` (string?) - Activation mode: "Toggle", "Hold", or "Always" (default: "Toggle")
  * `Callback` (function?) - Function called when key is pressed (default: empty function)
  * `Tab` (Frame?) - Parent tab container (default: toggleTab)

**Returns:**

* `Frame` - The UI frame container
* `TextButton` - The key display button
* `KeybindData` - Table with keybind data and methods:
  * `Text` (string) - Display name
  * `Key` (string) - Current key name
  * `Mode` (string) - Activation mode
  * `Callback` (function) - Callback function
  * `Enabled` (boolean) - Whether keybind is active
  * `GetState()` (function) - Returns true if key is currently pressed

## Example:

{% code lineNumbers="true" %}
```lua
AddToggle("char_spin", {
    Text = "Character Spin",
    Default = false,
    Tab = toggleTab,
    Callback = function()
        local toggle = Toggles.char_spin
        if not toggle then return end

        local keybind = Options.char_spin_keybind
        if keybind then
            keybind.NoUI = not toggle.Value
        end
    end
})

AddSlider("spin_speed", {
    Text = "Spin Speed",
    Default = 50,
    Min = 1,
    Max = 200,
    Rounding = 0,
    Tab = toggleTab
})

AddKeyPicker("char_spin_keybind", {
    Default = "M",
    Mode = "Toggle",
    Text = "Character Spin Keybind",
    Tab = toggleTab,
    Callback = function()
        if Toggles.char_spin and Toggles.char_spin.Value then
            _G.spinActive = not (_G.spinActive or false)
        end
    end
})

table.insert(unloadCleanup, RunService.Heartbeat:Connect(function()
    if not Toggles.char_spin.Value then
        if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("Humanoid") then
            LocalPlayer.Character.Humanoid.AutoRotate = true
        end
        return
    end

    local keybindOption = Options.char_spin_keybind
    local isActive = false

    if keybindOption.Mode == "Always" then
        isActive = true
    elseif keybindOption.Mode == "Hold" then
        isActive = keybindOption:GetState()
    elseif keybindOption.Mode == "Toggle" then
        isActive = _G.spinActive or false
    end

    if not isActive then
        if LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("Humanoid") then
            LocalPlayer.Character.Humanoid.AutoRotate = true
        end
        return
    end

    local char = LocalPlayer.Character
    local hrp = char and char:FindFirstChild("HumanoidRootPart")
    if not hrp then return end

    LocalPlayer.Character.Humanoid.AutoRotate = false
    local spinSpeed = sliders.spin_speed or 50
    hrp.CFrame = hrp.CFrame * CFrame.Angles(0, math.rad(spinSpeed / 10), 0)
end))
```
{% endcode %}

**Notes:**

* Keybinds are automatically monitored and triggered based on their Mode
* "Toggle" mode fires once per key press
* "Hold" mode requires continuous key press (check with `GetState()`)
* "Always" mode is always active regardless of key state
* All keybinds are stored in global `Options` table for easy access
* Users can reconfigure keys by clicking the button and pressing a new key
