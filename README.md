GameSense API for Lua
client.set_event_callback
client.unset_event_callback
client.log
client.color_log
client.error_log
client.exec
client.userid_to_entindex
client.draw_debug_text
client.draw_hitboxes
client.random_int
client.random_float
client.screen_size
client.visible
client.trace_line
client.trace_bullet
client.scale_damage
client.delay_call
client.latency
client.camera_angles
client.camera_position
client.timestamp
client.eye_position
client.set_clan_tag
client.system_time
client.unix_time
client.reload_active_scripts
client.create_interface
client.find_signature
client.key_state
client.get_model_name
client.register_esp_flag
config.load
config.export
cvar.set_string
cvar.get_string
cvar.set_float
cvar.set_raw_float
cvar.get_float
cvar.set_int
cvar.set_raw_int
cvar.get_int
cvar.invoke_callback
database.write
database.read
entity.get_local_player
entity.get_all
entity.get_players
entity.get_game_rules
entity.get_player_resource
entity.get_classname
entity.set_prop
entity.get_prop
entity.is_enemy
entity.is_alive
entity.is_dormant
entity.get_player_name
entity.get_player_weapon
entity.hitbox_position
entity.get_steam64
entity.get_bounding_box
entity.get_origin
entity.get_esp_data
globals.realtime
globals.curtime
globals.frametime
globals.absoluteframetime
globals.maxplayers
globals.tickcount
globals.tickinterval
globals.framecount
globals.mapname
globals.lastoutgoingcommand
globals.oldcommandack
globals.commandack
globals.chokedcommands
panorama.open
panorama.loadstring
materialsystem.get_name
materialsystem.reload
materialsystem.color_modulate
materialsystem.alpha_modulate
materialsystem.set_shader_param
materialsystem.get_shader_param
materialsystem.set_material_var_flag
materialsystem.get_material_var_flag
materialsystem.find_material
materialsystem.find_materials
materialsystem.find_texture
materialsystem.get_model_materials
materialsystem.arms_material
materialsystem.chams_material
plist.set
plist.get
renderer.text
renderer.measure_text
renderer.rectangle
renderer.line
renderer.gradient
renderer.circle
renderer.circle_outline
renderer.triangle
renderer.world_to_screen
renderer.indicator
renderer.texture
renderer.load_svg
renderer.load_png
renderer.load_jpg
renderer.load_rgba
ui.new_checkbox
ui.new_slider
ui.new_combobox
ui.new_multiselect
ui.new_hotkey
ui.new_button
ui.new_color_picker
ui.new_textbox
ui.new_listbox
ui.new_string
ui.new_label
ui.reference
ui.set
ui.get
ui.set_callback
ui.set_visible
ui.is_menu_open
ui.mouse_position
ui.menu_position
ui.menu_size
ui.name
client.set_event_callback
syntax: client.set_event_callback(event_name, callback)

event_name - Name of the event.

callback - Lua function to call when this event occurs.

Raises an error and prints a message in console upon failure.

Back to TOC


client.unset_event_callback
syntax: client.unset_event_callback(event_name, callback)

event_name - Name of the event

callback - Lua function that was passed to set_event_callback

Removes a callback that was previously set using set_event_callback

Back to TOC


client.log
syntax: client.log(msg, ...)

msg - The message

... - Optional comma-separated arguments to concatenate with msg.

Back to TOC


client.color_log
syntax: client.color_log(r, g, b, msg, ...)

r - Red (0-255)

g - Green (0-255)

b - Blue (0-255)

msg - The message

... - Optional comma-separated arguments to concatenate with msg.

Back to TOC


client.error_log
syntax: client.error_log(msg)

msg - The error message

Back to TOC


client.exec
syntax: client.exec(cmd, ...)

cmd - The console command(s) to execute.

... - Optional comma-separated arguments to concatenate with cmd.

Back to TOC


client.userid_to_entindex
syntax: client.userid_to_entindex(userid)

userid - This is given by some game events.

Returns the entity index, or 0 on failure.

Back to TOC


client.draw_debug_text
syntax: client.draw_debug_text(x, y, z, line_offset, duration, r, g, b, a, ...)

x - Position in world space

y - Position in world space

