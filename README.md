# Game-Engines-Check-In-Sorry-Were-Cleaning

Game-Engines Check In submission for our GDW game Sorry We're Cleaning!

## Group Formation
When making the team, Luke and I considered the possibility of forming it from the people that we know. We have been friends for quite a long time now and have worked together on numerous projects. Our previous assignments involved the Computer Graphics final assignment, as well as GDW games such as Duncrawl. Being the same team members in GDW, it was very logical that we will cooperate and develop our GDW game together. Thanks to these previous assignments, we were able to familiarize ourselves with each other’s skills, work style and way of solving problems.

## Game Description
Sorry, We’re Cleaning! is a cartoonish, low poly, stealth game where players will control a thief-cleaning robot, which will steal all valuables from their owners without getting caught. The task of players is to extract some objects for further sale, while pretending that they are cleaning the house.

Players move through the house, grapple to different surfaces, dash and hide from homeowners, and take objects which will have physics. In case players drop these objects, noise will be made, so homeowners will try to catch them. After stealing, players go to the store, buy new upgrades and proceed to another house.

Some planned features include nail-based grappling, procedural generation of houses and objects that players will try to steal and which will be able to fall and make noise attracting the homeowners.

## Game Screenshots
<img width="1290" height="866" alt="{092437A5-678C-425C-BCBA-A5C945DAB4A2}" src="https://github.com/user-attachments/assets/4d231d5e-4bf9-4a85-8489-f2fcdb60d60f" />
<img width="1919" height="860" alt="{061B3E19-1504-461F-AC41-959CA74E056B}" src="https://github.com/user-attachments/assets/5cc4c91f-f9d3-42a7-ad20-1225530aac1c" />

## Planning
We used a Miro Board to brainstorm ideas for implementing each of the design patterns
<img width="1406" height="1008" alt="{6687E307-09B1-4107-8304-341F22112520}" src="https://github.com/user-attachments/assets/ecb3c70a-4143-4a08-940e-3ea1528b0341" />

We used Click-Up to plan out the tasks for completing the assignment and to make our Gantt Chart
<img width="1523" height="521" alt="{F16AF081-0122-4155-99FE-259B90195D76}" src="https://github.com/user-attachments/assets/2e13b93a-38a3-4b09-99a1-bdd2a756401b" />
<img width="1827" height="644" alt="{4CDD3D0C-6B5D-4B97-8BDC-60086C7EF49A}" src="https://github.com/user-attachments/assets/e2b53748-0ea7-479c-9e1f-e97f0c3c03bb" />


## Work Breakdown

The breakdown that we had for this assignment was 60/40, Luke being the 60%, Augie being the 40% as Luke did the DLL. Everything else was evenly split.

# Luke
- Made the game instance hold multiple singletons
- Made the game manager singleton and tester blueprints
- Made a factory for mess spawning that spawns puddles right now
- Used a command pattern for storing jump inputs (can be expanded for other commands)
- Made a dll that stores variables (puddle size right now) that's easily expandable
- Did some of the brainstorming of what to implement in Miro

# Augie
- Converted the Audio Manager class to be a singleton and added it to the game object
- Added the Audio Manager to the radio and door blueprint classes
- Implemented the shop functionality and undo feature for purchases and used the command design pattern for it
- Created the valuable items spawn and implemented the factory design pattern for it
- Described the formation of the groups and game description
- Participated in making the diagram and description of our work
- Participated in creating the README on GitHub and video report


## Singleton Implementation: Audio Manager (Augie)
Singleton design pattern is used in the audio system where the Audio Manager object saves a reference to itself inside the BP_CustomGameInstance once the game starts. Radio and doors use this same reference to play/stop/suspend music and sound effects. It allows separation of audio processing from objects that are asking for that and gives a common way to access it. This is helpful for the game as it avoids any duplication of blueprint code and makes it easy to manage audio behavior.

## Audio Manager Screenshots
<img width="1456" height="482" alt="{D5033C88-E548-4DED-835E-F612E1EE40CF}" src="https://github.com/user-attachments/assets/9b26f84f-a14b-4811-9db9-318a1989fe8f" />
<img width="1891" height="771" alt="{F5C6A9A2-6E1C-4AF4-B398-747F2EE5795D}" src="https://github.com/user-attachments/assets/4962b04b-57c6-447e-8da9-6b182f558e7c" />

