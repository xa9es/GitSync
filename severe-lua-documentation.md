# Severe Lua Documentation

## Overview
This document provides comprehensive documentation for the Severe Lua API, including functions for interacting with the Roblox environment, drawing utilities, and memory manipulation.

## Base Information

### Roblox Lua Information
All "get" and "set" functions use PascalCase for rlua support. Objects typically have the following properties:

```lua
-- General properties:
-- .Data - returns the userdata
-- .Name - returns the name
-- .ClassName - returns the classname
-- .Parent - returns the parent
```

Example usage:
```lua
print(game.Players:FindFirstChild("novice"))
game:FindService("UserInputService"):SetMouseLocation(0, 0)
print(game:FindService("Players").localPlayer.Name)
print(game:FindService("Players").localPlayer.Data) -- returns userdata
```

## Predefined Globals

### Game
```lua
-- [return: userdata] Game - returns datamodel
```
Returns the datamodel as userdata.

### game
```lua
-- [return: table] game - returns datamodel [rlua only]
```
Returns the datamodel as a table (rlua only).

### Workspace
```lua
-- [return: userdata] Workspace - returns workspace
```
Returns the workspace as userdata.

### workspace
```lua
-- [return: userdata] workspace - returns workspace [rlua only]
```
Returns the workspace as userdata (rlua only).

## Misc Functions

### worldtoscreenpoint
```lua
-- [returns: tuple - fields: x, y | boolean] worldtoscreenpoint(table - vector3)
```
Returns the screen coordinates of a given Vector3 position and a boolean indicating whether the point is within the bounds of the screen.

### print
```lua
-- [return: none] print(string)
```
Prints the specified string in white text.

### warn
```lua
-- [return: none] warn(string)
```
Prints the specified string in yellow text.

### wait
```lua
-- [return: none] wait([OPTIONAL] number)
```
Yields the current thread with the specified timeout.

### spawn
```lua
-- [return: none] spawn(function)
```
Spawns a task which is executed in the scheduler.

### gethwid
```lua
-- [return: string] gethwid()
```
Returns the current user SID.

### setclipboard
```lua
-- [return: none] setclipboard(string)
```
Sets the string argument to your clipboard.

### tick
```lua
-- [return: number] tick()
```
Returns the amount of time in seconds since the Unix epoch according to this device's time.

### gcinfo
```lua
-- [return: number] gcinfo()
```
Returns the total memory heap size in kilobytes.

### time
```lua
-- [return: number] time()
```
Returns the amount of time, in seconds, that has elapsed since severe started running.

### loadstring
```lua
-- [return: variant] loadstring(string, [OPTIONAL] [CHUNK] string)
```
Loads Lua code from the string and returns it as a function.

### isrbxactive
```lua
-- [return: boolean] isrbxactive()
```
Returns a boolean indicating if Roblox is focused or not.

### destroy
```lua
-- [return: none] destroy(userdata)
```
Sets the userdata parent to nothing, technically destroying it.

### File Management Functions

#### makefolder
```lua
-- [return: none] makefolder(string - foldername)
```
Creates a folder at C:\v2\data\[foldername].

#### deletefolder
```lua
-- [return: none] deletefolder(string - foldername)
```
Deletes the folder at C:\v2\data\[foldername].

#### deletefile
```lua
-- [return: none] deletefile(string - filename)
```
Deletes the file at C:\v2\data\[filename].

#### checkfolder
```lua
-- [return: boolean] checkfolder(string - foldername)
```
Checks if the folder exists at C:\v2\data\[foldername].

#### checkfile
```lua
-- [return: boolean] checkfile(string - filename)
```
Checks if the file exists at C:\v2\data\[filename].

#### listfiles
```lua
-- [return: table] listfiles()
```
Lists all files in C:\v2\data.

#### writefile
```lua
-- [return: none] writefile(string - filename, string - data)
```
Creates the file and writes the data into it at C:\v2\data\[filename].

