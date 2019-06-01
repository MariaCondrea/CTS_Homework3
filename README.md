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

## Structural Design Patterns

*Decorator*, which can be used to dynamically change the behavior of an object at run time by wrapping them in an object of a decorator class. The special remote control toy used by the player is a case in which the decorator is handy. The remote control toy has behaviors attached to it during the gameplay, as the player switches between the attacks.

It is an advantage to use this pattern as the decoration is transparent to the user because the class that manages the remote toy inherits the specific interface that decorates with the behaviors of the attacks.

*Façade*, as it can create an intermediary layer between all the classes related to the player and monster behavior in the form of a game manager class. This way, the façade provides a simplified interface to a complex system. 

The classes are not modified at all; they interact with the intermediary layer, which allows a better management of the classes in order to use methods from multiple interfaces. A disadvantage of this pattern is that it increases the number of existent classes and complexity of the existent code and it can negatively affect the game’s performance.

*Flyweight*, because it can be used to store shared aspects of the playable characters and NPCs (zombie toys), like their models, textures, animations, separately from the individual aspects, like their position, health in a transparent way. 

This way, the memory occupied by objects is reduced by sharing them between clients or their status between other objects of the same type. However, the effects are only visible for solutions where the number of objects is large, which can’t really be the case for Zombie Toys.

## Behavioral Design Patterns

*State pattern*, which implements a state machine in an object-oriented way. With this pattern, a state machine is implemented by implementing each individual state as a derived class of the state pattern interface and implementing state transitions by invoking methods defined by the pattern’s superclass.

In the case of Zombie Toys, the pattern is used to store the players’ and toys’ several states, in essence, attacking, walking, and fleeing. Each can have its own update method and whatever other data it needs, like storing which character is attacking or running from, the area it is wandering.

*Observer*, in which an object called subject, maintains a list of its dependents, the observers, and notifies them automatically of any state changes, usually by calling one of their methods. This employs the integrated concept in the Model View Controller.

The usage of the pattern in this game has the renderable representation of a character listen to events from the logical representations, in order to change the visual presentation when necessary, without the game logic needing to know anything about rendering the code. This MVC is represented by the game manager, that observes each of the player and their interactions with the zombie toys and allies.

*Template method* defines the skeleton of how a certain algorithm could be performed, but defers the implementation of those steps in the children classes.

In the case of Zombie Toys, template sets up the generic combat routine of the players/zombies, with various functions to handle each step, like calculating the hit chance, resolve hit or miss, compute the damage and each of the type of attack skill will implement the methods in their own specific way, like Frost Attack freezing the zombies and leaving them vulnerable to shots.
