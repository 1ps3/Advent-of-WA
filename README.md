## Advent-of-WA
# Project 1: Triggers. 
First and foremost to get working in WeakAuras you must understand it's core, the trigger system. Triggers determine whether or not an aura is to display itself. WeakAuras expects a single function for a custom trigger (You can find more on functions <here>), in Lua funa return is used to end a function and return a variable, implicit return at the end of any function, so you do not need to use one if your function ends naturally, without returning any value. Custom triggers rely on this return determine whether or not they are to trigger. In Lua anything that isn't `false` or `nil` will return as `true`. 

In this first project we will be making an aura that simply remains triggered all the time. The this aura we will be using a custom status trigger that checks on `every frame`. Idealy we wouldn't be using an every frame trigger to run code, though this is a small amount of code and is for the purposes of this tutorial. Later projects will go into using other methods such as events. 

The first thing we should be doing here is declaring that we are starting a function, simply by writing `function()` on the first line, after which we simply `return true` on the next line and end our function after that with and `end`. This aura will now remain triggered. 
# Project 2: Units. 
Units are an integral part of WoW's API. They're used as a method of labeling characters and NPC's in the game world. Units are simply anything that has a UnitFrame or a Nameplate, you can learn more about Unit's and different Unit types <here>. In this project we will be using the `UnitHealth("unit")` and `UnitHealthMax("unit")` functions. Both of these functions expect Unit strings as their arguments and only work on units. So for this example we will be using the `player` Unit.

Once again we will be using an `every frame` status trigger though this time we will be using the two Unit functions in our return instead of true. We want to create an aura that triggers when our max health and current health are the same, so we will be calling the two unit functions using the player unit like so `UnitHealth("player")` and `UnitHealthMax("player")`, but we also want to compare the two of them, so we will use `==` to do so. So we will be returning `UnitHealth("player") == UnitHealthMax("player")`, because comparing is a booldean, this will return either `true` or `false` depending on our current health and will trigger when our health is at 100%.
# Project 2: Events. 
Events are notifications from the client that something has changed in game. There are events for almost everything in the entire game To understand the wow enviroment you must first understand the event system that's put in place to help addons get the
information they require at times when the client belives is necessary. Events exist for most things in the game, everything
from your health changing to adding a friend in game. There are lists of events that can be found at (event list here), but 
for the purposes of this tutorial we'll only be using a single event, `PLAYER_REGEN_ENABLED`. This event is
talk about registering events and what to return for triggers. 
# Project 2: The Aura Environment. 
saving variables and acessing the aura enviroment to pass variables to display. 
# Project 3: WoW functions and Units. 
using wow functions and unit types to track buffs
# Project 4: Timers and iteration. 