z - Position in world space

line_offset - Used for vertical alignment, use 0 for the first line.

duration - Time in seconds that the text will remain on the screen.

r - Red (1-255)

g - Green (1-255)

b - Blue (1-255)

a - Alpha (1-255)

... - The text that will be drawn

Avoid calling this during the paint event.

Back to TOC


client.draw_hitboxes
syntax: client.draw_hitboxes(entindex, duration, hitboxes, r, g, b, a, tick)

entindex - Entity index

duration - Time in seconds

hitboxes - Either the hitbox index, an array of hitbox indices, or 19 for all hitboxes

r - Red (1-255)

g - Green (1-255)

b - Blue (1-255)

a - Alpha (1-255)

tick - Optional integer

Draws hitbox overlays. Avoid calling this during the paint event.

Back to TOC


client.random_int
syntax: client.random_int(minimum, maximum)

minimum - Lowest possible result

maximum - Highest possible result

Returns a random integer between minimum and maximum.

Back to TOC


client.random_float
syntax: client.random_float(minimum, maximum)

minimum - Lowest possible result

maximum - Highest possible result

Returns a random float between minimum and maximum.

Back to TOC


client.screen_size
syntax: client.screen_size()

Returns (width, height).

Back to TOC


client.visible
syntax: client.visible(x, y, z)

x - Position in world space

y - Position in world space

z - Position in world space

Returns true if the position is visible. For example, you could use a player's origin to see if they are visible.

Back to TOC


client.trace_line
syntax: client.trace_line(skip_entindex, from_x, from_y, from_z, to_x, to_y, to_z)

skip_entindex - Ignore this entity while tracing

from_x - Position in world space

from_y - Position in world space

from_z - Position in world space

to_x - Position in world space

to_y - Position in world space

to_z - Position in world space

Returns fraction, entindex. fraction is a percentage in the range [0.0, 1.0] that tells you how far the trace went before hitting something, so 1.0 means nothing was hit. entindex is the entity index that hit, or -1 if no entity was hit.

Back to TOC


client.trace_bullet
syntax: client.trace_bullet(from_player, from_x, from_y, from_z, to_x, to_y, to_z, skip_players)

from_player - Entity index of the player whose weapon will be used for this trace

from_x - Position in world space

from_y - Position in world space

from_z - Position in world space

to_x - Position in world space

to_y - Position in world space

to_z - Position in world space

skip_players - Optional, pass true to skip expensive hitbox checks.

Returns entindex, damage. Entindex is nil when no player is hit or if players are skipped.

Back to TOC


client.scale_damage
syntax: client.scale_damage(entindex, hitgroup, damage)

entindex - Player entity index

hitgroup - Hit group index

damage - Damage

Returns adjusted damage for the specified hitgroup

Back to TOC


client.delay_call
syntax: client.delay_call(delay, callback, ...)

delay - Time in seconds to wait before calling callback.

callback - The lua function that will be called after delay seconds.

... - Optional arguments that will be passed to the callback.

Back to TOC


client.latency
syntax: client.latency()

Returns your latency in seconds.

Back to TOC


client.camera_angles
syntax: client.camera_angles()

Returns pitch, yaw, roll of where you are looking.

Back to TOC


client.camera_position
syntax: client.camera_position()

Returns x, y, z world coordinates of the camera position.

Back to TOC


client.timestamp
syntax: client.timestamp()

Returns high precision timestamp in milliseconds.

Back to TOC


client.eye_position
syntax: client.eye_position()

Returns x, y, z world coordinates of the local player's eye position, or nil on failure.

Back to TOC


client.set_clan_tag
syntax: client.set_clan_tag(...)

... - The text that will be drawn

The clan tag is removed if no argument is passed or if it is an empty string. Additional arguments will be concatenated similar to client.log.

Back to TOC


client.system_time
syntax: client.system_time()

Returns hour, minute, seconds, milliseconds.

local h, m, s, ms = client.system_time()

Back to TOC


client.unix_time
syntax: client.unix_time()

Returns hour, minute, seconds, milliseconds.

local time = client.unix_time()

Back to TOC


client.reload_active_scripts
syntax: client.reload_active_scripts()

