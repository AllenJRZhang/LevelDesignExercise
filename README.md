# Design Doc - Level Design Exercise

#### CS415 MP2 —- Allen Zhang(jiaruiz2)

## 1.Basic Control

Note: Right-click the screen when first starting the game to gain control of the character

Move camera - Mouse

Move - WASD

Jump - Space

Crouch - Left Ctrl

## 2.Gameplay

## 2.1 General Layout

The general layout of this level is a linear tunnel-like path, similar to that in platform
runner games such as _Temple Run_ , but is pre-generated,rather than generated
randomly at runtime. The linear level has a starting point and an end point.

## 2.2 Player Goal

The goal of the player is to make it to the end of the level, step on a giant green button,
without losing health to lower than or equal to zero, and avoid being caught by the
_Pursuer_ enemy.

## 2.3 Core Mechanism - Health System

The player has a health value, 100% at the beginning, and every type of damage taken
by the player will deduct this value by 10% each time. When the health is lowered to
zero, the game is over and the player has to start over again. There is a type of
collectibles called Health Packs which can increase the player health by 20% (up to
100%) when picked up.

## 2.4 Core Mechanism - Score System

The player also has a value called Score, initially being 0, will increase by 10 every time
the player picks up coins, another type of collectibles. And if the player manages to kill
an enemy, the player character will be granted with 100 bonus points and 10% health
(up to 100%).


## 2.5 Core Mechanism - Game Restart & Complete

Under certain circumstances it will be considered game over and a restart UI will be
shown on the screen while the player character freezes. And the player can choose to
restart the game, which will reset everything in the level. Here is a list of scenarios
where this will happen:

1. The player health reaches 0 or lower (by concealing enough damage)
2. The player character is caught up by the _Pursuer_ enemy
3. The player jumps off the platform

The level is completed when the player achieves the final goal – reaching the end of the
level and presses a green button. When this happens, a UI similar to the restart UI will
appear, with the addition of the text “LEVEL COMPLETE” added to the screen as well.
The player can still choose to restart the level with this UI.

## 3.Collectibles

### 3.1 Health Pack

```
● Health Packs are green, spinning objects
● Health Packs will disappear upon being picked up
● Health Packs will increase the player health by 20% (up to 100%) when picked
up
```
### 3.2 Coin

```
● Coins are yellow, circular spinning objects
● Coins will disappear upon being picked up
● Coins also serve as cues to guide player to navigate around obstacles
● Coins will increase the player score by 10 when picked up
● Some coins are also positioned in a ways such that it is risky for the player to
collect them, so the player must make a decision between taking the safer route
with fewer coins, or taking the more dangerous route for more potential gain
```
## 4.Enemy Types

### 4.1 Pursuer

Note: Certain changes are made to the functionality of this enemy type in comparison to
the general guideline to better fit this specific level design.


The _Pursuer_ is the type of enemy that will constantly chase after the player at all times.
If the player is caught up by the _Pursuer_ , the gamewill instantly be over. (Much like the
monster in _Temple Run_ ). Since the level is too narrowfor the patrol mechanism of
_Pursuer_ enemy to be plausible, this feature cannotbe implemented.

### 4.2 Mortar

Note: Certain changes are made to the functionality of this enemy type in comparison to
the general guideline to better fit this specific level design.

The _Mortar_ is the type of enemy that is stationary,and constantly shoots out projectiles
towards a certain direction. If either the projectile or the _Mortar_ itself touches the player,
the player health will decrease by 10%.

The _Mortar_ can be destroyed by jumping on top of them,which will grant the player
character 100 bonus points as well as 10% health (up to 100%).

Again since the level is too narrow, the _Mortar_ shootsprojectiles in a certain direction
instead of randomly within a radius. And the projectile doesn’t cause a blast but rather
directly hits the target.

### 4.3 Turret (Custom Enemy)

_Turret_ is the custom enemy type. They are stationary,floating orbs that will detect the
player character within a certain range, and shoot projectiles at the direction of the
player character as the player moves. They rotate in the direction to always face the
player character.

### 4.4 Lava Floor (Additional)

This is more of an environmental hazard. It is a type of floor which can deal damage
when the player character steps on it. They are put in a level in a strategic way to add
more challenge to the player.


