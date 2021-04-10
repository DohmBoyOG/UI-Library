# UILibV7
Usage:
```lua
local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/AlterRainbow/UI-Library/main/UILib.lua"))() -- gets the ui lib

local main = lib:Window(text) -- creates a window with given text.
local tab = main:Tab(text) -- creates a tab with given text.
local bttn = tab:Button(text, callback) -- creates a button with given text and runs given function.
local slid = tab:Slider(text, minvalue, maxvalue, default, callback) -- creates a slider with given text from minvalue to maxvalue with default being it's starting value, runs given function.
local tggle = tab:Toggle(text, callback) -- creates a toggle with given text that runs a given function.
local drop = tab:Dropdown(text, {}, callback) -- creates a dropdown with given text and runs the given function when an item that has been passed down as a table is pressed.
local item = drop:Item(text, value) -- creates an item in the dropdown with given text to display in the dropdown and a value that will be passed down when the dropdown's function is called. The passed text argument will also be the one to use as a way to identify between items so you can delete that item when needed.
drop:ItemRemove(text) -- Will remove an item from the dropdown that has the passed argument as text to display in the dropdown.
local lbl = tab:Label(text) -- creates a label with given text.
local clr = tab:Color(text, callback) -- creates a color picker (THE TWO SLIDERS AND THE HEX INPUT DO NOT WORK ATM, THE RGB INPUT DOES) that runs the given function when the confirm button has been clicked.
local box = tab:Textbox(text, callback) -- creates a textbox and runs given function.
local bind = tab:Keybind(text, default, callback) -- creates a keybind item with given text and 'default' as default keybind and runs given function when the keybind has been pressed.

Settings() -- you can choose to add this, this will create a tab where the you can customize the UI, change the keybind to hide/show the UI and a button to destroy the UI.
Info() -- you can choose to add this, this will create a tab where you can read some information about the UI etc.
Credits(text) -- you can choose to add this, this will create a tab where credits are given to me, and another label with custom text you can pass down.
```
Example:
```lua
local lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/AlterRainbow/UI-Library/main/UILib.lua"))()

local main = lib:Window("Example")

local tab = main:Tab("First example")
local tabb = main:Tab("Second example")
local tabbb = main:Tab("Dropdown example")

local butt tab:Button("print 'example'", function() print("example") end)
local slid = tab:Slider("rate example:", 7, 10, 8, function(nmbr) print("This example is rated "..nmbr.." out of 10.") end)
local tggle = tab:Toggle("print state", function(state) print(state) end)
local drop = tab:Dropdown("dilemma:", {"kill yourself", "kill your mom", "kill your dad"}, function(chosen) print("You chose to "..chosen..".") end)

local lbl = tabb:Label("Hi there, rate this UI")
local clr = tabb:Color("baseplate color", function(reddd, greennn, blueee) game.workspace.Baseplate.Color = Color3.fromRGB(reddd, greennn, blueee) end)
local box = tabb:Textbox("print input", function(input) print(input) end)
local bind = tabb:Keybind("change walkspeed to 100", "RightShift", function() game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 100 end)
local dropp = tabb:Dropdown("TP", {["home"] = game.workspace.home, ["moon"] = game.workspace.moon, ["sun"] = game.workspace.sun}, function(penis) game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = penis.CFrame end)

local plrs = {}

for i, v in pairs(game.Players:GetPlayers()) do
  if v ~= game.Players.LocalPlayer then
    table.insert(plrs, v)
  end
end

local droppp = tabbb:Dropdown("dropdown", plrs, function(chsn) game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = chsn.Character.HumanoidRootPart.CFrame end)

game.Players.PlayerAdded:Connect(function(plr)
  droppp:Item(plr.Name, plr)
end)

game.Players.PlayerRemoving:Connect(function(plr)
  droppp:Item(plr.Name)
end)

Settings()
Info()
Credits("Ok cool tutorial")
```
-- Notes --

Please remember to use the roblox KeyCodes for default keybinds, in other words, don't pass 'Right SHIFt' as default bind. Instead pass: "RightShift".
Dropdowns will add items with their text being the index if the table is a dictionary or the items will have their text set to the values if the table is an array.

Color picker sliders and hex inputs do not work (still looking for a way to fix those), rgb inputs do, so you can use color pickers.

I do not log your IP, HWID or anything else. I might start counting executions one day. However I will tell you guys when that happens.

Send me bugs etc.