#### readfile
```lua
-- [return: string] readfile(string - filename)
```
Returns the contents from the file at C:\v2\data\[filename].

### Window and UI Functions

#### set_window_passthrough
```lua
-- [return: none] set_window_passthrough(boolean)
```
Controls whether mouse events pass through the Severe overlay or not.

#### SET_SCHEDULER_TIMEOUT
```lua
-- [return: none] SET_SCHEDULER_TIMEOUT(boolean)
```
Controls whether the scheduler can timeout if frozen for 7 seconds or not.

#### ismenuopened
```lua
-- [return: boolean] ismenuopened()
```
Returns a boolean indicating if the Severe menu is opened or not.

### Check Functions

#### is_team_check_active
```lua
-- [return: boolean] is_team_check_active()
```
Returns a boolean indicating if team check is enabled or not.

#### is_forcefield_check_active
```lua
-- [return: boolean] is_forcefield_check_active()
```
Returns a boolean indicating if force field check is enabled or not.

#### is_tool_check_active
```lua
-- [return: boolean] is_tool_check_active()
```
Returns a boolean indicating if tool check is enabled or not.

#### is_local_name_check_active
```lua
-- [return: boolean] is_local_name_check_active()
```
Returns a boolean indicating if local name check is enabled or not.

#### is_local_health_check_active
```lua
-- [return: boolean] is_local_health_check_active()
```
Returns a boolean indicating if local health check is enabled or not.

### SendNotification
```lua
-- [return: none] SendNotification(string - content, string - type)
```
Sends a notification popup request to Severe.

### Model Data Functions

#### add_model_data
```lua
-- [return: boolean] add_model_data(table, string - key)
```
Creates model data with a specific key and processes it in the model thread. Returns true if successful.

#### edit_model_data
```lua
-- [return: boolean] edit_model_data(table, string - key)
```
Edits existing model data from a specific key. Returns true if successful.

#### remove_model_data
```lua
-- [return: boolean] remove_model_data(string - key)
```
Removes existing model data from a specific key. Returns true if successful.

#### clear_model_data
```lua
-- [return: boolean] clear_model_data()
```
Removes all model data. Returns true if successful.

### Local Data Functions

#### override_local_data
```lua
-- [return: boolean] override_local_data(table)
```
Overrides existing or creates local data for the local thread. Returns true if successful.

#### clear_local_data
```lua
-- [return: boolean] clear_local_data()
```
Removes all created local data. Returns true if successful.

### JSON Functions

#### JSONEncode
```lua
-- [return: string] JSONEncode(variant)
```
Transforms a Lua table into a JSON object or array.

#### JSONDecode
```lua
-- [return: variant] JSONDecode(string)
```
Transforms a JSON object or array into a Lua table.

### Vector and CFrame Functions

#### lerpvector3
```lua
-- [return: tuple - Vector3 - fields: x, y, z] lerpvector3(table - vector3, table - vector3, number - alpha)
```
Returns a Vector3 interpolated between arg1 and arg2 by the fraction alpha.

#### lerpcframe
```lua
-- [return: tuple - CFrame - fields: lookvector - vector3, upvector - vector3, rightvector - vector3, position - vector3] lerpcframe(cframe, cframe, number - alpha)
```
Returns a CFrame interpolated between arg1 and arg2 by the fraction alpha.

#### cframelookat
```lua
-- [return: tuple - CFrame - fields: lookvector - vector3, upvector - vector3, rightvector - vector3, position - vector3] cframelookat(table - cframe, table - vector3)
```
Returns a new CFrame with the position of arg1 [cframe] and facing towards arg2 [vector3].

### Pointer Conversion Functions

#### pointer_to_table_data
```lua
-- [return: table] pointer_to_table_data(number - pointer)
```
Returns the pointer as a table that can be used for internal functions (for rlua only).

