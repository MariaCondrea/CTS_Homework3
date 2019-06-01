# CTS_Homework3

The game I have worked on during my practical stage is called Zombie Toys and it is a third-person endless shooter/arcade game where the player, a young boy or girl, has awoken to find out that their toys came to life as zombies who threaten them. The aim of the game is to survive as long as possible, as the player avoids being hurt by the zombified toys, as well as killing the toys. Points are earned by shooting the monsters using a special remote control toy, having four attacks available, Lightning Attack, Frost Attack, Stink Bomb and Slime Attack. By gaining points, the player might spawn an ally, which will attract the enemies, giving the player a chance to take them down.

The game was based on the coding the behaviors of the players, the enemies or the attacks, and the design of the game UI, creating the players, using prefabs to create them, how lightning is important in a video game and how it can change the overall effect of the gameplay by adding physics to it. The game is playable on PC and Android phones.

In order to describe the game’s specs from a clean code POV, the following design patterns can be used:

## Creational Design Patterns

*Factory Method* can be used to create the ally of the player, either as a sheep or as dog. When playing the game, the player can pick a sheep, which is the default ally spawned, or can pick the dog. The default ally has the function of distracting the attention of the zombie toys. Each time an ally is spawned, a concrete instance of the class is assembled from the factory class into the game. 

This provides a way to delegate the instantiation logic of an ally to its children, which are the sheep and dog. The ally object is created by calling the factory method specified in the interface rather can calling a constructor.

*Builder*, used for setting up component-based entities one component at a time, based on the given data, step by step. This way, we can build complex objects with different types and representations of an object using the same construction code. The player is built from a builder class that is letting possible the creation of two separate players, a boy and a girl.

Each player has its own attributes, clothes and behaviors, and constructing them is made by a mechanism that is independent on the process of making these objects. 

An interface containing several parts of the player object is created, and then a builder class and method takes these parts and creates the concrete player objects. It is an advantageous pattern because it allows for different representations of objects created by a common interface.

*Prototype*, used for storing a generic player character with initial properties and creating player instances by cloning it – instances that are the players in the game, the boy or the girl. The time to create a player that is usually a costly object when it comes to creation time and memory occupied that has a long life.

It is advantageous to clone the objects each time you need time in order to avoid explicitly using the constructor’s call, it can create a collection of prototypes that can be used to generate new objects, like boy/girl players. One setback this design pattern is creating objects sharing the same resources, which is a shallow copy.
