# BetterRayfield 
This is the written documentation for BetterRayfield

Credits to [Shlex](https://github.com/shlexware/) for writing the original library, as this is a modified version of [Rayfield](https://github.com/shlexware/Rayfield/).

## Booting the Library
```lua
local Library = loadstring(game:HttpGet('https://raw.githubusercontent.com/05-4/BetterRayfield/main/source.lua'))()
```

### Secure Mode
If the game you're trying to run BetterRayfield Interface Suite on, is detecting or crashing when you use BetterRayfield Interface Suite, try using Secure Mode:
- Place `getgenv().SecureMode = true` above the initial BetterRayfield loadstring

BetterRayfield will now use Secure Mode and attempt to reduce detection
- Note: This may cause some elements of the UI to look lower quality or may increase loading times slightly

### Enabling Configuration Saving
- Enable ConfigurationSaving in the CreateWindow function
- Choose an appropiate FileName in the CreateWindow function
- Choose an unique flag identifier for each supported element you create
- Place `BetterRayfield:LoadConfiguration()` at the bottom of all your code

Rayfield will automatically save and load your configuration

## Creating a Window
```lua
local Window = Library:CreateWindow({
	Name = "Example Window",
	LoadingTitle = "BetterRayfield",
	LoadingSubtitle = "Sirius",
	ConfigurationSaving = {
		Enabled = true,
		FolderName = nil,
		FileName = "Big Hub"
	},
        Discord = {
        	Enabled = false,
        	Invite = "sirius", -- The Discord invite code, do not include discord.gg/
        	RememberJoins = true -- Set this to false to prompt joins every time BetterRayfield is opened
        },
	KeySystem = true, -- Set this to true to use our key system
	KeySettings = {
		Title = "BetterRayfield",
		Subtitle = "Key System",
		Note = "Join the discord (discord.gg/sirius)",
		FileName = "SiriusKey",
		SaveKey = true,
		GrabKeyFromSite = false, -- If this is true, set Key below to the RAW site you would like BetterRayfield to get the key from
		Key = "Hello"
	}
})
```

## Creating a Tab
```lua
local Tab = Window:CreateTab("Tab Example", 4483362458) -- Title, Image
```

## Creating a Section
```lua
local Section = Tab:CreateSection("Section Example")
```
### Updating a Section
```lua
Section:Set("Section Example")
```

## Notifying the user
```lua
Library:Notify({
    Title = "Notification Title",
    Content = "Notification Content",
    Duration = 6.5,
    Image = 4483362458,
    Actions = { -- Notification Buttons
        Ignore = {
            Name = "Okay!",
            Callback = function()
                print("The user tapped Okay!")
            end
		},
	},
})
```

## Creating a Button
```lua
local Button = Tab:CreateButton({
	Name = "Button Example",
	Callback = function()
		-- The function that takes place when the button is pressed
	end,
})
```
### Updating a Button
```lua
Button:Set("Button Example")
```

## Creating a Toggle
```lua
local Toggle = Tab:CreateToggle({
	Name = "Toggle Example",
	CurrentValue = false,
	Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
	Callback = function(Value)
		-- The function that takes place when the toggle is pressed
    		-- The variable (Value) is a boolean on whether the toggle is true or false
	end,
})
```
### Updating a Toggle
```lua
Toggle:Set(false)
```

## Creating a Color Picker
Coming Soon


## Creating a Slider
```lua
local Slider = Tab:CreateSlider({
	Name = "Slider Example",
	Range = {0, 100},
	Increment = 10,
	Suffix = "Bananas",
	CurrentValue = 10,
	Flag = "Slider1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
	Callback = function(Value)
		-- The function that takes place when the slider changes
    		-- The variable (Value) is a number which correlates to the value the slider is currently at
	end,
})
```
### Updating a Slider
```lua
Slider:Set(10) -- The new slider integer value
```

## Creating a Label
```lua
local Label = Tab:CreateLabel("Label Example")
```
### Updating a Label
```lua
Label:Set("Label Example")
```

## Creating a Paragraph
```lua
local Paragraph = Tab:CreateParagraph({Title = "Paragraph Example", Content = "Paragraph Example"})
```
### Updating a Paragraph
```lua
Paragraph:Set({Title = "Paragraph Example", Content = "Paragraph Example"})
```

## Creating an Adaptive Input (TextBox)
```lua
local Input = Tab:CreateInput({
	Name = "Input Example",
	PlaceholderText = "Input Placeholder",
	RemoveTextAfterFocusLost = false,
	Callback = function(Text)
		-- The function that takes place when the input is changed
    		-- The variable (Text) is a string for the value in the text box
	end,
})
```



## Creating a Keybind
```lua
local Keybind = Tab:CreateKeybind({
	Name = "Keybind Example",
	CurrentKeybind = "Q",
	HoldToInteract = false,
	Flag = "Keybind1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
	Callback = function(Keybind)
		-- The function that takes place when the keybind is pressed
    		-- The variable (Keybind) is a boolean for whether the keybind is being held or not (HoldToInteract needs to be true)
	end,
})
```
### Updating a Keybind
```lua
Keybind:Set("RightCtrl") -- Keybind (string)
```

## Creating a Dropdown menu
```lua
local Dropdown = Tab:CreateDropdown({
	Name = "Dropdown Example",
	Options = {"Option 1","Option 2"},
	CurrentOption = "Option 1",
	Flag = "Dropdown1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
	Callback = function(Option)
	  	  -- The function that takes place when the selected option is changed
    	  -- The variable (Option) is a string for the value that the dropdown was changed to
	end,
})
```
### Updating a Dropdown
```lua
Dropdown:Set("Option 2") -- The new option value
```

## Check the value of an existing element
To check the current value of an existing element, using the variable, you can do `ElementName.CurrentValue`, if it's a keybind or dropdown, you will need to use `KeybindName.CurrentKeybind` or `DropdownName.CurrentOption`
You can also check it via the flags from `Library.Flags`


## Destroying the Interface
```lua
Library:Destroy()
```

Or all the running interfaces in the game:

```lua
getgenv().DestroyAll()
```

## Get the UI Instance
You can now get the Instance of BetterRayfield to modify things yourself.

```lua
Library.Instance
```

## Custom Themes
Coming Soon