#### pointer_to_user_data
```lua
-- [return: userdata] pointer_to_user_data(number - pointer)
```
Returns the pointer as userdata that can be used for internal functions.

## Get Functions

### getvalue
```lua
-- [return: number or table or bool or int or string] getvalue(userdata)
```
Returns the value property of the userdata class (name must include "Value").

### findfirstchild
```lua
-- [return: userdata] findfirstchild(userdata, string)
```
Returns the first child of the userdata with the given name.

### findfirstchildofclass
```lua
-- [return: userdata] findfirstchildofclass(userdata, string)
```
Returns the first child of the userdata whose classname is equal to the given classname.

### findfirstancestorofclass
```lua
-- [return: userdata] findfirstancestorofclass(userdata, string)
```
Returns the first ancestor of the userdata whose classname is equal to the given classname.

### getname
```lua
-- [return: string] getname(userdata)
```
Returns the name of the userdata.

### getclassname
```lua
-- [return: string] getclassname(userdata)
```
Returns the classname of the userdata.

### getchildren
```lua
-- [return: array] getchildren(userdata)
```
Returns an array containing all of the userdata's direct children.

### getdescendants
```lua
-- [return: array] getdescendants(userdata)
```
Returns an array containing all children of the userdata and every child of those children.

### getparent
```lua
-- [return: userdata] getparent(userdata)
```
Returns the parent of the userdata.

### isancestorof
```lua
-- [return: boolean] isancestorof(userdata, userdata)
```
Returns true if the first userdata is an ancestor of the given descendant (second userdata).

### isdescendantof
```lua
-- [return: boolean] isdescendantof(userdata, userdata)
```
Returns true if the first userdata is a descendant of the given ancestor (second userdata).

### getlocalplayer
```lua
-- [return: userdata] getlocalplayer()
```
Returns the local player.

### getcharacter
```lua
-- [return: userdata] getcharacter(userdata -> Player)
```
Returns the character of the given player.

### findservice
```lua
-- [return: userdata] findservice(userdata -> Game, string)
```
Returns the service specified by the given classname.

### getuserid
```lua
-- [return: number] getuserid(userdata -> Player)
```
Returns the player's user ID.

### getping
```lua
-- [return: number] getping()
```
Returns your Roblox game ping.

### getscreendimensions
```lua
-- [returns: tuple - fields: x, y] getscreendimensions()
```
Returns the screen dimensions.

### getadornee
```lua
-- [return: userdata] getadornee(userdata -> BillboardGui)
```
Returns the adornee of the BillboardGui.

### getdisplayname
```lua
-- [return: string] getdisplayname(userdata -> Player)
```
Returns the display name of the player.

### getprimarypart
```lua
-- [return: userdata] getprimarypart(userdata -> Model)
```
Returns the primary part of the model.

### gethealth
```lua
-- [return: number] gethealth(userdata -> Humanoid)
```
Returns the health of the humanoid.

### getmaxhealth
```lua
-- [return: number] getmaxhealth(userdata -> Humanoid)
```
Returns the max health of the humanoid.

### getteam
```lua
-- [return: userdata] getteam(userdata -> Player)
```
Returns the team of the player.

### gettextureid
```lua
-- [return: string] gettextureid(userdata -> MeshPart)
```
Returns the texture ID of the MeshPart.

### getmeshid
```lua
-- [return: string] getmeshid(userdata -> MeshPart)
```
Returns the mesh ID of the MeshPart.

### getcamerafov
```lua
-- [return: number] getcamerafov(userdata -> Camera)
```
Returns the FOV of the camera.

### getposition
```lua
-- [return: tuple - fields: x, y, z] getposition(userdata)
```
Returns the position of the given part or camera.

### getlookvector
```lua
-- [return: tuple - fields: x, y, z] getlookvector(userdata)
```
Returns the look vector of the given part or camera.