Reloads all scripts the following frame.

Back to TOC


client.create_interface
syntax: client.create_interface(module_name, interface_name)

module_name - Filename of the module that contains the interface

interface_name - Name of the interface

Returns a pointer to the interface, or nil on failure.

Back to TOC


client.find_signature
syntax: client.find_signature(module_name, pattern)

module_name - Filename of the module that contains the interface

pattern - String in the form of '\x01\x02\xCC\x03'

Finds the specified pattern and returns its address, or nil if not found. CC is wildcard.

Back to TOC


client.key_state
syntax: client.key_state(virtual_key)

virtual_key - Virtual key index

Returns true if the key is pressed.

Back to TOC


client.get_model_name
syntax: client.get_model_name(model_index)

model_index - Model index

Returns model name, or nil on failure.

Back to TOC


client.register_esp_flag
syntax: client.register_esp_flag(flag, r, g, b, callback)

flag - String of text that will be shown when callback returns true

r - Red (1-255)

g - Green (1-255)

b - Blue (1-255)

callback - Function that will be called for each entity while drawing the ESP

Requires "Flags" is enabled in Player ESP

Back to TOC


config.load
syntax: config.load(name, tab_name, container_name)

name - Name of the config

tab_name - Optional name of the tab

container_name - Optional name of the container

To load the specified config: config.load('Config name here') To load a tab from the specified config: config.load('Config name here', 'Tab name here') To load a container from the specified config: config.load('Config name here', 'Tab name here', 'Container name here')

Back to TOC


config.export
syntax: config.export()

Returns the current config as a string

Back to TOC


cvar.set_string
syntax: cvar.set_string(value)

value - String value

Back to TOC


cvar.get_string
syntax: cvar.get_string()

Returns nil on failure.

Back to TOC


cvar.set_float
syntax: cvar.set_float(value)

value - Float value

cvar.cl_interp_ratio:set_float(1)

Back to TOC


cvar.set_raw_float
syntax: cvar.set_raw_float(value)

value - Float value

This sets the float value without changing the integer and string values.

Back to TOC


cvar.get_float
syntax: cvar.get_float()

Returns nil if called on a ConCommand.

Back to TOC


cvar.set_int
syntax: cvar.set_int(value)

value - Integer value

Back to TOC


cvar.set_raw_int
syntax: cvar.set_raw_int(value)

value - Integer value

This sets the integer value without changing the float and string values.

Back to TOC


cvar.get_int
syntax: cvar.get_int()

Returns nil if called on a ConCommand.

Back to TOC


cvar.invoke_callback
syntax: cvar.invoke_callback()

For ConCommands, optionally pass extra arguments and they will be forwarded to the callback. For ConVars, optionally pass an extra integer argument specifying the index of the change callback to invoke, otherwise all change callbacks will be invoked.

cvar.snd_setmixer:invoke_callback("Ambient", "vol", "0") -- equivalent to typing "snd_setmixer Ambient vol 0" in console

Back to TOC


database.write
syntax: database.write(key, value)

key - Name of the database, must be a string

value - Value or table

Saves a persistent table, possibly overwriting any existing data

Back to TOC


database.read
syntax: database.read(key)

key - Unique string identifier

Returns a table

Back to TOC


entity.get_local_player
syntax: entity.get_local_player()

Returns the entity index for the local player, or nil on failure.

Back to TOC


entity.get_all
syntax: entity.get_all(classname)

classname - Optional string that specifies the class name of entities that will be added to the list, for example "CCSPlayer".

Returns an array of entity indices. Pass no arguments for all entities.

Back to TOC


entity.get_players
syntax: entity.get_players(enemies_only)

enemies_only - Optional. If true then you and the players on your team will not be added to the list.

Returns an array of player entity indices. Dormant and dead players will not be added to the list.

Back to TOC


entity.get_game_rules
syntax: entity.get_game_rules()

Returns entity index of CCSGameRulesProxy instance, or nil if none exists.

Back to TOC


entity.get_player_resource
syntax: entity.get_player_resource()

Returns entity index of CCSPlayerResource instance, or nil if none exists.

Back to TOC


entity.get_classname
syntax: entity.get_classname(ent)

ent - Entity index.