## Radio Blueprint Screenshots
<img width="1501" height="731" alt="{8B582039-9599-40E4-A2BB-C25D45C1FF9C}" src="https://github.com/user-attachments/assets/1398bc2a-5917-41b4-824c-7ed4a59db7c8" />
<img width="1582" height="438" alt="{4B80B8CF-3528-41ED-8CD4-C90D58B7F863}" src="https://github.com/user-attachments/assets/c76e4638-8471-4fc4-b6c6-30ef31751228" />

## Door Blueprint Screenshots
<img width="1695" height="667" alt="{D981107F-059F-4D4D-AC51-774AFC6110A8}" src="https://github.com/user-attachments/assets/7ba0e2ff-8a16-4763-9aff-57ca0502c7f0" />
<img width="1275" height="670" alt="{8488765C-8CFA-405E-96A5-30B17C9FA36F}" src="https://github.com/user-attachments/assets/1e613b30-1c4b-4a60-9270-89bb2e02a7f8" />
<img width="1850" height="755" alt="{5C6E96B6-C0E5-47DA-9685-1A864504671E}" src="https://github.com/user-attachments/assets/117ccb23-f669-4274-adba-bb659e89af1e" />

## Audio Manager UML Diagram
<img width="1179" height="726" alt="{1FEC94BB-FBDD-49C3-B4B7-69A255505D38}" src="https://github.com/user-attachments/assets/e1a2e9e1-a683-4095-92ae-27c0cbd98878" />

## Factory Implementation: Valuables Spawner (Augie)
The Factory Pattern is instantiated via the BP_ValuableFactory, which spawns an instance of the Blueprint class stored in its ValuableClass variable at its location. During the initialization process called BeginPlay, all of the factories located in the world, as well as their children, are located by the Valuables Manager, which calls SpawnValuable for each of them. In this way, the spawning process is separated from the object instantiation process. This design helps in the game in reusing the same spawning code for different stealable valuables.

## Valuable Manager Screenshot
<img width="1392" height="488" alt="{F467A67D-C378-4DC1-A7A2-6D70613F5121}" src="https://github.com/user-attachments/assets/91c00b64-2018-4037-9286-a4aecc8a381a" />

## Valuable Factory Screenshot
<img width="989" height="516" alt="{5412D28A-61D1-43F9-A6D2-977014CF29C6}" src="https://github.com/user-attachments/assets/27c411b3-59d1-4bac-b2af-0f2c8617c2bc" />

## Valuable Screenshot
<img width="919" height="444" alt="{19FDC78C-32F5-454F-9191-71C600E13208}" src="https://github.com/user-attachments/assets/fad4e718-97d3-4810-aa8d-169701ed78ca" />

## Valuables Spawner UML Diagram
<img width="987" height="605" alt="{B93E9E53-5E5A-4B6F-8FCE-A90BBF6E4870}" src="https://github.com/user-attachments/assets/4e394d88-d1c8-43d3-b04a-e7f960ab699a" />

## Command Implementation: Shop Refund System (Augie)
The Command pattern handles each purchase of an upgrade as an independent command entity with Execute and Undo events. In case of speed and jump commands, the value of the last move is saved before the application of the upgrade, and the shop stores the commands in its history list but also deducts the purchase price. The refund process simply executes the Undo operation on the latest command and returns the cost of the command. It is important to separate the logic of upgrades and shops and provide all necessary data for undoing players' purchases.

## Upgrade Shop Screenshot
<img width="517" height="809" alt="{40B4F2D4-1F1B-4E63-BF08-BAE4CE7911AC}" src="https://github.com/user-attachments/assets/598093bb-a803-48c9-83b6-627c90918b59" />
<img width="1659" height="513" alt="{5A1F1B5F-E22C-48BC-9277-0418FFE35568}" src="https://github.com/user-attachments/assets/5a54b036-21ba-488e-8bf0-288180824f6f" />
<img width="1834" height="363" alt="{0EB887E8-8E3C-400C-BD25-24DBADA631B6}" src="https://github.com/user-attachments/assets/58a04d2b-4a10-4657-bfd2-c8bf987f9fce" />

## Upgrade Base Command Screenshot
<img width="689" height="549" alt="{87902F5A-FB68-48B8-A3C4-1392400E5B22}" src="https://github.com/user-attachments/assets/98d1fd78-3a35-4a70-b678-ff071a7a3a1b" />

