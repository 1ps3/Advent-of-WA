## Advent-of-WA
# Project 1.1: Printing.
Useful Links: https://wow.gamepedia.com/MACRO_script
Apparently printing "Hello World" as the first thing you do when working with a language is a thing so we should probably do the same here too. To do this we'll be utilizing slash commands to run code. The slash command to run code is pretty simple, it's simply `/run` or `/script` these will run and execute the code after the command. The other useful function we'll be using is the print function, named `print()`, print will print anything passed to it. So we'll be printing the string "Hello World".

# Solution
`/run print("Hello World")`

# Project 1.3: Functions.
# Useful Links: https://www.lua.org/pil/5.html
WeakAuras expects a single function for a custom trigger (You can find more on functions <here>), in Lua return is used to end a function and return some kind of variable, string or table, there is also implicit return at the end of any function, so you do not need to use one if your function ends naturally. To understand functions we will once again be using WoW's run slash command. Functions can be declared be calling either, `function name ()` or `name = function()`. Both of these lines will save a function called `name` for us to use in our code. The print in part 1.1 we were using to output things into chat is a function provided by Lua. Functions require an `end` on the last line to end the function call. To run a function simply call it like so `name()`, this will run the function code block.

In this example we will be using a function to print "Hello World" instead of directly calling print. By writing the function in the /run command and placing a print inside of it, we then will call it after we end the function to run it and print

# Solution
`/run function a() print("Hello World") end a()`

# Project 1.4: Function Parameters. 
Much like other langagues, things can be passed into functions as parameters. To do this in Lua you would simply place the parameters inside of the brackets like so. `function a(var1, var2, var3)` this will allow us to pass anything into the three parameters and use them inside the function by calling `var1`, `var2` and `var3`. Using this info we can get out function to print anything we'd like. First we will have to delcare a variable and then create a function which passes at least a single parameter, then call that function with the variable like so `a(myVariable)`. 

# Solution
`/run myVariable = true function a(var1) print(var1) end a(myVariable)`
  
# Project 1: Triggers. 
First and foremost to get working in WeakAuras you must understand it's core, the trigger system. Triggers determine whether or not an aura is to display itself. WeakAuras expects a single function for a custom trigger (You can find more on functions <here>), in Lua return is used to end a function and return some kind of variable, string or table, there is also implicit return at the end of any function, so you do not need to use one if your function ends naturally. Custom triggers rely on this return determine whether or not they are to trigger. In Lua anything that isn't `false` or `nil` will return as `true`. 

In this first project we will be making an aura that simply remains triggered all the time. The this aura we will be using a custom status trigger that checks on `every frame`. Idealy we wouldn't be using an every frame trigger to run code, though this is a small amount of code and is for the purposes of this tutorial. Later projects will go into using other methods such as events. 

The first thing we should be doing here is declaring that we are starting a function, simply by writing `function()` on the first line, after which we simply `return true` on the next line and end our function after that with and `end`. This aura will now remain triggered. 
# Project 2: Units. 
Units are an integral part of WoW's API. They're used as a method of labeling characters and NPC's in the game world. Units are simply anything that has a UnitFrame or a Nameplate, you can learn more about Unit's and different Unit types <here>. In this project we will be using the `UnitHealth("unit")` and `UnitHealthMax("unit")` functions. Both of these functions expect Unit strings as their arguments and only work on units. So for this example we will be using the `player` Unit.

Once again we will be using an `every frame` status trigger though this time we will be using the two Unit functions in our return instead of true. We want to create an aura that triggers when our max health and current health are the same, so we will be calling the two unit functions using the player unit like so `UnitHealth("player")` and `UnitHealthMax("player")`, but we also want to compare the two of them, so we will use `==` to do so. So we will be returning `UnitHealth("player") == UnitHealthMax("player")`, because comparing is a booldean, this will return either `true` or `false` depending on our current health and will trigger when our health is at 100%.
# Project 3: Events. 
Events are a crucial part of WoW's API they are essentially notifications from the client that something has changed in game. There are events for almost everything in the entire game this system helps addons grab the information they need from the game or run thier code only when they need to. There's no point in check health all the time if it hasn't changed. 

For the purposes of this tutorial we'll only be using a single event, `UNIT_HEALTH_FREQUENT`. This event will fire each time a unit's health changes. This is obviously ideal from tracking health because we only run our code when a unit's health changes, and not any other time. As mentioned ealier `UNIT_HEALTH_FREQUENT` will make out code run if any unit's health changes, this means that we're going to have our code running even when our target's health changes, even though we only want to check the palyer's health. To do this we have to filter out other units. Our function will have a payload that WeakAuras passes into the function. In the case of `UNIT_HEALTH_FREQUENT` it only has one argument that is passed, that being the unit, so adding a variable inside of our function call will let us check against the unit type, like so `function(unit)`. This will let us use the variable `unit` to filter the units. 
# Project 4: The Aura Environment. 
saving variables and acessing the aura enviroment to pass variables to display. 
# Project 3: WoW functions and Units. 
using wow functions and unit types to track buffs
# Project 4: Timers and iteration. 