Returns the name of the entity's class, or nil on failure.

Back to TOC


entity.set_prop
syntax: entity.set_prop(ent, propname, value, array_index)

ent - Entity index.

propname - Name of the networked property.

value - The property will be set to this value. For vectors or angles, separate the components by commas.

array_index - Optional. If propname is an array, the value at this array index will be set.

Back to TOC


entity.get_prop
syntax: entity.get_prop(ent, propname, array_index)

ent - Entity index.

propname - Name of the networked property.

array_index - Optional. If propname is an array, the value at this array index will be returned.

Returns the value of the property, or nil on failure. For vectors or angles, this returns three values.

Back to TOC


entity.is_enemy
syntax: entity.is_enemy(ent)

ent - Entity index.

Returns true if the entity is on the other team.

Back to TOC


entity.is_alive
syntax: entity.is_alive(ent)

ent - Entity index.

Returns true if the player is not dead.

Back to TOC


entity.is_dormant
syntax: entity.is_dormant(ent)

ent - Entity index.

Returns true if the player is not dormant.

Back to TOC


entity.get_player_name
syntax: entity.get_player_name(ent)

ent - Player entity index.

Returns the player's name, or the string "unknown" on failure.

Back to TOC


entity.get_player_weapon
syntax: entity.get_player_weapon(ent)

ent - Player entity index.

Returns the entity index of the player's active weapon, or nil if the player is not alive, dormant, etc.

Back to TOC


entity.hitbox_position
syntax: entity.hitbox_position(player, hitbox)

player - Entity index of the player.

hitbox - Either a string of the hitbox name, or an integer index of the hitbox.

Returns world coordinates x, y, z, or nil on failure.

Back to TOC


entity.get_steam64
syntax: entity.get_steam64(player)

player - Entity index of the player.

Returns steamID3, or nil on failure.

Back to TOC


entity.get_bounding_box
syntax: entity.get_bounding_box(player)

player - Entity index of the player.

Returns x1, y1, x2, y2, alpha_multiplier. The contents of x1, y1, x2, y2 must be ignored when alpha_multiplier is zero, which indicates that the bounding box is invalid and should not be drawn.

Back to TOC


entity.get_origin
syntax: entity.get_origin(player)

player - Entity index

Returns x, y, z world coordinates of the entity's origin, or nil if the entity is dormant and dormant ESP information is not available.

Back to TOC


entity.get_esp_data
syntax: entity.get_esp_data(player)

player - Entity index

Returns a table containing alpha, health, and weapon_id, or nil on failure.

Back to TOC


globals.realtime
syntax: globals.realtime()

Returns the local time in seconds.

Back to TOC


globals.curtime
syntax: globals.curtime()

Returns the game time in seconds. This number is synchronized with the server.

Back to TOC


globals.frametime
syntax: globals.frametime()

Returns the number of seconds elapsed during the last game frame.

Back to TOC


globals.absoluteframetime
syntax: globals.absoluteframetime()

Returns the number of seconds elapsed during the last game frame.

Back to TOC


globals.maxplayers
syntax: globals.maxplayers()

Returns the maximum number of players in the server.

Back to TOC


globals.tickcount
syntax: globals.tickcount()

Returns the number of ticks elapsed in the server.

Back to TOC


globals.tickinterval
syntax: globals.tickinterval()

Returns the time elapsed in one game tick in seconds.

Back to TOC


globals.framecount
syntax: globals.framecount()

Returns the number of frames since the game started

Back to TOC


globals.mapname
syntax: globals.mapname()

Returns the name of the loaded map, or nil if you are not in game.

Back to TOC


globals.lastoutgoingcommand
syntax: globals.lastoutgoingcommand()

Returns the command number of the last outgoing command.

Back to TOC


globals.oldcommandack
syntax: globals.oldcommandack()

Returns the command number of the previous server-acknowledged command.

Back to TOC


globals.commandack
syntax: globals.commandack()

Returns the command number of the most recent server-acknowledged command.

Back to TOC


globals.chokedcommands
syntax: globals.chokedcommands()

Returns the number of choked commands, i.e. the number of commands that haven't yet been sent to the server.

Back to TOC


