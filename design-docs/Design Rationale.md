# Assignment 1 -- Team **dbuihpat**

The overall design choices are made keeping in mind the extensibility of the game.
Below listed the details of design choices for each project requirement.

## Leave affordance

**Design choice**
1. Create a new `Leave` class which will complement the existing `Take` class
2. All the entities that have `Take` affordance should have a `Leave` affordance in their initialisers

**Advantages**
- Having another class will make it more extensible, for eg. we can implement a `Throw` class where the `Actor` *throws* the `Entity` and it drops at different `Location`.
- It'll be easy to implement `Leave` class as it has to do opposite of whatever `Take` does.

**Disadvantages**
- Implementing a whole class, as compared to a method, just to undo what `Take` does will make the project more complex.
- It will increase the dependencies and there will be code to maintain.

## Ben Kenobi
**Design choice**
1. Implement an ArrayList in `BenKenobi` for all the players that are to be trained. That will make it extendable for Ben to train other players, so for example, if we wish to include another player Han Solo, we can add him to Ben's list and Ben will train him when they're in the same spot.
2. The `Train` class will have a method `checkLocal()` that will take an ArrayList of `SWActors` as parameter. It will check if any of those actors are on the same location as Ben.
3. If an actor is in the same location as Ben, `Train` will execute `upskill()` method and pass-in that `Actor` as parameter. If there are more than one Actors at the same location, one of them will be randomly be chosen and trained.

**Advantages**
- Highly flexible as if we need Ben to train some other Actor, we just have to include that Actor’s name in Ben’s ArrayList. 
- Implementing a Train class separately will also enable some other player to perform `Train` action. For example, if Luke has mastered the Force, he can train Princess Leia.

**Disadvantages**
- Increases dependencies and complexity of the game. It is not the most efficient solution, as implementing a `train(Luke)` function in BenKenobi would seem like the most simple and  method.


## Droids


**Design choice**

1. For simplilcity we will assume that each droid can have only one owner and each owner can own no more than one droid.
2. The droids will belong to team `Neutral`
3. A `SWActor` variable in `Droid` that will let the droid know it’s owner.
4. Implement a function to check if droid is on `badlands`, if it is, decrease it's health.
5. Implementing a `FindActor` behaviour, which will take `SWActor` as a parameter (we will pass-in the owner for droids), that will tell the droid where to move to. It will do so by analysing the neighbouring locations to see if owner is present. If it is then return the `Direction` of it’s owner, if not then command droid to move in a random `Direction`.
6. We will have two boolean flags:
    - `hasOwner` -- to tell if owner is dead 
    - `isImmobile` -- to tell if droid has health or is immobile


**Advantages**
- A highly flexible design that can be extended to make game more interesting. For example, Ben Kenobi can use Find Actor to find Luke to train him or TuskenRaiders can be programmed to find Ben to engage in a fight with him!

**Disadvantages**

- Adding new class will improve the overall complexity. Furthermore, `FindActor` will be a dependency for actors, which can be prone to errors.
-  At times, it might be difficult for player to keep track of `SWActors` and the actors they are finding.


## Force
**Design choice**
1. For extensibility purposes, the force will be a class of its own. 
2. A new action option will be displayed but only if the player is holding the lightsaber.
3. Only lightsaber wielders will have the force action option.
4. An if...else statement will be implemented to check the force level of whoever is attempting to use the force action.
5. A new attack message will be displayed based on whether or not the user was able to attack with the lightsaber.


**Advantages**
- This makes the program more extensible rather than having the force become an attribute.
- A check simplifies the force action where we simply need to check the character's current force level 

**Disadvantages**
- Requires a completely new class to be implemented. 


## Lightsaber
**Design Choice**
1. The force class will depend on the lightsaber, simply to use it as an object since the lightsaber can exist independently from the force class.
2. It will be included in the if...else statement (in the force class) as a condition alongside the force level condition. 

**Advantages**
- Allows for only competent force users to attack with a lightsaber.
- No modifications to the lightsaber class are necessary.
- Use of the lightsaber as a condition is only a small addition. 

**Disadvantages**
- Adds extra steps to allowing attacks to be made by lightsaber wielders. 