### getrightvector
```lua
-- [return: tuple - fields: x, y, z] getrightvector(userdata)
```
Returns the right vector of the given part or camera.

### getupvector
```lua
-- [return: tuple - fields: x, y, z] getupvector(userdata)
```
Returns the up vector of the given part or camera.

### getsize
```lua
-- [return: tuple - fields: x, y, z] getsize(userdata)
```
Returns the size of the given part.

### getvelocity
```lua
-- [return: tuple - fields: x, y, z] getvelocity(userdata)
```
Returns the velocity of the given part.

### findfirstdescendant
```lua
-- [return: userdata] findfirstdescendant(userdata, string)
```
Returns the first descendant found with the given name.

### findfirstancestor
```lua
-- [return: userdata] findfirstancestor(userdata, string)
```
Returns the first ancestor of the userdata whose name equals the given name.

### waitforchild
```lua
-- [return: userdata] waitforchild(userdata, string, [OPTIONAL] number)
```
Returns the child of the userdata with the given name. If the child does not exist, it will pause the current thread until it does. The optional timeout parameter will cause the function to return nil after the specified number of seconds.

### getcframe
```lua
-- [return: tuple - CFrame - fields: lookvector - vector3, upvector - vector3, rightvector - vector3, position - vector3] getcframe(userdata)
```
Returns the CFrame of the given part or camera.

## Set Functions

### setcframe
```lua
-- [return: none] setcframe(userdata, table - cframe)
```
Sets the CFrame of the userdata to the given CFrame.

### setlookvector
```lua
-- [return: none] setlookvector(userdata, table - vector3)
```
Sets the look vector of the userdata to the given Vector3.

### setupvector
```lua
-- [return: none] setupvector(userdata, table - vector3)
```
Sets the up vector of the userdata to the given Vector3.

### setrightvector
```lua
-- [return: none] setrightvector(userdata, table - vector3)
```
Sets the right vector of the userdata to the given Vector3.

### setposition
```lua
-- [return: none] setposition(userdata, table - vector3)
```
Sets the position of the userdata to the given Vector3.

### setvelocity
```lua
-- [return: none] setvelocity(userdata, table - vector3)
```
Sets the velocity of the userdata to the given Vector3.

### setmouselocation
```lua
-- [return: none] setmouselocation(userdata -> MouseService, number - x, number - y)
```
Sets Roblox mouse location to specified x and y values.

### setmouseiconenabled
```lua
-- [return: none] setmouseiconenabled(userdata -> MouseService, bool)
```
Sets Roblox mouse icon visibility (false = hide cursor, true = show cursor).

### setmousebehaviour
```lua
-- [return: none] setmousebehaviour(userdata -> MouseService, number)
```
Sets Roblox mouse behavior (0 = Default, 1 = LockCenter, 2 = LockCurrentPosition).

### setmousedeltasensitivity
```lua
-- [return: none] setmousedeltasensitivity(userdata -> MouseService, number)
```
Sets Roblox mouse delta sensitivity.

### setvalue
```lua
-- [return: none] setvalue(userdata, int or number or table or bool or string)
```
Sets the value property of the userdata. Class name must include "Value" and the second argument must match the classname.

### setcamerasubject
```lua
-- [return: none] setcamerasubject(userdata -> Camera)
```
Sets the camera subject.

## Keyboard Functions

For virtual key codes, refer to: https://docs.microsoft.com/en-us/windows/desktop/inputdev/virtual-key-codes

### keypress
```lua
-- [return: none] keypress(number - keycode)
```
Simulates a key press for the given virtual keycode.

### keyrelease
```lua
-- [return: none] keyrelease(number - keycode)
```
Simulates a key release for the given virtual keycode.

### getpressedkey
```lua
-- [return: string] getpressedkey()
```
Returns the last pressed key name.

### getpressedkeys
```lua
-- [return: array] getpressedkeys()
```
Returns a list of pressed key names.

## Mouse Functions