panorama.open
syntax: panorama.open(panel)

panel - Optional panel name

Back to TOC


panorama.loadstring
syntax: panorama.loadstring(js_code, panel)

js_code - String containing JavaScript code

panel - Optional panel name

Back to TOC


materialsystem.get_name
syntax: materialsystem.get_name()

Returns name of the material

Back to TOC


materialsystem.reload
syntax: materialsystem.reload()

Resets the material

Back to TOC


materialsystem.color_modulate
syntax: materialsystem.color_modulate(r, g, b)

r - Red (0-255)

g - Green (0-255)

b - Blue (0-255)

Back to TOC


materialsystem.alpha_modulate
syntax: materialsystem.alpha_modulate(alpha)

alpha - Opacity (0-255)

Back to TOC


materialsystem.set_shader_param
syntax: materialsystem.set_shader_param(param_name, value, force)

param_name - Name of the shader parameter

value - New value

force - Optional boolean. Add the var if it does not exist in the material

Back to TOC


materialsystem.get_shader_param
syntax: materialsystem.get_shader_param(param_name)

param_name - Name of the shader parameter

Back to TOC


materialsystem.set_material_var_flag
syntax: materialsystem.set_material_var_flag(index, enabled)

index - Index of MaterialVarFlags_t

enabled - Boolean

Back to TOC


materialsystem.get_material_var_flag
syntax: materialsystem.get_material_var_flag(index)

index - Index of MaterialVarFlags_t

Returns true if the specified flag is set

Back to TOC


materialsystem.find_material
syntax: materialsystem.find_material(path, force_load)

path - Path to material including filename

force_load - Optional boolean. Load the material if it isn't loaded

Returns a reference to the material

Back to TOC


materialsystem.find_materials
syntax: materialsystem.find_materials(partial_path, force_load)

partial_path - Partial path to material

force_load - Optional boolean. Load each material if it isn't loaded

Returns a table of references to materials that have partial_path in their name

Back to TOC


materialsystem.find_texture
syntax: materialsystem.find_texture(path)

path - Path to texture including filename

Returns a reference to the texture that can be used with set_shader_param

Back to TOC


materialsystem.get_model_materials
syntax: materialsystem.get_model_materials(entindex)

entindex - Entity index

Returns a table of references to materials used by the entity

Back to TOC


materialsystem.arms_material
syntax: materialsystem.arms_material()

Returns a reference to the arms material when 'Viewmodel arms' is enabled

Back to TOC


materialsystem.chams_material
syntax: materialsystem.chams_material()

Returns a reference to the player chams material

Back to TOC


plist.set
syntax: plist.set(entindex, field, value)

entindex - Player index

field - Name of the field

value - Value of the field

Back to TOC


plist.get
syntax: plist.get(entindex, field)

entindex - Player index

field - Name of the field

Back to TOC


renderer.text
syntax: renderer.text(x, y, r, g, b, a, flags, max_width, ...)

x - Screen coordinate

y - Screen coordinate

r - Red (0-255)

g - Green (0-255)

b - Blue (0-255)

a - Alpha (0-255)

flags - "+" for large text, "-" for small text, "c" for centered text, "r" for right-aligned text, "b" for bold text, "d" for high DPI support. "c" can be combined with other flags. nil can be specified for normal sized uncentered text.

max_width - Text will be clipped if it exceeds this width in pixels. Use 0 for no limit.

... - Text that will be drawn

This can only be called from the paint callback.

Back to TOC


renderer.measure_text
syntax: renderer.measure_text(flags, ...)

flags - "+" for large text, "-" for small text, or nil for normal sized text.

... - Text that will be measured

Returns width, height. This can only be called from the paint callback.

Back to TOC


renderer.rectangle
syntax: renderer.rectangle(x, y, w, h, r, g, b, a)

x - Screen coordinate

y - Screen coordinate

w - Width in pixels

h - Height in pixels

r - Red (0-255)

g - Green (0-255)

b - Blue (0-255)

a - Alpha (0-255)

This can only be called from the paint callback.

Back to TOC


renderer.line
syntax: renderer.line(xa, ya, xb, yb, r, g, b, a)

xa - Screen coordinate of point A

ya - Screen coordinate of point A

