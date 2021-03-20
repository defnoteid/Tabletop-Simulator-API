Games frequently need to execute code in response to some action, interaction, or change taking place in the game,
collectively referred to as _events_.

## Event Handlers

Event handlers are **functions you define**, that Tabletop Simulator calls.

There are many event handlers that you can define. Each one gives you an opportunity to handle occurrences of a
particular event.

When Tabletop Simulator calls your function, it will provide event-specific details as arguments to your event handler
function.

In order for Tabletop Simulator to discover an event handler, it must be defined as a global variable with a specific
name. The name that you use depends on which event you wish to handle. Event-specific details are covered below.

!!!note
	Whilst event handler _names_ corresponds with just one type of event. Each event may have multiple corresponding
	event handlers (i.e. event handler names) that Tabletop Simulator will look for and execute.

There are two types of event handlers:

* [Universal Event Handlers](#universal-event-handlers)
* [Object Event Handlers](#object-event-handlers)

### Universal Event Handlers

Universal Event Handlers may be defined in the [Global script](intro.md#global-script) _and/or_
[Object scripts](intro.md#object-scripts).

### Object Event Handlers

Object Event Handlers may only be defined in [Object scripts](intro.md#object-scripts).

If you were to define a function using the name of an Object Event Handler in your
[Global script](intro.md#global-script). It simply won't be called.

## Event Handler Execution

_Typically_, if there are multiple event handlers exist for the one event i.e. in an Object script and Global
Script _and/or_ multiple Object scripts, then _all_ of these event handlers will be executed.

!!!info
	Some event handlers permit you to return a value in order to trigger an optional side effect. For example, returning
	`false` from a "try" event handler will prevent whatever action is being _tried_. If you return a value that
	triggers an optional side effect, then subsequent event handlers (for the same event occurrence) will _not_ be
	executed.

## Event Summary

### Universal Event Handlers {: #universal-event-handlers-summary }

As described above, you may declare these functions in the [Global script](intro.md#global-script) or in
[Object scripts](intro.md#object-scripts).

Function Name | Description | &nbsp;
-- | -- | --
filterObjectEnterContainer([<span class="tag obj"></span>](types.md) container, [<span class="tag obj"></span>](types.md) enter_object) | <p>[<span class="tag deprecated"></span>](intro.md#deprecated) _Use [tryObjectEnterContainer(...)](#tryobjectentercontainer)_.</p> Called when an object attempts to enter any container. | [:i:](#tryobjectentercontainer)
onChat([<span class="tag str"></span>](types.md) message, [<span class="tag pla"></span>](types.md) sender) | Called when a chat message is sent in game chat. | [:i:](#onchat)
onExternalMessage([<span class="tag tab"></span>](types.md) data) | Called when an external script editor (like [Atom](atom.md)) sends a message back to the game. Used for custom editor functionality. | [:i:](#onexternalmessage)
onFixedUpdate() | Called **every physics tick** (90 times a second). This is a frame independent onUpdate(). | [:i:](#onfixedupdate)
onLoad([<span class="tag str"></span>](types.md) script_state) | Called when a save has completely finished loading. | [:i:](#onload)
onObjectCollisionEnter([<span class="tag obj"></span>](types.md) registered_object, [<span class="tag tab"></span>](types.md) collision_info) | Called when an Object starts colliding with a [collision registered](object.md#registercollisions) Object. | [:i:](#onobjectcollisionenter)
onObjectCollisionExit([<span class="tag obj"></span>](types.md) registered_object, [<span class="tag tab"></span>](types.md) collision_info) | Called when an Object stops colliding with a [collision registered](object.md#registercollisions) Object. | [:i:](#onobjectcollisionexit)
onObjectCollisionStay([<span class="tag obj"></span>](types.md) registered_object, [<span class="tag tab"></span>](types.md) collision_info) | Called **every frame** that an Object is colliding with a [collision registered](object.md#registercollisions) Object. | [:i:](#onobjectcollisionstay)
onObjectDestroy([<span class="tag obj"></span>](types.md) dying_object) | Called whenever any object is destroyed. | [:i:](#onobjectdestroy)
onObjectDrop([<span class="tag str"></span>](types.md) player_color, [<span class="tag obj"></span>](types.md) dropped_object) | Called whenever any object is dropped by a player. | [:i:](#onobjectdrop)
onObjectEnterScriptingZone([<span class="tag obj"></span>](types.md) zone, [<span class="tag obj"></span>](types.md) enter_object) | Called when any object enters any scripting zone. | [:i:](#onobjectenterscriptingzone)
onObjectEnterContainer([<span class="tag obj"></span>](types.md) container, [<span class="tag obj"></span>](types.md) enter_object) | Called when any object enters any container. Includes decks | [:i:](#onobjectentercontainer)
onObjectFlick([<span class="tag obj"></span>](types.md) object, [<span class="tag str"></span>](types.md) player_color, [<span class="tag vec"></span>](types.md) impulse) | Called when a player flicks an object. | [:i:](#onobjectflick)
onObjectHover([<span class="tag str"></span>](types.md) player_color, [<span class="tag obj"></span>](types.md) hovered_object) | Called when a player moves their pointer (cursor) over an object. | [:i:](#onobjecthover)
onObjectLeaveScriptingZone([<span class="tag obj"></span>](types.md) zone, [<span class="tag obj"></span>](types.md) enter_object) | Called when any object leaves any scripting zone. | [:i:](#onobjectleavescriptingzone)
onObjectLeaveContainer([<span class="tag obj"></span>](types.md) container, [<span class="tag obj"></span>](types.md) leave_object) | Called when any object leaves any container. | [:i:](#onobjectleavecontainer)
onObjectLoopingEffect([<span class="tag obj"></span>](types.md) loop_object, [<span class="tag int"></span>](types.md) index) | Called whenever the looping effect of an [AssetBundle](behavior/assetbundle.md) is activated. | [:i:](#onobjectloopingeffect)
onObjectNumberTyped([<span class="tag obj"></span>](types.md) object, [<span class="tag str"></span>](types.md) player_color, [<span class="tag int"></span>](types.md) number) | Called when a player types a number whilst hovering over an object. | [:i:](#onobjectnumbertyped)
onObjectPageChange([<span class="tag obj"></span>](types.md) object) | Called when a Custom PDF object changes page. | [:i:](#onobjectpagechange)
onObjectPeek([<span class="tag obj"></span>](types.md) object, [<span class="tag str"></span>](types.md) player) | Called when a player using peek to look under an Object. | [:i:](#onobjectpeek)
onObjectPickUp([<span class="tag str"></span>](types.md) player_color, [<span class="tag obj"></span>](types.md) picked_up_object) | Called whenever a Player picks up an Object. | [:i:](#onobjectpickup)
onObjectRandomize([<span class="tag obj"></span>](types.md) randomize_object, [<span class="tag str"></span>](types.md) player_color) | Called when an Object is randomized. Like when shuffling a deck or shaking dice. | [:i:](#onobjectrandomize)
onObjectSearchEnd([<span class="tag obj"></span>](types.md) obj, [<span class="tag str"></span>](types.md) player_color) | Called when a search is finished on any container. | [:i:](#onobjectsearchend)
onObjectSearchStart([<span class="tag obj"></span>](types.md) obj, [<span class="tag str"></span>](types.md) player_color) | Called when a search is started on any container. | [:i:](#onobjectsearchstart)
onObjectSpawn([<span class="tag obj"></span>](types.md) spawn_object) | Called when any Object is spawned/created. | [:i:](#onobjectspawn)
onObjectTriggerEffect([<span class="tag obj"></span>](types.md) trigger_object, [<span class="tag int"></span>](types.md) index) | Called whenever the trigger effect of an [AssetBundle](behavior/assetbundle.md) is activated. | [:i:](#onobjecttriggereffect)
onPlayerChangeColor([<span class="tag str"></span>](types.md) player_color) | Called when a player changes color or selects it for the first time. It also returns `"Grey"` if they disconnect. | [:i:](#onplayerchangecolor)
onPlayerChangeTeam([<span class="tag str"></span>](types.md) player_color,&nbsp;[<span class="tag str"></span>](types.md) team) | Called when a player changes team. | [:i:](#onplayerchangeteam)
onPlayerConnect([<span class="tag pla"></span>](types.md) person) | Called when a [Player](player/instance.md) connects to a game. | [:i:](#onplayerconnect)
onPlayerDisconnect([<span class="tag pla"></span>](types.md) person) | Called when a [Player](player/instance.md) disconnects from a game. | [:i:](#onplayerdisconnect)
onPlayerTurn([<span class="tag pla"></span>](types.md) person) | Called at the start of a player's turn when using the in-game turn system. | [:i:](#onplayerturn)
onSave() | Called whenever a script needs to save its state. | [:i:](#onsave)
onScriptingButtonDown([<span class="tag int"></span>](types.md) index, [<span class="tag str"></span>](types.md) player_color) | Called when a scripting button (numpad by default) is pressed. The index range that is returned is 1-10. | [:i:](#onscriptingbuttondown)
onScriptingButtonUp([<span class="tag int"></span>](types.md) index, [<span class="tag str"></span>](types.md) player_color) | Called when a scripting button (numpad by default) is released. The index range that is returned is 1-10. | [:i:](#onscriptingbuttonup)
onUpdate() | Called **every frame**. | [:i:](#onupdate)
tryObjectEnterContainer([<span class="tag obj"></span>](types.md) container, [<span class="tag obj"></span>](types.md) entering_object) | Called when an object attempts to enter any container. | [:i:](#tryobjectentercontainer)

### Object Event Handlers {: #object-event-handlers-summary }

As described [above](#object-event-handlers), you may declare these functions in the
[Object scripts](intro.md#object-scripts).

!!!important
	These **cannot** declare these event handlers in the [Global script](intro.md#global-script).

Function Name | Description | &nbsp;
-- | -- | --
filterObjectEnter([<span class="tag obj"></span>](types.md) obj) | <p>[<span class="tag deprecated"></span>](intro.md#deprecated) _Use [tryObjectEnter(...)](#tryobjectenter)_.</p> Called when an object attempts to enter this object. Return `false` to prevent the object entering. | [:i:](#tryObjectenter)
onCollisionEnter([<span class="tag tab"></span>](types.md) collision_info) | Called when an Object starts colliding with the Object the function is on. | [:i:](#oncollisionenter)
onCollisionExit([<span class="tag tab"></span>](types.md) collision_info) | Called when an Object stops colliding with the Object the function is on. | [:i:](#oncollisionexit)
onCollisionStay([<span class="tag tab"></span>](types.md) collision_info) | Called **every frame** that an Object is colliding with the Object This event handler is on. | [:i:](#oncollisionstay)
onDestroy() | Called when an Object it is on is destroyed. | [:i:](#ondestroy)
onDrop([<span class="tag str"></span>](types.md) player_color) | Called when a player releases an Object after picking it up. | [:i:](#ondrop)
onFlick([<span class="tag str"></span>](types.md) player_color, [<span class="tag vec"></span>](types.md) impulse) | Called when a player flicks the object. | [:i:](#onflick)
onHover([<span class="tag str"></span>](types.md) player_color) | Called when a player moves their pointer (cursor) over the object. | [:i:](#onhover)
onNumberTyped([<span class="tag str"></span>](types.md) player_color, [<span class="tag int"></span>](types.md) number) | Called when a player types a number whilst hovering over the object. | [:i:](#onnumbertyped)
onPageChange() | Called when a Custom PDF page is changed. | [:i:](#onpagechange)
onPeek([<span class="tag str"></span>](types.md) player_color) | Called when a player using peek to look under this Object. | [:i:](#onpeek)
onPickUp([<span class="tag str"></span>](types.md) player_color) | Called when a player picks up an Object. | [:i:](#onpickup)
onRandomize([<span class="tag str"></span>](types.md) player_color) | Called when this Object is randomized. Like when shuffling a deck or shaking dice. | [:i:](#onrandomize)
onSearchEnd([<span class="tag str"></span>](types.md) player_color) | Called when a player finishes searches this Object. | [:i:](#onsearchend)
onSearchStart([<span class="tag str"></span>](types.md) player_color) | Called when a player starts searching this Object. | [:i:](#onsearchstart)
tryObjectEnter([<span class="tag obj"></span>](types.md) entering_object) | Called when another object attempts to enter this Object (container). Return `false` to prevent the object entering. | [:i:](#tryObjectenter)

---

## Universal Event Handler Details

###onChat(...)

This function is called when a message is sent through the in-game chat. It does not trigger when global chat messages are sent. Using `#!lua return false` inside of this function prevents the chat message which triggered it to be suppressed.

!!!info "onChat(message, sender)"
	* [<span class="tag str"></span>](types.md) **message**: Chat message which triggered the function.
	* [<span class="tag pla"></span>](types.md) **sender**: Player which sent the chat message.

``` Lua
function onChat(message, player)
	print(message)
	print(player.color)
end
```

---


###onExternalMessage(...)

This function is called when an external script editor (like [Atom](atom.md)) sends a message back to the game. Used for custom editor functionality.

!!!info "onExternalMessage(data)"
	* [<span class="tag tab"></span>](types.md) **data**: The data returned by the external editor into the game.

``` Lua
function onExternalMessage(data)
	print("External message received")
end
```

---


###onFixedUpdate()

Called **every physics tick** (90 times a second). This is a frame independent onUpdate().

!!!warning
	This is a very expensive function and can easily slow/crash your game if misused. Use with caution.

``` Lua
function onFixedUpdate()
	self.addTorque({0,100,0}, 1)
end
```


###onLoad(...)

**Global Script**

Called when a saved game (and all Objects it contains) have finished loading. This includes manually loaded games/saves,
as well as when a user rewinds.

**Object Script**

This will be called when a saved game finishes loading _or_ when the script-owner Object has finished loading for some
other reason e.g. if the script-owner Object was pulled out of a container mid-game.

!!!info "onLoad(script_state)"
	* [<span class="tag str"></span>](types.md) **script_state**: The previously saved script state i.e. value returned
	from [onSave(...)](#onsave), or an empty string if there is no saved script state available.


!!!example
	Decodes a JSON representation of a game state, consisting of nested tables, strings, numbers and object GUIDs. Then
	obtains an object reference from the saved GUID.
	```lua
    local some_object -- We'll store an object reference to use later.

	function onLoad(script_state)
		-- JSON decode our saved state
		local state = JSON.decode(script_state)

		-- In this example, we're assuming the existence of some specific saved state data.
		local questions = state.questions -- access a nested table

		for _, qa in ipairs(state.questions) do
			print("Question: " .. qa.question)
			print("Answer: " .. qa.answer)
		end

		some_object = getObjectFromGUID(state.guids.some_object)

		-- Let's highlight some_object a random color.
		-- Because why not.

		local colors = {'Blue', 'Yellow', 'Green'}
		some_object.highlightOn(colors[math.random(1, 3)])

		return JSON.encode(state)
	end
	```
	Refer to [onSave(...)](#onsave) to see an example of how this same save state structure could be created. Subscribe
	to the [example mod](https://steamcommunity.com/sharedfiles/filedetails/?id=2430471959) to see this in action.
---

###onObjectCollisionEnter(...)

This function is called when an Object starts colliding with a [collision registered](object.md#registercollisions) Object.

!!!info "onObjectCollisionEnter(registered_object, collision_info)"
	* [<span class="tag obj"></span>](types.md) **registered_object**: The object registered to receive collision events.
	* [<span class="tag tab"></span>](types.md) **collision_info**: A table containing data about the collision.
		* [<span class="tag obj"></span>](types.md) **collision_info.*collision_object***: Object coming into contact with `registered_object`.
		* [<span class="tag tab"></span>](types.md) **collision_info.*contact_points***: Table/array full of contact points, where each 3D point is represented by a (number indexed) table, _not_ a [Vector](vector.md).
		* [<span class="tag tab"></span>](types.md) **collision_info.*relative_velocity***: Table (number indexed) representation of a 3D vector (but _not_ a [Vector](vector.md)) indicating the direction and magnitude of the collision.

``` Lua
-- Example Usage
function onObjectCollisionEnter(registered_object, info)
	print(tostring(info.collision_object) .. " collided with " .. tostring(registered_object))
end
```
``` Lua
-- Example collision_info table
{
	collision_object = objectReference,
	contact_points = {
		{5, 0, -2}
	},
	relative_velocity = {0, 20, 0}
}
```

---


###onObjectCollisionExit(...)

This function is called when an Object stops colliding with a [collision registered](object.md#registercollisions) Object.

!!!info "onObjectCollisionExit(registered_object, collision_info)"
	* [<span class="tag obj"></span>](types.md) **registered_object**: The object registered to receive collision events.
	* [<span class="tag tab"></span>](types.md) **collision_info**: A table containing data about the collision.
		* [<span class="tag obj"></span>](types.md) **collision_info.*collision_object***: Object leaving contact with `registered_object`.
		* [<span class="tag tab"></span>](types.md) **collision_info.*contact_points***: Table/array full of contact points, where each 3D point is represented by a (number indexed) table, _not_ a [Vector](vector.md).
		* [<span class="tag tab"></span>](types.md) **collision_info.*relative_velocity***: Table (number indexed) representation of a 3D vector (but _not_ a [Vector](vector.md)) indicating the velocity of the object that has moved out of contact.

``` Lua
-- Example Usage
function onObjectCollisionExit(registered_object, info)
	print(tostring(info.collision_object) .. " stopped colliding with " .. tostring(registered_object))
end
```
``` Lua
-- Example collision_info table
{
	collision_object = objectReference,
	contact_points = {
		{5, 0, -2}
	},
	relative_velocity = {0, 20, 0}
}
```

---


###onObjectCollisionStay(...)

This function is called **every frame** that an Object is colliding with a [collision registered](object.md#registercollisions) Object.

!!!warning
	This is a very expensive function and can easily slow/crash your game if misused. Use with caution.

!!!info "onObjectCollisionStay(registered_object, collision_info)"
	* [<span class="tag obj"></span>](types.md) **registered_object**: The object registered to receive collision events.
    * [<span class="tag tab"></span>](types.md) **collision_info**: A table containing data about the collision.
		* [<span class="tag obj"></span>](types.md) **collision_info.*collision_object***: Object coming into contact with `registered_object`.
		* [<span class="tag tab"></span>](types.md) **collision_info.*contact_points***: Table/array full of contact points, where each 3D point is represented by a (number indexed) table, _not_ a [Vector](vector.md).
		* [<span class="tag tab"></span>](types.md) **collision_info.*relative_velocity***: Table (number indexed) representation of a 3D vector (but _not_ a [Vector](vector.md)) indicating the direction and magnitude of the collision.

``` Lua
-- Example Usage
function onObjectCollisionStay(registered_object, info)
	print(tostring(info.collision_object) .. " still colliding with " .. tostring(registered_object))
end
```
``` Lua
-- Example collision_info table
{
	collision_object = objectReference,
	contact_points = {
		{5, 0, -2}
	},
	relative_velocity = {0, 20, 0}
}
```

---

###onObjectDestroy(...)

Called whenever any object is destroyed. The dying Object has 1 frame left to live. This event fires immediately before the dying Object’s `onDestroy()` but their lifetime is the same final frame.

!!!info "onObjectDestroy(dying_object)"
	* [<span class="tag obj"></span>](types.md) **dying_object**: The object that was destroyed.

``` Lua
function onObjectDestroy(destroyedObj)
	print(destroyedObj.getName())
end
```

---


###onObjectDrop(...)

Called whenever any object is dropped by a player.

!!!info "onObjectDrop(player_color, dropped_object)"
	* [<span class="tag str"></span>](types.md) **player_color**: [Player Color](player/colors.md) of the Player who dropped the Object.
	* [<span class="tag obj"></span>](types.md) **dropped_object**: The Object in game which was dropped.

``` Lua
function onObjectDrop(colorName, obj)
	print(colorName .. " dropped " .. obj.getName())
end
```

---


###onObjectEnterScriptingZone(...)

Called when any object enters any scripting zone.

!!!info "onObjectEnterScriptingZone(zone, enter_object)"
	* [<span class="tag obj"></span>](types.md) **zone**: The Object of the scripting zone.
	* [<span class="tag obj"></span>](types.md) **enter_object**: The Object triggering the function.

``` Lua
function onObjectEnterScriptingZone(zone, obj)
	print(obj.getGUID())
end
```

---

###onObjectEnterContainer(...)

Called when any object enters any container. Includes Objects entering decks.

!!!info "onObjectEnterContainer(container, enter_object)"
	* [<span class="tag obj"></span>](types.md) **container**: Container the Object entered.
	* [<span class="tag obj"></span>](types.md) **enter_object**: Object that entered the container.

``` Lua
function onObjectEnterContainer(bag, obj)
	print(bag)
	print(obj)
end
```

---

###onObjectFlick(...)

Called whenever a player [flicks](https://kb.tabletopsimulator.com/game-tools/flick-tool/) flicks an object.

!!!info "onFlick(object, player_color, impulse)"
* [<span class="tag obj"></span>](types.md) **object**: The object that was flicked.
* [<span class="tag str"></span>](types.md) **player_color**: [Player Color](player/colors.md) of the player who flicked an object.
* [<span class="tag vec"></span>](types.md) **impulse**: The impulse applied to the object.

!!!example
	Print the player color, type of the flicked object, and magnitude of the flick:
	``` Lua
	function onObjectFlick(object, player_color, impulse)
		print(player_color .. " flicked a " .. object.type ..  " with impulse " .. impulse:magnitude())
	end
	```

---

###onObjectHover(...)

Called when a player moves their pointer (cursor) over an object.

!!!info "onObjectHover(player_color, hovered_object)"
	* [<span class="tag str"></span>](types.md) **player_color**: [Player Color](player/colors.md) of the player who moved the pointer over an object.
	* [<span class="tag obj"></span>](types.md) **hovered_object**: Object on which the pointer was moved.

!!!important
    [<span class="tag obj"></span>](types.md) **hovered_object** can be [<span class="tag nil"></span>](types.md) **nil** in some cases. For example if you move the pointer from the object to the table.



``` Lua
function onObjectHover(player_color, hovered_object)
    if( hovered_object ~= nil ) then
        print(player_color)
	    print(hovered_object)
    end
end
```

---


###onObjectLeaveScriptingZone(...)

Called when any object leaves any scripting zone.

!!!info "onObjectLeaveScriptingZone(zone, enter_object)"
	* [<span class="tag obj"></span>](types.md) **zone**: The Object of the scripting zone.
	* [<span class="tag obj"></span>](types.md) **enter_object**: The Object triggering the function.

``` Lua
function onObjectLeaveScriptingZone(zone, obj)
	print(obj.getGUID())
end
```

---


###onObjectLeaveContainer(...)

Called when any object leaves any container.

!!!info "onObjectLeaveContainer(container, leave_object)"
	* [<span class="tag obj"></span>](types.md) **container**: Container the object left.
	* [<span class="tag obj"></span>](types.md) **leave_object**: Object that left the container.

``` Lua
function onObjectLeaveContainer(bag, obj)
	print(bag)
	print(obj)
end
```

---


###onObjectLoopingEffect(...)

Called whenever the looping effect of an [AssetBundle](behavior/assetbundle.md) is activated.

!!!info "onObjectLoopingEffect(loop_object, index)"
	* [<span class="tag obj"></span>](types.md) **loop_object**: AssetBundle which had its loop activated.
	* [<span class="tag int"></span>](types.md) **index**: Index number for the loop activated.

``` Lua
function onObjectLoopingEffect(obj, index)
	print("Loop " .. index .. " activated.")
end
```

---

###onObjectNumberTyped(...)

Called when a player types a number whilst hovering over an object.

If you wish to prevent the default behavior (e.g. drawing a card) then you may return `true` to indicate you've handled the event yourself.

!!!info "onObjectNumberTyped(object, player_color, number)"
	* [<span class="tag obj"></span>](types.md) **object**: The object the player was hovering over whilst typing a number.
	* [<span class="tag str"></span>](types.md) **player_color**: [Player Color](player/colors.md) of the player that typed the number.
	* [<span class="tag int"></span>](types.md) **number**: The number typed.

!!!example
	Print the player color, the number they entered and the type of object being hovered over:
	``` Lua
	function onObjectNumberTyped(object, player_color, number)
		print(player_color .. " typed " .. number .. " whilst hovering over a " .. object.type)
	end
	```

!!!example
	Prevent players drawing more than 2 cards at a time:
	``` Lua
	function onObjectNumberTyped(object, player_color, number)
		if object.type == 'Deck' and number > 2 then
			print("Sorry. You can only draw a maximum of 2 cards.")
			return true
		end
	end
	```

---

###onObjectPageChange(...)

Called when an object's Custom PDF page is changed.

!!!info "onObjectPageChange(object)"
	* [<span class="tag obj"></span>](types.md) **object**: The object that's page changed.

!!!example
	Print the name of the object and what page it changed to:
	``` Lua
	function onObjectPageChange(object)
		print(object.getName() .. " changed page to " .. object.Book.getPage())
	end
	```

---



###onObjectPeek(...)

Called when a player using peek to look under an Object.

!!!info "onObjectPeek(object, player)"
	* [<span class="tag obj"></span>](types.md) **object**: A reference to the Object which was peeked at.
	* [<span class="tag str"></span>](types.md) **player**: Name of the [Player Color](player/colors.md) that peeked.



``` Lua
function onObjectPeek(object, color)
	printToAll(color .. " peeked at an Object.", {1,0,0})
end
```




---


###onObjectPickUp(...)

Called whenever a Player picks up an Object.

!!!info "onObjectPickUp(player_color, picked_up_object)"
	* [<span class="tag str"></span>](types.md) **player_color**: [Player Color](player/colors.md) of the Player who picked up the object.
	* [<span class="tag obj"></span>](types.md) **picked_up_object**: The Object in game which was picked up.

``` Lua
function onObjectPickUp(colorName, obj)
	print(colorName .. " picked up " .. obj.getName())
end
```

---


###onObjectRandomize(...)

Called when an Object is randomized. Like when shuffling a deck or shaking dice.

!!!info "onObjectRandomize(randomize_object, player_color)"
	* [<span class="tag obj"></span>](types.md) **spawn_object**: The Object which triggered this function.
	* [<span class="tag str"></span>](types.md) **player_color**: [Player Color](player/colors.md) of the player who triggered the function.



``` Lua
function onObjectRandomize(obj, color)
	print(obj.getName() .. " was randomized by " .. color)
end
```

---


###onObjectSearchEnd(...)

Called when a search is finished on any container.

!!!info "onObjectSearchEnd(obj, player_color)"
    * [<span class="tag obj"></span>](types.md) **obj**: The Object which was searched.
    * [<span class="tag str"></span>](types.md) **player_color**: [Player Color](player/colors.md) of the player who triggered the function.

---


###onObjectSearchStart(...)

Called when a search is started on any container.

!!!info "onObjectSearchStart(obj, player_color)"
    * [<span class="tag obj"></span>](types.md) **obj**: The Object which was searched.
    * [<span class="tag str"></span>](types.md) **player_color**: [Player Color](player/colors.md) of the player who triggered the function.

---


###onObjectSpawn(...)

Called when any Object is spawned/created.

!!!info "onObjectSpawn(spawn_object)"
	* [<span class="tag obj"></span>](types.md) **spawn_object**: The Object which triggered this function.

``` Lua
function onObjectSpawn(obj)
	print(obj)
end
```

---


###onObjectTriggerEffect(...)

Called whenever the trigger effect of an [AssetBundle](behavior/assetbundle.md) is activated.

!!!info "onObjectTriggerEffect(loop_object, index)"
	* [<span class="tag obj"></span>](types.md) **loop_object**: AssetBundle which had its trigger activated.
	* [<span class="tag int"></span>](types.md) **index**: Index number for the trigger activated.

``` Lua
function onObjectTriggerEffect(obj, index)
	print("Loop " .. index .. " activated.")
end
```

---

###onPlayerChangeColor(...)

Called when a player changes color or selects it for the first time. It also returns `"Grey"` if they disconnect.

!!!info "onPlayerChangeColor(player_color)"
	* [<span class="tag str"></span>](types.md) **player_color**: [Player Color](player/colors.md) of the player who triggered the function.

``` Lua
function onPlayerChangeColor(color)
	print(color)
end
```

---

###onPlayerChangeTeam(...)

Called when a player changes team.

!!!info "onPlayerChangeTeam(player_color, team)"
	* [<span class="tag str"></span>](types.md) **player_color**: [Player Color](player/colors.md) of the player who triggered the function.
    * [<span class="tag str"></span>](types.md) **team**: Team to which the player has changed.  Options below.
        * "" (empty string, if changed to None)
        * Diamonds
        * Hearts
        * Jokers
        * Clubs
        * Spades

``` Lua
function onPlayerChangeTeam(player_color, team)
	print(player_color)
    print(team)
end
```

---

###onPlayerConnect(...)

Called when a [Player](player/instance.md) connects to a game.

!!!info "onPlayerConnect(person)"
	* [<span class="tag pla"></span>](types.md) **person**: [Player](player/instance.md) reference to who connected.

---


###onPlayerDisconnect(...)

Called when a [Player](player/instance.md) disconnects from a game.

!!!info "onPlayerDisconnect(person)"
	* [<span class="tag pla"></span>](types.md) **person**: [Player](player/instance.md) reference to who disconnected.

---


###onPlayerTurn(...)
Called at the start of a player's turn when using the in-game turn system.

!!!info "onPlayerTurn(person)"
	* [<span class="tag pla"></span>](types.md) **person**: [Player](player/instance.md) who's turn is starting.

``` Lua
function onPlayerTurn(person)
	print(person.color .. "'s turn starts now.")
end
```

---


###onSave()

Return a [<span class="tag str"></span>](types.md).

This event handler provides you with an opportunity to persist your script's state, such that when a save game is loaded
(or the user rewinds) the data you've persisted will be made available to [onLoad(...)](#onload).

A script's saved state is just a singular [<span class="tag str"></span>](types.md). The convention for storing complex
state is to create a Lua table, [JSON.encode(...)](json.md#encode) it, and return the JSON encoded string from this
function.

**Global Script**

This is called whenever the user manually saves game, when an auto-save is created _and_ when a rewind checkpoint is
created, by default, that's every 10 seconds. Due to the frequency at which this event handler is called, it's important
that your function be fast.

**Object Script**

In addition to saves and rewind checkpoints, this event handler will also be called on an Object that requires its state
be saved mid-game e.g. when the script-owner Object enters a container.

!!!tip
	[JSON.encode(...)](json.md#encode) has limitations with regards to what data it can encode. It _cannot_ encode
	references to Objects. If you wish to encode a reference to an object, encode the Object's [guid](object.md#guid)
    and in [onLoad(...)](#onload) obtain a new Object reference via
	[getObjectFromGUID(...)](base.md#getobjectfromguid).

!!!warning
	Pressing "Save & Play" (in either the in-game Scripting Editor or Atom) does _not_ trigger the save event.

    In this context "Save" is referring to saving your script only. Save & Play will in fact reload your game,
	_discarding any non-scripting changes_ made since the game was last (manually) loaded/saved.

!!!example
	Returns a JSON encoding of a game state consisting of nested tables, strings, numbers and object references
	(encoded as GUIDs). In this example, `some_object` is a reference to an [Object](object.md).
	```lua
	function onSave()
		local state = {
			questions = { -- nested table
				{
					question = "What day comes after Saturday?", -- string
					answer = "Sunday",
				},
				{
					question = "Unknown",
					answer = 42, -- number
				}
			},
			guids = {
				some_object = some_object.guid -- GUID (a string)
			}
		}
		return JSON.encode(state)
	end
	```
	Refer to [onLoad(...)](#onload) to see an example of this same save state structure being loaded. Subscribe to the
	[example mod](https://steamcommunity.com/sharedfiles/filedetails/?id=2430471959) to see this in action.

---


###onScriptingButtonDown(...)

Called when a scripting button (numpad by default) is pressed. The index range that is returned is 1-10.

!!!info "onScriptingButtonDown(index, player_color)"
	* [<span class="tag int"></span>](types.md) **index**: Index number, representing which key was pressed.
	* [<span class="tag str"></span>](types.md) **player_color**: [Player Color](player/colors.md) of the player who triggered the function.

``` Lua
function onScriptingButtonDown(index, color)
	print(index)
end
```

---

###onScriptingButtonUp(...)

Called when a scripting button (numpad by default) is released. The index range that is returned is 1-10.

!!!info "onScriptingButtonUp(index, player_color)"
	* [<span class="tag int"></span>](types.md) **index**: Index number, representing which key was released.
	* [<span class="tag str"></span>](types.md) **player_color**: [Player Color](player/colors.md) of the player who triggered the function.

``` Lua
function onScriptingButtonUp(index, color)
	print(index)
end
```

---


###onUpdate()

Called **every frame**.

!!!warning
	This is a very expensive function and can easily slow/crash your game if misused. Use with caution.

``` Lua
function onUpdate()
	print("This will probably slow your game down.")
end
```

---

###tryObjectEnterContainer(...)

Called when an object attempts to enter a container. Return `false` to prevent the object entering.

!!!info "tryObjectEnterContainer(container, entering_object)"
	* [<span class="tag obj"></span>](types.md) **container**: The container the Object is trying to enter.
	* [<span class="tag obj"></span>](types.md) **entering_object**: The Object entering the container.

!!!example
	```lua
	function tryObjectEnterContainer(container, entering_object)
		print(entering_object.getName()) -- Print entering object's name
		return true -- Allows object to enter.
	end
	```


---


## Object Event Handler Details

###onCollisionEnter(...)

This function is called when an Object starts colliding with the Object the function is on. Does not work in Global.

!!!info "onCollisionEnter(collision_info)"
	* [<span class="tag tab"></span>](types.md) **collision_info**: A table containing data about the collision.
		* [<span class="tag obj"></span>](types.md) **collision_info.*collision_object***: Object coming into contact with `self`.
		* [<span class="tag tab"></span>](types.md) **collision_info.*contact_points***: Table/array full of contact points, where each 3D point is represented by a (number indexed) table, _not_ a [Vector](vector.md).
		* [<span class="tag tab"></span>](types.md) **collision_info.*relative_velocity***: Table (number indexed) representation of a 3D vector (but _not_ a [Vector](vector.md)) indicating the direction and magnitude of the collision.
``` Lua
-- Example Usage
function onCollisionEnter(info)
	print(tostring(info.collision_object) .. " collided with " .. tostring(self))
end
```
``` Lua
-- Example collision_info table
{
	collision_object = objectReference,
	contact_points = {
		{5, 0, -2}
	},
	relative_velocity = {0, 20, 0}
}
```

---


###onCollisionExit(...)

This function is called when an Object stops colliding with the Object the function is on. Does not work in Global.

!!!info "onCollisionExit(collision_info)"
	* [<span class="tag tab"></span>](types.md) **collision_info**: A table containing data about the collision.
		* [<span class="tag obj"></span>](types.md) **collision_info.*collision_object***: Object leaving contact with `self`.
		* [<span class="tag tab"></span>](types.md) **collision_info.*contact_points***: Table/array full of contact points, where each 3D point is represented by a (number indexed) table, _not_ a [Vector](vector.md).
		* [<span class="tag tab"></span>](types.md) **collision_info.*relative_velocity***: Table (number indexed) representation of a 3D vector (but _not_ a [Vector](vector.md)) indicating the velocity of the object that has moved out of contact.

``` Lua
-- Example Usage
function onCollisionExit(info)
	print(tostring(info.collision_object) .. " stopped colliding with " .. tostring(self))
end
```
``` Lua
-- Example collision_info table
{
	collision_object = objectReference,
	contact_points = {
		{5, 0, -2}
	},
	relative_velocity = {0, 20, 0}
}
```

---


###onCollisionStay(...)

This function is called **every frame** that an Object is colliding with the Object this function is on. Does not work in Global.

!!!warning
	This is a very expensive function and can easily slow/crash your game if misused. Use with caution.

!!!info "onCollisionStay(collision_info)"
	* [<span class="tag tab"></span>](types.md) **collision_info**: A table containing data about the collision.
		* [<span class="tag obj"></span>](types.md) **collision_info.*collision_object***: Object coming into contact with `self`.
		* [<span class="tag tab"></span>](types.md) **collision_info.*contact_points***: Table/array full of contact points, where each 3D point is represented by a (number indexed) table, _not_ a [Vector](vector.md).
		* [<span class="tag tab"></span>](types.md) **collision_info.*relative_velocity***: Table (number indexed) representation of a 3D vector (but _not_ a [Vector](vector.md)) indicating the direction and magnitude of the collision.

``` Lua
-- Example Usage
function onCollisionStay(info)
	print(tostring(info.collision_object) .. " still colliding with " .. tostring(self))
end
```
``` Lua
-- Example collision_info table
{
	collision_object = objectReference,
	contact_points = {
		{5, 0, -2}
	},
	relative_velocity = {0, 20, 0}
}
```

---


###onDestroy()

This function is called when an [Object](object.md) it is on is destroyed. When `onDestroy()` is called, the Object has one frame left to live but its recommended to avoid using it as a reference here. This event fires immediately after [onObjectDestroy()](#onobjectdestroy) but their lifetime is the same final frame. Does not work in Global.

``` Lua
function onDestroy()
	print("This object was destroyed!")
end
```

---

###onDrop(...)

This event handler is called when this [Object](object.md) is dropped. Does not work in Global.

!!!info "onDrop(player_color)"
	* [<span class="tag str"></span>](types.md) **player_color**: [Player Color](player/colors.md) of the Player.

``` Lua
function onDrop(color)
	print(color)
end
```

---

###onFlick(...)

Called when a player [flicks](https://kb.tabletopsimulator.com/game-tools/flick-tool/) this [Object](object.md).

!!!info "onFlick(player_color, impulse)"
* [<span class="tag str"></span>](types.md) **player_color**: [Player Color](player/colors.md) of the player who flicked this object.
* [<span class="tag vec"></span>](types.md) **impulse**: The impulse applied to the object.

!!!example
	Print the player color and magnitude of the flick:
	``` Lua
	function onFlick(player_color, impulse)
		print(player_color .. " flicked with impulse " .. impulse:magnitude())
	end
	```

---

###onHover(...)

Called when a player moves their pointer (cursor) over this [Object](object.md).

!!!info "onHover(player_color)"
	* [<span class="tag str"></span>](types.md) **player_color**: [Player Color](player/colors.md) of the player who moved the pointer over an object.

``` Lua
function onHover(player_color)
    print(player_color)
end
```

---

###onNumberTyped(...)

Called when a player types a number whilst hovering over this [Object](object.md).

If you wish to prevent the default behavior (e.g. drawing a card, if this object were a deck) then you may return `true` to indicate you've handled the event yourself.

!!!info "onNumberTyped(player_color, number)"
	* [<span class="tag str"></span>](types.md) **player_color**: [Player Color](player/colors.md) of the player that typed the number.
	* [<span class="tag int"></span>](types.md) **number**: The number typed.

!!!example
	Print the player color and the number they typed:
	``` Lua
	function onNumberTyped(player_color, number)
		print(player_color .. " typed " .. number)
	end
	```

!!!example
	Prevent players drawing more than 2 cards at a time (from this object):
	``` Lua
	function onNumberTyped(player_color, number)
		if self.type == 'Deck' and number > 2 then
			print("Sorry. You can only draw a maximum of 2 cards.")
			return true
		end
	end
	```

---

###onPageChange()

Called when this [Object](object.md)'s Custom PDF page is changed.

!!!example
	Print this object's name and what page it changed to:
	``` Lua
	function onPageChange()
		print(self.getName() .. " changed page to " .. self.Book.getPage())
	end
	```

---


###onPeek(...)

Called when a player using peek to look under an Object.

!!!info "onPeek(player_color)"
	* [<span class="tag str"></span>](types.md) **player_color**: Name of the [Player Color](player/colors.md) that peeked.


``` Lua
function onPeek(color)
	printToAll(color .. " peeked at an Object.", {1,0,0})
end
```


---


###onPickUp(...)

Called when a player picks up an Object.

!!!info "onPickUp(player_color)"
	* [<span class="tag str"></span>](types.md) **player_color**: [Player Color](player/colors.md) of the Player.

``` Lua
function onPickUp(color)
	print(color)
end
```

---



###onRandomize(...)

Called when an Object is randomized. Like when shuffling a deck or shaking dice.

!!!info "onRandomize(player_color)"
	* [<span class="tag str"></span>](types.md) **player_color**: [Player Color](player/colors.md) of the player who triggered the function.


``` Lua
function onRandomize(color)
	print(self.getName() .. " was randomized by " .. color)
end
```

---






###onSearchEnd(...)

Called when a player first searches this Object.

!!!info "onSearchEnd([<span class="tag str"></span>](types.md) player_color)"
	* [<span class="tag str"></span>](types.md) **player_color**: [Player Color](player/colors.md) of the Player.

---


###onSearchStart(...)

Called when a player finishes searching this Object.

!!!info "onSearchStart([<span class="tag str"></span>](types.md) player_color)"
	* [<span class="tag str"></span>](types.md) **player_color**: [Player Color](player/colors.md) of the Player.

---

###tryObjectEnter(...)

Called when another object attempts to enter this Object (container). Return `false` to prevent the object entering.

!!!info "tryObjectEnter(entering_object)"
	* [<span class="tag obj"></span>](types.md) **entering_object**: The object that has tried to enter the object this script is attached to.

!!!example
	Print the name of the object entering this container.
	```lua
	function tryObjectEnter(entering_object)
		print(entering_object.getName())
		return true -- Allows the object to enter.
	end
	```