### isleftclicked
```lua
-- [return: boolean] isleftclicked()
```
Returns a boolean indicating if the left mouse button was clicked.

### isrightclicked
```lua
-- [return: boolean] isrightclicked()
```
Returns a boolean indicating if the right mouse button was clicked.

### isleftpressed
```lua
-- [return: boolean] isleftpressed()
```
Returns a boolean indicating if the left mouse button is pressed.

### isrightpressed
```lua
-- [return: boolean] isrightpressed()
```
Returns a boolean indicating if the right mouse button is pressed.

### mousemoverel
```lua
-- [return: none] mousemoverel(number - x, number - y)
```
Moves the mouse to the x and y relative coordinates.

### mousemoveabs
```lua
-- [return: none] mousemoveabs(number - x, number - y)
```
Moves the mouse to the x and y absolute coordinates.

### mousescroll
```lua
-- [return: none] mousescroll(number - pixels)
```
Scrolls your mouse by the given pixels.

### mouse1click
```lua
-- [return: none] mouse1click()
```
Simulates a left mouse click.

### mouse1press
```lua
-- [return: none] mouse1press()
```
Simulates a left mouse press.

### mouse1release
```lua
-- [return: none] mouse1release()
```
Simulates a left mouse release.

### mouse2click
```lua
-- [return: none] mouse2click()
```
Simulates a right mouse click.

### mouse2press
```lua
-- [return: none] mouse2press()
```
Simulates a right mouse press.

### mouse2release
```lua
-- [return: none] mouse2release()
```
Simulates a right mouse release.

### getmouseposition
```lua
-- [return: tuple - fields: x, y] getmouseposition()
```
Returns the default mouse position.

### ismouseiconenabled
```lua
-- [return: boolean] ismouseiconenabled(userdata -> MouseService)
```
Returns a boolean indicating if the mouse icon is enabled.

### getmouselocation
```lua
-- [return: tuple - fields: x, y] getmouselocation(userdata -> MouseService)
```
Returns the Roblox mouse location.

### getmousebehavior
```lua
-- [return: number] getmousebehavior(userdata -> MouseService)
```
Returns a number indicating how the mouse is behaving (0 = Default, 1 = LockCenter, 2 = LockCurrentPosition).

### getmousedeltasensitivity
```lua
-- [return: number] getmousedeltasensitivity(userdata -> MouseService)
```
Returns the Roblox mouse delta sensitivity.

### smoothmouse_exponential
```lua
-- [return: tuple - fields: x, y] smoothmouse_exponential(table - x | y [ORIGIN], table - x | y [POINT], number - speed)
```
Returns the exponential smoothing mouse results (recommended for aimbot).

Example usage:
```lua
local mouse = getmouseposition()
local point_to = {0, 0}
local speed = .5
local result = smoothmouse_exponential({mouse.x, mouse.y}, point_to, speed)
print(result.x, result.y)
```

### smoothmouse_linear
```lua
-- [return: tuple - fields: x, y] smoothmouse_linear(table - x | y [ORIGIN], table - x | y [POINT], number - sensitivity, number - smoothness)
```
Returns the linear smoothing mouse results (recommended for aimbot).

Example usage:
```lua
local mouse = getmouseposition()
local point_to = {0, 0}
local sensitivity = 1
local smoothness = .5
local result = smoothmouse_linear({mouse.x, mouse.y}, point_to, sensitivity, smoothness)
print(result.x, result.y)
```

## Network Functions

### WebSocket Functions

Example usage:
```lua
local ws = websocket_connect("ws://severe-websocket-test.glitch.me") -- connects to the websocket
websocket_onmessage(ws, function(msg) warn(msg) end) -- fires when a message is received from the websocket
websocket_send(ws, "Hello World!") -- sends message to the websocket
wait(1) -- yields the thread for 1 second
websocket_close(ws) -- closes the connection to the websocket
```