xb - Screen coordinate of point B

yb - Screen coordinate of point B

r - Red (0-255)

g - Green (0-255)

b - Blue (0-255)

a - Alpha (0-255)

This can only be called from the paint callback.

Back to TOC


renderer.gradient
syntax: renderer.gradient(x, y, w, h, r1, g1, b1, a1, r2, g2, b2, a2, ltr)

x - Screen coordinate

y - Screen coordinate

w - Width in pixels

h - Height in pixels

r1 - Red (0-255)

g1 - Green (0-255)

b1 - Blue (0-255)

a1 - Alpha (0-255)

r2 - Red (0-255)

g2 - Green (0-255)

b2 - Blue (0-255)

a2 - Alpha (0-255)

ltr - Left to right. Pass true for horizontal gradient, or false for vertical.

This can only be called from the paint callback.

Back to TOC


renderer.circle
syntax: renderer.circle(x, y, r, g, b, a, radius, start_degrees, percentage)

x - Screen coordinate

y - Screen coordinate

r - Red (0-255)

g - Green (0-255)

b - Blue (0-255)

a - Alpha (0-255)

radius - Radius of the circle in pixels.

start_degrees - 0 is the right side, 90 is the bottom, 180 is the left, 270 is the top.

percentage - Must be within [0.0-1.0]. 1.0 is a full circle, 0.5 is a half circle, etc.

This can only be called from the paint callback.

Back to TOC


renderer.circle_outline
syntax: renderer.circle_outline(x, y, r, g, b, a, radius, start_degrees, percentage, thickness)

x - Screen coordinate

y - Screen coordinate

r - Red (0-255)

g - Green (0-255)

b - Blue (0-255)

a - Alpha (0-255)

radius - Radius of the circle in pixels.

start_degrees - 0 is the right side, 90 is the bottom, 180 is the left, 270 is the top.

percentage - Must be within [0.0-1.0]. 1.0 is a full circle, 0.5 is a half circle, etc.

thickness - Thickness of the outline in pixels.

This can only be called from the paint callback.

Back to TOC


renderer.triangle
syntax: renderer.triangle(x0, y0, x1, y1, x2, y2, r, g, b, a)

x0 - Screen coordinate X for point A

y0 - Screen coordinate Y for point A

x1 - Screen coordinate X for point B

y1 - Screen coordinate Y for point B

x2 - Screen coordinate X for point C

y2 - Screen coordinate Y for point C

r - Red (0-255)

g - Green (0-255)

b - Blue (0-255)

a - Alpha (0-255)

This can only be called from the paint callback.

Back to TOC


renderer.world_to_screen
syntax: renderer.world_to_screen(x, y, z)

x - Position in world space

y - Position in world space

z - Position in world space

Returns two screen coordinates (x, y), or nil if the world position is not visible on your screen. This can only be called from the paint callback.

Back to TOC


renderer.indicator
syntax: renderer.indicator(r, g, b, a, ...)

r - Red (0-255)

g - Green (0-255)

b - Blue (0-255)

a - Alpha (0-255)

... - The text that will be drawn

Returns the Y screen coordinate (vertical offset) of the drawn text, or nil on failure. This can only be called from the paint callback.

Back to TOC


renderer.texture
syntax: renderer.texture(id, x, y, w, h, r, g, b, a, mode)

id - Texture ID

x - X screen coordinate

y - Y screen coordinate

w - Width

h - Height

r - Red (0-255)

g - Green (0-255)

b - Blue (0-255)

a - Alpha (1-255)

mode - Optional string: "f" for fill, "r" for repeat, otherwise automatic

In fill mode, the texture will be stretched to the specified size. This may cause textures to appear blurry if the specified size is not the same as the texture's size. In repeat mode, the texture will be tiled.

Back to TOC


renderer.load_svg
syntax: renderer.load_svg(contents, width, height)

contents - SVG file contents

width - Width

height - Height

Returns a texture ID that can be used with renderer.texture, or nil on failure

Back to TOC


renderer.load_png
syntax: renderer.load_png(contents, width, height)

contents - PNG file contents

width - Width

height - Height

Returns a texture ID that can be used with renderer.texture, or nil on failure

