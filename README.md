# Godot-Editor-Settings-Description
Allow you to set a description on a custom project and editor settings. Useful for making a settings for a plugin.

Currently, [godot didn't allow you to add description to a custom project/editor settings](https://github.com/godotengine/godot-proposals/discussions/8224). this as a temporary fix original by PiCode.

This is made for an extension of your plugin, so add this to your plugin folder, and the description will be displayed as long as the plugin is in the project.

> Tested on godot 4.6.

<img width="1202" height="739" alt="image" src="https://github.com/user-attachments/assets/b7fd1666-1c38-4822-9a49-a511c6753206" />

# Performace
This meant to be as lightweight as possible in term of storage and also cpu and memory usage. So the code is not running every frame.

# Installation
- Download the script file.
- Place them into your plugin folder (e.g. `addons/my_plugin/...`)
# Usage
Preload the script and use the script's `set_editor_setting_tooltip()` or `set_project_setting_tooltip()` method to set the description of your custom settings.
### Example:
```gdscript
func _ready() -> void:
	## Get Script:
	const SETTINGS_TOOLTIPS = preload("path/to/info.gd")

	## For Add editor Setting Tooltip
	SETTINGS_TOOLTIPS.set_editor_setting_tooltip("key_setting", "description for the setting")

	## For Add Project Setting Tooltip
	SETTINGS_TOOLTIPS.set_project_setting_tooltip("key_setting", "description for the setting")
```

# Implementation detail.
The way this works is, when you set a description, it will be stored in memory. Then when the setting's tooltip pop up, it will get access directly to the tooltip node, and set the description to its label.