#### websocket_connect
```lua
-- [return: none] websocket_connect(string - URL)
```
Connects to the websocket URL. Errors if it fails.

#### websocket_onmessage
```lua
-- [return: none] websocket_onmessage(userdata - websocket, function)
```
Executes the function when a new message from the websocket is received.

#### websocket_send
```lua
-- [return: none] websocket_send(userdata - websocket, string)
```
Sends a message (string) to the websocket.

#### websocket_close
```lua
-- [return: none] websocket_close(userdata - websocket, string)
```
Closes the connection with the websocket.

### HTTP Functions

#### httpget
```lua
-- [return: string] httpget(string)
```
Returns the contents of the given URL.

#### httppost
```lua
-- [return: string] httppost(string - URL, string - DATA, string - CONTENT_TYPE, string - ACCEPT, [OPTIONAL] string - COOKIE, [OPTIONAL] string - REFERER, [OPTIONAL] string - ORIGIN)
```
Sends a POST request to the given URL and returns the result.

## Drawing Library

### Drawing.clear
```lua
-- [return: none] Drawing.clear()
```
Clears and deletes all created drawing objects.

### Drawing.new
```lua
-- [return: object] Drawing.new(string - TYPE)
```
Creates a new drawing object and returns it.

#### Supported Types
1. Text
2. Line
3. Quad
4. Triangle
5. Circle
6. Square
7. Image

#### Default Properties
All drawing objects have these properties:
```lua
bool Visible
void Remove
Vector3 Color
number zIndex
```

#### Text Properties
```lua
string Text
number Transparency
number Size
bool Center
bool Outline
Vector3 OutlineColor
Vector2 Position
Vector2 TextBounds [readonly]
number Font : 0 - 15
```

#### Line Properties
```lua
number Transparency
number Thickness
Vector2 From
Vector2 To
```

#### Circle Properties
```lua
number Transparency
number Thickness
number NumSides
number Radius
bool Filled
Vector2 Position
```

#### Square Properties
```lua
number Transparency
number Thickness
Vector2 Size
Vector2 Position
bool Filled
```

#### Triangle Properties
```lua
number Transparency
number Thickness
Vector2 PointA
Vector2 PointB
Vector2 PointC
bool Filled
```

#### Image Properties
```lua
string Url
bool Gif
number Delay [GIF Only]
Vector2 Position
Vector2 Size
number Transparency
```

#### Quad Properties
```lua
Vector2 PointA
Vector2 PointB
Vector2 PointC
Vector2 PointD
number Thickness
bool Filled
number Transparency
```

#### Example Usage - Text

```lua
local text = Drawing.new("Text")
text.Text = "severe drawing library!"
text.Visible = true
text.zIndex = 1
text.Position = {10, 10}
text.Color = {255, 255, 255}
text.Size = 15
wait(5) -- yield for 5 seconds
text:Remove()
```

#### Example Usage - Image (GIF)

```lua
local Image = Drawing.new("Image")
Image.Url = "https://i.giphy.com/media/v1.Y2lkPTc5MGI3NjExaTMzN21qODhla2pudGtlZHQ4aXpyMm5rOXlud3hkbjRmcm44MXhkdCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/VrQjb9El7JaQSFYjgJ/giphy-downsized-large.gif"
Image.Visible = true
Image.zIndex = 1
Image.Gif = true
Image.Delay = 30
Image.Position = {400, 100}
Image.Size = {500, 500}
wait(20) -- yield for 20 seconds
Image:Remove()
```

#### Example Usage - Image (Static)

```lua
local Image = Drawing.new("Image")
Image.Url = "https://letsenhance.io/static/8f5e523ee6b2479e26ecc91b9c25261e/1015f/MainAfter.jpg"
Image.Visible = true
Image.zIndex = 1
Image.Position = {1000, 100}
Image.Size = {500, 500}
wait(10) -- yield for 10 seconds
Image:Remove()
```