Back to TOC


renderer.load_jpg
syntax: renderer.load_jpg(contents, width, height)

contents - JPG file contents

width - Width

height - Height

Returns a texture ID that can be used with renderer.texture, or nil on failure

Back to TOC


renderer.load_rgba
syntax: renderer.load_rgba(contents, width, height)

contents - RGBA buffer

width - Width

height - Height

Returns a texture ID that can be used with renderer.texture, or nil on failure

Back to TOC


ui.new_checkbox
syntax: ui.new_checkbox(tab, container, name)

tab - The name of the tab: RAGE, AA, LEGIT, VISUALS, MISC, SKINS, PLAYERS, LUA.

container - The name of the existing container to which this control will be added.

name - The name of the checkbox.

Returns a special value that can be passed to ui.get and ui.set, or throws an error on failure.

Back to TOC


ui.new_slider
syntax: ui.new_slider(tab, container, name, min, max, init_value, show_tooltip, unit, scale, tooltips)

tab - The name of the tab: RAGE, AA, LEGIT, VISUALS, MISC, SKINS, PLAYERS, LUA.

container - The name of the existing container to which this control will be added.

name - The name of the slider.

min - The minimum value that can be set using the slider.

max - The maximum value that can be set using the slider.

init_value - Optional integer. The initial value. If not provided, the initial value will be min.

show_tooltip - Optional boolean. true if the slider should display its current value.

unit - Optional string that is two characters or less. This will be appended to the display value. For example, "px" for pixels or "%" for a percentage.

scale - Optional The display value will be multiplied by this scale. For example, 0.1 will make a slider with the range [0-1800] show as 0.0-180.0 with one decimal place.

tooltips - Optional table used to override the tooltip for the specified values. The key must be within min-max. The value is a string that will be shown instead of the numeric value whenever that value is selected.

Returns a special value that can be passed to ui.get and ui.set, or throws an error on failure.

Back to TOC


ui.new_combobox
syntax: ui.new_combobox(tab, container, name, ...)

tab - The name of the tab: RAGE, AA, LEGIT, VISUALS, MISC, SKINS, PLAYERS, LUA.

container - The name of the existing container to which this control will be added.

name - The name of the combobox.

... - One or more comma separated string values that will be added to the combobox. Alternatively, a table of strings that will be added.

Returns a special value that can be passed to ui.get and ui.set, or throws an error on failure.

Back to TOC


ui.new_multiselect
syntax: ui.new_multiselect(tab, container, name, ...)

tab - The name of the tab: RAGE, AA, LEGIT, VISUALS, MISC, SKINS, PLAYERS, LUA.

container - The name of the existing container to which this control will be added.

name - The name of the multiselect.

... - One or more comma separated string values that will be added to the combobox. Alternatively, a table of strings that will be added.

Returns a special value that can be passed to ui.get and ui.set, or throws an error on failure.

Back to TOC


ui.new_hotkey
syntax: ui.new_hotkey(tab, container, name, inline, default_hotkey)

tab - The name of the tab: RAGE, AA, LEGIT, VISUALS, MISC, SKINS, PLAYERS, LUA.

container - The name of the existing container to which this control will be added.

name - The name of the hotkey.

inline - Optional boolean. If set to true, the hotkey will be placed to the right of the preceding menu item.

default_hotkey - Optional virtual key

Returns a special value that can be passed to ui.get to see if the hotkey is pressed, or throws an error on failure.

Back to TOC


ui.new_button
syntax: ui.new_button(tab, container, name, callback)

tab - The name of the tab: RAGE, AA, LEGIT, VISUALS, MISC, SKINS, PLAYERS, LUA.

container - The name of the existing container to which this checkbox will be added.

name - The name of the button.

callback - The lua function that will be called when the button is pressed.

Throws an error on failure. The return value should not be used with ui.set or ui.get.

Back to TOC


ui.new_color_picker
syntax: ui.new_color_picker(tab, container, name, r, g, b, a)

tab - The name of the tab: RAGE, AA, LEGIT, VISUALS, MISC, SKINS, PLAYERS, LUA.

container - The name of the existing container to which this checkbox will be added.

