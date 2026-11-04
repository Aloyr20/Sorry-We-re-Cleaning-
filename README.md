# Game-Engines-Check-In-Sorry-Were-Cleaning

Game-Engines Check In submission for our GDW game Sorry We're Cleaning!

## Group Formation
When making the team, Luke and I considered the possibility of forming it from the people that we know. We have been friends for quite a long time now and have worked together on numerous projects. Our previous assignments involved the Computer Graphics final assignment, as well as GDW games such as Duncrawl. Being the same team members in GDW, it was very logical that we will cooperate and develop our GDW game together. Thanks to these previous assignments, we were able to familiarize ourselves with each other’s skills, work style and way of solving problems.

## Game Description
Sorry, We’re Cleaning! is a cartoonish, low poly, stealth game where players will control a thief-cleaning robot, which will steal all valuables from their owners without getting caught. The task of players is to extract some objects for further sale, while pretending that they are cleaning the house.

Players move through the house, grapple to different surfaces, dash and hide from homeowners, and take objects which will have physics. In case players drop these objects, noise will be made, so homeowners will try to catch them. After stealing, players go to the store, buy new upgrades and proceed to another house.

Some planned features include nail-based grappling, procedural generation of houses and objects that players will try to steal and which will be able to fall and make noise attracting the homeowners.

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


## Video Report










 