## Internal Functions

### Memory Value Types
1. qword
2. dword
3. double
4. float
5. string
6. bool

### getmemoryvalue
```lua
-- [return: qword | dword | double | float | string | bool] getmemoryvalue(userdata - pointer, number - offset, string - type)
```
Reads the value at the specified offset and returns it with the type you want.

### setmemoryvalue
```lua
-- [return: none] setmemoryvalue(userdata - pointer, number - offset, string - type, number | string - value)
```
Sets the value at the specified offset with the type you want.

### Example - Fake Headless
```lua
-- primitive offset: 0x160
-- size x offset: 0x2b0
-- size y offset: 0x2b4
-- size z offset: 0x2b8

-- [ fake headless -client sided- scroll in and out of head ]
local head = game.Players.localPlayer.Character.Head
local primitive_ptr = head:GetMemoryValue(0x160, "qword")
local primitive_ptr_data = pointer_to_table_data(primitive_ptr)
primitive_ptr_data:SetMemoryValue(0x2ac, "float", 0) -- x
primitive_ptr_data:SetMemoryValue(0x2ac, "float", 0) -- y
primitive_ptr_data:SetMemoryValue(0x2ac, "float", 0) -- z
```

### Example - Change LocalPlayer Username
```lua
-- [ change localplayer username -client sided- ]
local localplayer = getlocalplayer()
-- get the memory value residing at offset: 0x68 with type: qword
local nameptr = getmemoryvalue(localplayer, 0x68, "qword")
-- convert the pointer to a userdata so it can be used
local nameptr_data = pointer_to_user_data(nameptr)
-- get the string value residing at offset: 0x0 which represents the name
local name = getmemoryvalue(nameptr_data, 0x0, "string")
-- print the name
print(name)
-- set the new localplayer name that you want in memory
setmemoryvalue(nameptr_data, 0x0, "string", "hello_severe")
```

## Thread Override Examples

### Model Data Structure
Defines the structure for storing character-related information, used for gameplay logic such as targeting, visualization, and status tracking.

Fields:
- Username (string) - The player's in-game username
- Displayname (string) - The player's display name
- Userid (number) - Unique player identifier (Roblox UserId)
- Character (Instance) - Reference to the character model instance
- PrimaryPart (Instance) - The root/base part of the character (usually HumanoidRootPart)
- Head (Instance) - Head part of the character
- LeftLeg (Instance) - Left leg part
- LeftArm (Instance) - Left arm part
- RightLeg (Instance) - Right leg part
- RightArm (Instance) - Right arm part
- Torso (Instance) - Torso or central body part
- BodyHeightScale (number) - Height scale multiplier for the character
- RigType (number) - Rig type (e.g., "R6 = 0" or "R15 = 1")
- Whitelisted (boolean) - Whether the player is excluded from hostile logic
- Archenemies (Boolean) - Hostile player
- Aimbot_Part (Instance) - Preferred target part for aimbot functionality
- Aimbot_TP_Part (Instance) - Target part for aimbot teleportation (e.g., for mouse tp)
- Triggerbot_Part (Instance) - Part used for triggerbot activation
- Health (number) - Current health value of the character
- MaxHealth (number) - Maximum health value
- body_parts_data (table) - Table for specific body parts (typically used for chams & skeleton), format: `{ name = "LowerTorso", part = userdata }`
- full_body_data (table) - Table for all relevant body parts (typically used for closest and random body parts), format: `{ name = "Head", part = userdata }`

Example usage:
```lua
local data = {
  Username = "Player1",
  Displayname = "CoolPlayer",
  Userid = 123456,
  Character = workspace.Player1.Character,
  PrimaryPart = workspace.Player1.Character.HumanoidRootPart
  -- additional fields...
}

add_model_data(data, "key_1")
```

### Model Edit Structure
Defines a partial data structure intended to update specific fields of an existing model data. Used for modifying values such as health