name - The name of the color picker. This will not be shown, it is only used to identify this item in saved configs.

r - Optional initial red value (0-255)

g - Optional initial green value (0-255)

b - Optional initial blue value (0-255)

a - Optional initial alpha value (0-255)

Throws an error on failure. The color picker is placed to the right of the previous menu item.

Back to TOC


ui.new_textbox
syntax: ui.new_textbox(tab, container, name)

tab - The name of the tab: RAGE, AA, LEGIT, VISUALS, MISC, SKINS, PLAYERS, LUA.

container - The name of the existing container to which this textbox will be added.

name - The name of the textbox

Throws an error on failure. Returns a special value that can be used with ui.get

Back to TOC


ui.new_listbox
syntax: ui.new_listbox(tab, container, name, items)

tab - The name of the tab: RAGE, AA, LEGIT, VISUALS, MISC, SKINS, PLAYERS, LUA

container - The name of the existing container to which this listbox will be added

name - Name

items - Optional table of items (strings)

Throws an error on failure. Returns a special value that can be used with ui.get. Calling ui.get on a listbox will return the zero-based index of the currently selected string.

Back to TOC


ui.new_string
syntax: ui.new_string(name, value)

name - Name

value - Optional string that specifies the default value.

Returns a special value that can be used with ui.get and ui.set. This function does not create any menu items. The value will be stored in configs just like other menu items.

Back to TOC


ui.new_label
syntax: ui.new_label(tab, container, name)

tab - The name of the tab: RAGE, AA, LEGIT, VISUALS, MISC, SKINS, PLAYERS, LUA

container - The name of the existing container to which this listbox will be added

name - Name

Returns a special value that can be used with ui.set

Back to TOC


ui.reference
syntax: ui.reference(tab, container, name)

tab - The name of the tab: RAGE, AA, LEGIT, VISUALS, MISC, SKINS, PLAYERS, LUA.

container - The name of the existing container to which this checkbox will be added.

name - The name of the menu item.

Avoid calling this from inside a function. Returns a reference that can be passed to ui.get and ui.set, or throws an error on failure. This allows you to access a built-in pre-existing menu items. This function returns multiple values when the specified menu item is followed by unnamed menu items, for example a color picker or a hotkey.

Back to TOC


ui.set
syntax: ui.set(item, value, ...)

item - The result of either ui.new_* or ui.reference

value - The value to which the menu item will be set

... - Optional. For multiselect comboboxes, you may want to set more than one option.

For checkboxes, pass true or false. For a slider, pass a number that is within the slider's minimum/maximum values. For a combobox, pass a string value. For a multiselect combobox, pass zero or more strings. For referenced buttons, value is ignored and the button's callback is invoked. For color pickers, pass the arguments r, g, b, a.

Back to TOC


ui.get
syntax: ui.get(item)

item - The special value returned by ui.new_checkbox, ui.new_slider, ui.new_combobox, ui.new_hotkey, or ui.reference.

For a checkbox, returns true or false. For a slider, returns an integer. For a combobox, returns a string. For a multiselect combobox, returns an array of strings. For a hotkey, returns true if the hotkey is active. For a color picker, returns r, g, b, a. Throws an error on failure.

Back to TOC


ui.set_callback
syntax: ui.set_callback(item, callback)

item - The special value returned by ui.new_*. Do not try passing a reference to an existing menu item.

callback - Lua function that will be called when the menu item changes values. For example, this will be called when the user checks or unchecks a checkbox.

item is passed as an argument to the callback function.

Back to TOC


ui.set_visible
syntax: ui.set_visible(item, visible)

item - A menu item reference.

visible - Boolean. Pass false to hide the control from the menu.

Back to TOC


ui.is_menu_open
syntax: ui.is_menu_open()

Returns true if the menu is currently open.

Back to TOC


ui.mouse_position
syntax: ui.mouse_position()

Returns current mouse coordinates x, y

Back to TOC


ui.menu_position
syntax: ui.menu_position()

Returns current window coordinates x, y

Back to TOC


ui.menu_size
syntax: ui.menu_size()

Returns current menu size width, height

Back to TOC


ui.name
syntax: ui.name(item)

item - Reference to menu item

Returns the display name

Back to TOC