## Jump Upgrade Command Screenshot
<img width="1371" height="741" alt="{9D4E9372-4CAA-4B76-9356-C837683661B2}" src="https://github.com/user-attachments/assets/c2104959-495c-417b-af62-3fe172c5b851" />

## Speed Upgrade Command Screenshot
<img width="1272" height="805" alt="{82F75E31-52F6-4567-8E47-FDEE5EA77914}" src="https://github.com/user-attachments/assets/66e2622a-6bd4-41d8-baa2-0efe37da74e9" />

## Shop Refund System UML Diagram
<img width="1149" height="707" alt="{DDB2E8E4-CCBD-4AA2-ABF1-B9C7AD6E0DA2}" src="https://github.com/user-attachments/assets/56ba9d1a-f4f1-4e2b-a908-676786abfefb" />

---

# Luke Explanations/Pseudocode

**Singleton**:

-Set the game instance to a custom instance

-Make variables for each singleton in the custom instance

-The singletons are actors and are placed in the scene

-In the BeginPlay events of each actor, there's a short delay, then they get the game instance, cast it to the custom game instance, get the intended singleton variable, and set it to the actor itself.

-To use a singleton from any blueprint, we get the game instance, cast to the custom game instance, get the intended singleton variable, then set or get one of its variables.


That's the design/implementation. Technically, simply using a custom game instance itself directly AS a singleton is a cleaner and faster approach, however the downside is that you could only have one singleton. Also technically, the "best"/cleanest option to have multiple singletons would be to use Unreal's subsystems, however the downside is this requires usage of C++ which I don't understand well at all. Therefore, the best solution was to use a custom game instance as a container that simply holds references to different singletons, that can be accessed globally. The singletons are actors instead of objects so that they have access to the BeginPlay event, which triggers their assignment to the singleton variables in the custom instance. They have a small delay to ensure that the custom instance is all sorted out before we try to assign variables to it.

Our game benefits from singletons because instead of juggling objects of a game manager, trying to keep them in sync in different blueprints, or having it be an actor in the world and finding references directly to it, we can simply get a reference to the custom game instance and get the singleton there. This allows a game manager to be guaranteed synced in all files, and easily accessible in any blueprint that's doing any task. If you want to track a new variable in the gamemanager singleton, for example we want to track doors opened, you simply make a new variable in the gamemanager, access it and increment its value in the door open event, and now it can be accessed in any other blueprint. It's that easy. For the audio manager, it allows for cooldowns that are definitely synced in all files, so sounds play at a consistent rate, etc, and prevents having multiple copies of the same thing which burns memory.
<br>
<br>
<br>
<br>
**Factory**:

-We make an actor blueprint called MessBase

-Make a child of the MessBase and give it a static mesh

-Make an actor blueprint called MessSpawner

-In MessSpawner, make a variable of type MessBase, make it instance editable and public

-In MessSpawner, make a custom event, spawn actor of the above variable class

-Make a child of MessSpawner containing the name of the child of MessBase created earlier

-Place the child of MessSpawner into the level, then set its MessClass to the child of MessBase with a static mesh

That's the design/implementation. It's very easy to repeatedly duplicate that child of MessSpawner anywhere and spawn as many messes as you'd like. We use a factory to be able to very easily change any qualities of these messes. If we want their location to be random, we can very easily, in the child of MessSpawner, on BeginPlay or in the construction script, set the actor scale to something else, offset its location by a random amount, or anything of the sort, and it would happen instantly to every mess that spawner spawns. This lets spawning logic be a lot more modular and easily changed, so while playtesting, we can test different parameters and effects to make messes feel more fun, without repeatedly rewriting code or finding different blueprints.
<br>
<br>
<br>
<br>
**Command**:

-Make an interface called Command with just one function inside: Execute

-Make an object called CommandBase, click Class Settings, add an implemented interface, select the Command interface from earlier

-In CommandBase, add a variable ExpirationTimer of type float, and a variable PlayerObj of type BP_Player

-Make a child of CommandBase with the name of the intended command, e.g. CommandJump

-In the eventgraph you should see the Execute event from the interface, make it call the Jump function, set Jump's target to the PlayerObj variable

-In the player blueprint (BP_Player), make a variable called QueuedInputCommand of type CommandBase object

