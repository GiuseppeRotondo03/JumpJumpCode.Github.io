# #Summary

<hr>
To create this game, I used unreal engine Visual Scripting Blueprints as they are faster and easier to update than C++ scripts.

- In this repostery, I won't post every blueprint, as I think almost all of them are really easy to understand, but I will post my working method and the blueprints I think are most important.

## #Optimization


<hr>
- There are many blueprints in the game world and make the game as light as possible, I tried to minimize the interaction between the various blueprints by casting using Almost and only BluePrint Function Library and BluePrint Interface.
- In this way each blueprint in the game level interacts with the player, to apply debuff effects, buffs and more, without creating references and weighing down the game.
- When player interacts with actors that influence Widget(UI), they still use BluePrint Interfaces by logging into player First and After to Blue Print Widgets.
- In the end, I tried to use as few " event ticks " as possible to avoid performance issues.
- As a result, the game runs at maximum quality (unreal engine 5.0 default), without creating problems, even on not very powerful Laptops.

## #A bit of coding

### #Wall

<hr>
When you create new rooms the new walls spawn left and right based on the current wall. If you are looking at a wall turned 90°, the coordinates will change. To find the exact position I have created and used functions that calculate your position by performing operations with vectors.
- You can find the function here: [click here](https://blueprintue.com/blueprint/hsnp327y/)
- You can fine the spawn process here: [click here](https://blueprintue.com/blueprint/z5vy5r16/)

### #how Rooms are spawned

<hr>
- The player performs a raycast
- If he hits the wall from the right side, he asks the wall to spawn the "Room controller"
- The hit wall is destroyed
- The room controller is the one who manages Everything

![RC](/BP_RC.png)
The Room Controller is the actor who
- Manages the spawn of all obstacles, buffs and debuffs based on the type of Room
- Change the type of wall based on whether or not it's a "Wall Jump" room
- Destroys all actors inside the "room" when the player dies or gets too far away
- Assign buffs or debuffs
  
#### #A bit of organization

<hr>

If you want to see more aboyt my BluePrints visual code, please, ask.
- Each piece of code is commented and grouped to help my understanding (or that of other future developers) even after months.
![FP](/BP_FirstPerson.png)
- All variables, event functions, meshes... have been named correctly to facilitate their search, management and use
![F1](/Screen_Folder_0.png)
- I also used "Category" to organize more efficiently Variables, Custom Events and Functions inside blueprints
[Click here](/Screen_Folder_1.png)
- During the alpha test, i used "Gray Box" to test your code without interference or distraction
