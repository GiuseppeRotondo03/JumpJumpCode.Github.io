# #Summary
To create this game, I used unreal engine Visual Scripting Blueprints as they are faster and easier to update than C++ scripts.

- In this repostery, I won't post every blueprint, as I think almost all of them are really easy to understand, but I will post my working method and the blueprints I think are most important.

## #Optimization
**immagine**
- There are many blueprints in the game world and make the game as light as possible, I tried to minimize the interaction between the various blueprints by casting using Almost and only BluePrint Function Library and BluePrint Interface.
- In this way each blueprint in the game level interacts with the player, to apply debuff effects, buffs and more, without creating references and weighing down the game.
- When player interacts with actors that influence Widget(UI), they still use BluePrint Interfaces by logging into player First and After to Blue Print Widgets.
- In the end, I tried to use as few " event ticks " as possible to avoid performance issues.
- As a result, the game runs at maximum quality (unreal engine 5.0 default), without creating problems, even on not very powerful Laptops.