-Where you have your normal inputaction for jumping, make its event construct an object from the class CommandJump, set its expirationtimer to an appropriate value

-Set the PlayerObj variable in CommandJump to the player blueprint (reference to self)

-Set QueuedInputCommand to be the CommandJump created

-Make the Event Tick event check if the CommandJump object is valid, if it is, subtract deltaseconds from the expirationtimer of the QueuedInputCommand

-If the expirationtimer is greater than 0, and the player is not falling, call Execute of the QueuedInputCommand


That's the design/implementation. From a high level overview: when the player presses jump, turn it into an object and hold it. It has a set time that counts down before it's no longer queued. While it's still queued, if the player is on the ground, we call Execute which actually enacts the jump. We use commands in this way to be able to queue inputs, which can make the game feel more responsive, and have the controller be more forgiving. If you press the jump button only 50 milliseconds before you hit the ground, by default the jump will never occur, but we queue jumps using the command pattern so that you can configure how much time before you touch the ground that you can hit the jump button and have it still work. It's implemented in this way because it's essentially the most natural way I could think to implement this pattern. It's a fairly simple pattern, as all it requires is to be able to store an input as an object for later, so we simply have an object variable that holds it. To make sure it doesn't work even after your configured time, we simply decrease the expiration timer in real time and make sure it didn't expire. We use an interface so that we can just call Execute on the CommandBase and it finds it easily, I tried avoiding using an interface originally but it appeared to be finnicky with actually finding/executing the Execute event.
<br>
<br>
<br>
<br>
**DLL**:

-Make a new visual studio C++ dll project

-Go to Project -> Properties -> Configuration Properties -> C/C++ -> Precompiled Headers, and set them to off

-Make a .cpp file with the name of your DLL, e.g. Unreal_DLL, export whatever variables you'd like as getter methods

-Declare method bodies below

-Build the dll, then put it into your Unreal Engine project Binaries/Win64 folder

-In your Unreal solution, add a library header file that uses CoreMinimal and BlueprintFunctionLibrary.h to define the blueprint access type (does it have execution pins or not) and define the type and parameters of your methods with UFUNCTION declarations

-As private variables, use typedef to define your types

-In the corresponding cpp file, we define pointers to the previously described methods, and define the actual return values that will be used when calling the methods in blueprints

-In Build.cs for Unreal, I replaced "Binaries" with "EditorBinaries" as a different place to hold the binary, so when building it doesn't cause issues trying to build on top of itself. The normal Binaries folder is still used by the editor to load the dll, but when building, it helps a lot to have it in that other folder

-We make a blueprint function library (from the C++ class menu) that will actually be used to call our dll in unreal with almost identical code to the original Unreal_DLL_Library.cpp and header files

-We close unreal and visual studio then generate visual studio project files

-In the level blueprint in unreal, we load the dll, then can call the getter methods to access the variables

-Now we can directly call getter method names in any blueprints and it works flawlessly. In our game, we use a puddleSize variable for the puddle spawner factory, which takes in the dll value then sets every puddle to that scale.


That's the design/implementation. It was implemented in this way as to be quite frank, it was the way taught in the class slides. However, I use the dll only for getter methods for variables to use the dll as a, quite literal, package of variable values that can be easily swapped. Being able to use dlls in this way is EXTREMELY useful for rapid balancing and playtesting, as sets of values can be shared extremely easily by team members. For example, imagine you believe your game feels better with the player being a bit slower, and enemies being a bit faster. If you want your team to experience the new variable values, you could edit the scene and push it for everyone, causing problems if they were also editing it. To avoid that issue, you could duplicate the scene, taking up significantly more space and also requiring team members to git pull. To avoid any and all issues, you could simply tell every member of your team to set the playerSpeed to 11.2, and the skeletonSpeed to 12.5, and whatever other variables that you thought should be changed, however this takes time and effort, also requires members to put the values back to normal if they want to go back. What's the ultimate solution? a dll that holds only variable values and getter methods to access them. You could have a dll for high player speed slow enemies, a dll for faster projectiles and larger explosions, even set the values of every single variable in your game (hundreds?) differently in different dlls, and team members can instantly try out whatever values you have set by slotting it into a build or into their editor folder. This is an amazing concept and is something I'll be using for probably every single game I'll ever make for the rest of my life.

---

## Video Report










 
