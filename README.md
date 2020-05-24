**SpaceSharp** *now features a new User defined Scripts system by leveraging the power of Javacript.
You can write plugins for SpaceSharp using common Javascript functions and the custom functions we added below:*

```js
// This function return milliSeconds since 1970
getMilliSeconds()

// A function to log messages into the SpaceSharp Script-Logging-Window
log(string logMsg)

// Clears Log WIndow
clearLogs()

// Returns the percentage health of the player
getPercentageHealth()

// Returns attack speed of payer
getAttackSpeed()

// Returns movement speed of player
getMovementSpeed()

// Returns movement speed of player in pixels (care it is only a rough appxoimation)
getMovementSpeedInPixels()

// Disables movement (rightclicks) during kiting
disableMovementWhileKiting(bool disable = true)

// Returns the current mouse position as an array
getMousePos()

// Returns the position of player champ while kiting as an array (this function is also quite inaccurate, so use with care)
getPlayerPosWhileKiting()

// Check if a key on keyboard is down
isKeyDown(int keyCode)

// Presses Key
pressKey(int keyCode)

// Holds key down until keyUp is called
keyDown(int keyCode)

// Releases key
keyUp(int keyCode)

/* Returns a bunch of information regarding the player. these information are:
abilityPower
armor
attackDamage
attackRange
bonusArmorPenetrationPercent
bonusMagicPenetrationPercent
cooldownReduction
critChance
critDamage
currentHealth
healthRegenRate
lifeSteal
magicResist
maxHealth
moveSpeed
resourceMax
resourceRegenRate
resourceType
resourceValue
currentGold
level
abilityLevelQ
abilityLevelW
abilityLevelE
abilityLevelR

For example:
var stats = getChampionStats();
log(stats['level']); <-- Will print current champion level
*/
getChampionStats()

// Returns current player health% as double
getCurrentHealth()

// Returns user screen dimensions as array
getScreenDimensions()

// TODO 
getMinions()

// TODO
getEnemyChamps()

// TODO 
getPixelColor()

// TODO
isInRange()

// TODO
isInRangeWhileKiting()

// TODO
searchPixel()


// Returns pixel per ingame unit
convertIngameRangeToRangeInPixel()

// Moves mouse to x,y position
moveMouseToPos(int x, int y)

// Returns x,y position of enemy as an array, which is next to mouse
getEnemyNextToMouse(bool checkForInRange)

// Sets the attackspeed to a fixed value and will never get updated again by SpaceSharp
setAttackSpeedTo(double attackSpeed)

// Disables auto attacks while kiting (e.g. useful when implementing Cassio ability kiting)
disableAAWhileKiting(bool disable=true)

// Sleeps given amount of milliseconds
sleep(int sleepTime)

//
//	Callbacks
//	The following functions will be invoked by C# at given times of execution
//

// This function is invoked when the "Start/Stop" toogle is set to "Start"
function onStart() {}

// This function is invoked when the "Start/Stop" toogle is set to "Stop"
function onStop() {}

// This function is invoked before actually doing the "real heal" of Spacesharp (e.g. usefull for activating heal and barrier at the same time)
// The parameter supplied is the current HP of player (values reach from 0 to 1)
function onHeal(hp) {}

// This function is invoked before the auto attack while kiting is done.
// But the mouse cursor is already on the enemy
// The parameters are the x and y coordinate of the found enemy
function onBeforeAttackWhileKiting(x,y) {}

// This function is invoked before the auto attack while kiting is done.
function onAfterAttackWhileKiting(x,y) {}

// Gets called after windup time is over
// Useful to implement auto attacks in combos
function onAfterWindupWhileKiting(x, y) {}

// This function is called every few milliseconds
// You could do things like checking if Key is pressed, etc.
function onForever() {}
