# 2204331 Ben Powell
# Ben Powell Project Commentary
Repository Link: [Repo](https://github.com/Warius5/FMP_Prototype_BenPowell/tree/FMP)

Itch.io Build: [Itch](https://warius5.itch.io/turn-based-auto-battler)

Video link: [Video Demonstration](https://youtu.be/y-19JoRGPuk)

## Project Outcome

This project aim is to create an autobattler prototype system, with item equipping, turn based combat, and an overall progression map that is used to go between the battles. 

For the project i want to make use of a different sort of layout/ architecture of the parts of the project than i am used to, where i would normally use a object oriented design to structure the project, i want to use a more data oriented structure. Other than gaining experience creating and designing a system that uses a different sort of methodology than have before, using a data oriented approach seems a better way getting through the turn based and stats based combat of the game. Using managers and passing data and events between them to complete the battle and ui logic means its all centralised in one place makes using turn based more easy as its all in one manager rather than spread out between different places.
I also want to have a lot of the parts be dynamic in their creation, where rather than all manually made / assigned by me specifically, i want the set up and generation of the map especially to be create in a script, with limited interaction.
I think the one of the more difficult things will be making the map in an good way, as there are many possible ways of having the map tree, and having not done something like that before, figuring out the way to do it may be hard so some trial and error may be needed.
As the project goes on, being able to go back through and fix things within the managers may cause issues, as things could become to entangled with each other, so changing or adding things may become somewhat problematic. Hopefully I can keep on top of it, or at least make use of events and functions to separate out the logic to avoid.


## Organisation

* Using Github for version control, as is what i've used before, and allows me to keep saves of the unreal project that can be easily added to from different computers and keeps past versions in case anything breaks horribly.
* Using a Trello board to make a time plan, using a Kanban structure, as the development was mainly in steps of things being done, so not a lot of backwards cross to other mechanics. Therefore, the tasks can go along the stages on the board as i complete parts. Which fits with the ethos of Kanban.
https://trello.com/

<iframe src = "https://trello.com/b/KM5ifd0c.html" frameBorder="0" width="100%" height="700"> </iframe>


[If the embed doesnt work](https://trello.com/b/KM5ifd0c/fmp-proper)

* I will also try to keep ontop of using proper naming and file strucure for my files, and where i forget to, or cannot. I will try to make the actors, variable and events names be clear and useful.
* Also using comments within the blueprints to explain key parts or purposes of the main nodes.

## Research

---

###  **Methodology**

* Used a range of sources: **games**, **academic papers**, **technical documentation**, and **user feedback**.
* Focused research around three areas:

  * Turn-based combat systems (gameplay structure)
  * UI/UX design and feedback
  * Procedural map generation
* Carefully selected games that reflected **specific mechanics** relevant to the vision for my game, rather than genre alone.
* Supplemented academic research with:

  * Unreal Engine documentation
  * Community forums
  * **ChatGPT** to clarify and explain solutions that were unclear or scattered in other sources.
* Conducted iterative **user testing** via surveys and gameplay observations to validate interface clarity and gameplay mechanics throughout development.

---

###  **Game Sources**

#### *Super Auto Pets* (Team Wood Games, 2021)

* Auto-battler featuring drag-and-drop item mechanics and simple turn-based combat.
* Pets have two stats (attack and health), which **reset after each round** unless changed in the shop phase.
* Influenced:

  * My item equipping system (drag-and-drop)
  * Stat display feedback (colour coding)
  * Decision to use **automated combat** rather than player-selected actions.
* Strong UI feedback through colour, sound, and animations inspired my use of hover indicators and clear stat visuals.

![Super Auto Pets](https://shared.cloudflare.steamstatic.com/store_item_assets/steam/apps/1714040/ss_f61be4caff97d77b7df02bcdadee2687232e991f.1920x1080.jpg?t=1680944541)
(Team Wood Games, 2021)

---

#### *Darkest Dungeon* (Red Hook Studios, 2016)

* Roguelike turn-based RPG using strict initiative-based combat.
* Characters act one at a time, each with individual animations and positional effects.
* Inspired my **sequential turn logic** — each character performs a full turn before the next, improving clarity and animation feedback.
* Helped inform pacing and attack presentation in my battle system.

---

#### *Peglin* (Red Nexus Games, 2022)

* Roguelike with turn-based battles and a **branching node map**.
* Map system inspired my **procedural node generation**:

  * Used child actor components for dynamic node creation.
  * Adapted from static to procedural structure using spatial logic and depth-based generation.
* Influenced visual design for nodes:

  * Clear distinction between active, inactive, and completed paths.
  * Visual clarity of the map helped inform **UI layout and player path feedback**.

![Peglin Map Example](https://static.wikia.nocookie.net/peglin/images/4/43/Map.png/revision/latest/scale-to-width-down/1000?cb=20220127024649)
(Peglin Wiki, 2025)

---

###  **Academic Sources**

#### *Turn-Based vs Real-Time Combat* (Mäkelä and Schmidt, 2020)

* Compared player preferences for different combat styles in RPGs.
* Key observations:

  * “The key characteristic of RT systems is that all, or almost all, of the gameplay takes place in real-time.”
  * Turn-based systems: “combatants act in turns, usually one at a time. Other combatants are typically unable to move or perform actions outside of their own turn.”
* Study showed turn-based combat is **better suited for party control**, supporting my design choice to avoid real-time or RT-with-pause systems.
* Identified that real-time systems can hinder multi-character control, while turn-based combat fits strategic, readable design.

![Real-Time Screenshot](https://raw.githubusercontent.com/Warius5/FMP_Prototype_BenPowell/eb3b81c56b20f7246d4caeede5c472dbea602498/FMP%202ndTermStuff/Images/RealTime.png)
![Turnbased screenshot](https://raw.githubusercontent.com/Warius5/FMP_Prototype_BenPowell/refs/heads/FMP/FMP%202ndTermStuff/Images/TurnBased.png)
![RTWPause](https://github.com/Warius5/FMP_Prototype_BenPowell/raw/eb3b81c56b20f7246d4caeede5c472dbea602498/FMP%202ndTermStuff/Images/RTWPause.png)

---

#### *Data-Oriented Design (DOD)* (Rosell Hernandez, 2022–2023)

* Explores DOD as a performance- and structure-focused alternative to OOP.
* DOD benefits beyond performance:

  * Modular structure
  * Easier debugging
  * Cleaner, centralized logic
* Quote: DOD “fundamentally changes the way a program is conceived, making it more efficient from the start.”
* Influenced my use of **centralized managers** and **data-driven systems** in both combat and map design.
* Helped avoid deep inheritance hierarchies and improved the maintainability of expanding systems.

---

#### *Wave Function Collapse (WFC)* – Procedural Generation (Gumin, 2023; Geschwärzt, 2022)


* WFC is a constraint-solving procedural algorithm originally used for texture synthesis.
* Quote: WFC is “a non-backtracking, greedy constraint solving method that is able to generate complex patterns based on a set of input samples” (Gumin, 2023).
* Can be used for generating branching or structured content based on adjacency rules.
* I researched WFC as a possible tool for procedural map generation, but chose not to use it due to:

  * Complexity relative to my needs
  * Most documentation focused on grid/tile systems
  * Potential contradictions if constraints were too strict (Geschwärzt, 2022)
* Instead, I implemented a simpler system using **manual checks and randomised node spawning**, but WFC informed my understanding of constraint-based logic.

* Using this video as a example of WFC in use, made me view the wfc in more of a texture generating way, and after looking at other ways to create he node tree, would overcomplicating things. (3D Wave Function Collapse Unreal Overview, 2024)
---

## Implementation

## UI



## Initial User feedback of prototype

[Link to results of survey](https://forms.office.com/Pages/AnalysisPage.aspx?AnalyzerToken=kicANjRSNFTOrDz91SWRa2kFrZ5jzEmN&id=DDGcBsLUVEWxZpDKgFpeqhCe_JK5EUJHqmW8pKszlMJUNzQ5MDdJMzBSUTFJQVNJNjBMQlRLNVJaUS4u)
### Results

* **Early testing focused on core UI and combat systems**, with feedback highlighting a strong desire for clearer visual indicators (e.g., turn cues, stat displays, and equipped item visibility) and a simple tutorial to ease players into the mechanics.
* **Combat pacing received mixed feedback**, with an average rating suggesting it felt slightly slow — highlighting the need to streamline animation timing or offer user control over combat speed.
* **Post-battle flow and progression expectations** (e.g., loot choices, map navigation) were frequently mentioned, which directly informed the later decision to implement a **rogue-like node-based map** to enhance player agency and long-term structure.

![alt text](<https://raw.githubusercontent.com/Warius5/FMP_Prototype_BenPowell/refs/heads/FMP/FMP%202ndTermStuff/ResearchVid/Untitled%20video%20-%20Made%20with%20Clipchamp.gif>)
![alt text](https://raw.githubusercontent.com/Warius5/FMP_Prototype_BenPowell/refs/heads/FMP/FMP%202ndTermStuff/Images/image-1.png)


![alt text](https://raw.githubusercontent.com/Warius5/FMP_Prototype_BenPowell/refs/heads/FMP/FMP%202ndTermStuff/Images/image-2.png)

* The clear details on what things do really makes it easier to play smoothly in Super Auto Pet's. Form the feedback, knowing what is equipped and how that is affecting the character, as well as seeing the stat values of the characters easily is something that is important. 

---

## **Battle Manager**

<iframe src="https://blueprintue.com/render/qanh32po/" style="width: 100%; height: 100vh; border: none;" scrolling="no" allowfullscreen></iframe>

* The destination of a lot of event dispatches, coming from UI buttons 
* Coordinates the **combat flow** between heroes and enemies.
* Controls turn order, damage handling, and end-of-battle logic.
* Integrates tightly with `BPC_Hero` and `BPC_Enemy` via `references` to trigger attacks and updates to stats or texts.
* Issues encountered included **broken references** when switching camera views — fixed by making references `Instance Editable` and explicitly assigning them in the editor.
* Integrates with the map system by triggering return transitions after battle completion (`Battle Finish to Map`).
* Uses array sorting to sort all the characters by their speed.
  <iframe src="https://blueprintue.com/render/hrwi5n5i/" style="width: 100%; height: 100vh; border: none;" scrolling="no" allowfullscreen></iframe>
* Uses a tag system to track what characters are alive, to make it easier to find who can be targeted. Rather than having to remove them from the array and possibly cause issues, just having them not show up in a array of 'alive characters' means there's less adding and re-adding to structures.
* Makes use of lots of events that often trigger each other rather than from externally, so some of them could be put into functions instead. However, as many of the events use variables and data that come from elsewhere, keeping all the logic in one place so you can follow where logic and info have come from seems like a decent bonus.
*  With hindsight, a lot of the functions probably could've been events and some of the events could have been functions. I think more planning could help with cleaning up what should go where, and streamlining logic and the amount of events. (Event/functions, what’s the main difference between them? - Programming & Scripting / Blueprint, 2016)

---

## **Characters (`BP_BaseCharacter`, `BPC_Hero` and `BPC_Enemy`)**

<iframe src="https://blueprintue.com/render/739thrz2/" style="width: 100%; height: 100vh; border: none;" scrolling="no" allowfullscreen></iframe>

* Contains the logic for health, attack stats, animations, mostly triggered from the `battle manager`.
* Visual feedback includes animations and sounds. Triggered using `Play Animation` rather than using a behaviour tree, as the animations were complex, and no nuanced player movement means partway states/ blends do not matter as much.
* Lerps used to show the turn being done, like in the super auto pets or darkest dungeon. Made it simpler than using a moving animation that would not return to the correct place, or jump around too much.
* As the main parts of the Hero's and Enemy are the same, a `BaseCharacter` is used to create a `BPC_Hero` and `BPC_Enemy`. With that mostly allow the character specific logic like setting health and triggering the visibility of the selection sphere.

---

## **Item Manager**

<iframe src="https://blueprintue.com/render/bjsyfcog/" style="width: 100%; height: 100vh; border: none;" scrolling="no" allowfullscreen></iframe>

* Handles item selection, equipping, and application of stat changes to characters.
* Uses `Data tables` to store the item stats, meaning its scalable for if new items were to be added, as well as allowing the structure to be expanded if new values were needed.
(Working with Data in Unreal Engine; Data tables, Data Assets, UPROPERTY specifiers and more! | Tutorial, 2024)
* Stat changes triggered by item usage do not persist across rounds unless by buying equipment, mimicking SAP’s temporary vs. permanent stat flow.
* Uses event dispatchers to get the equip event to trigger, and then sends out a dispatch to track the number of `equips` are left.

---

## **Menu Manager**

<iframe src="https://blueprintue.com/render/6-fpz72h/" style="width: 100%; height: 100vh; border: none;" scrolling="no" allowfullscreen></iframe>

* Controls transitions between the viewports. 
* Manages the UI being added and removed  
* Some of the logic could probably be more centrally handled in the ui blueprints themselves.
* uses the references to the game mode to set up the dispatches, as an in between the manager and other things, as it was a reference that could be made by any bp and widget. I think that this probably isn't the most necessary, if I set it up differently from the start. 

---

## **Map**

<iframe src="https://blueprintue.com/render/5adufuzu/" style="width: 100%; height: 100vh; border: none;" scrolling="no" allowfullscreen></iframe>

* The `BP_Map` sets up the node tree to use for selecting the next encounter. This involves generating the node tree dynamically and then populating it with an event. 
* Moves the player location sphere when a valid node is clicked and sets the event.
* Initially considered using `Wave Function Collapse (WFC)` (Gumin, 2023), but was found to be overengineered for the project’s linear tree structure — instead a dynamic generation of the tree, using 'self replicating nodes' using a `TMap_LocationMap` to control placement, and then an array to be stored. (Map Containers in Unreal Engine | Unreal Engine 5.5 Documentation | Epic Developer Community, s.d.) (How to... Map Variables, 2021)
* Construction
<iframe src="https://blueprintue.com/render/evp23jg7/" style="width: 100%; height: 100vh; border: none;" scrolling="no" allowfullscreen></iframe>

* Constructing the tree - starts at the node, and uses the LocationMap to store it, using its location as the key. Adds the node to the array. and then generates 2 child nodes through `Node making`. Then loops for a specified amount, and calls node making for each one.  
<iframe src="https://blueprintue.com/render/i9c2jav1/" style="width: 100%; height: 100vh; border: none;" scrolling="no" allowfullscreen></iframe>

* NodeMaking - Done for left and right for each node. The new nodes are spawned a set distance away from the 'current' node. This location is first checked against the `Tmap LocationMap` as a key. And if it is the node is spawned as a child component and is added to the array. 
<iframe src="https://blueprintue.com/render/wfx1r9jd/"style="width: 100%; height: 100vh; border: none;" scrolling="no" allowfullscreen></iframe>

* This set up allows the current use of the nodes as child components, and as the connections generate they are made, there are no issues having to try and go back through and figure out where the nodes are, and then where the player will be able to go.



## [Link to showing Map working](https://youtu.be/4-OyRDOcjKk)


### Old Map
![alt text](https://raw.githubusercontent.com/Warius5/FMP_Prototype_BenPowell/refs/heads/FMP/FMP%202ndTermStuff/Images/image-6.png)
![alt text](https://raw.githubusercontent.com/Warius5/FMP_Prototype_BenPowell/refs/heads/FMP/FMP%202ndTermStuff/Images/image-7.png)

[Old logic](https://blueprintue.com/render/fcwh048q/)
* This old logic was my first idea on how to create the connected nodes, however due to the relative vs actual location, and using child components of a normal actor, made figuring out how fix any issue quite difficult. It was also done after the fact, so the tree would be made manually.

* Originally wanted to use datatables to save the enemies, however they could not be done at runtime. I researched into custom plugins that would allow that, but it added alot of complexity that wouldn't give anything saving as a struct would couldn't.(Runtime DataTable, s.d.)

[Link to plugin](https://www.fab.com/listings/5c77947a-5096-438f-91fb-a28729a34b57)





* Boss Making - To be able to be done at the end, no matter the size of the tree.
* The end nodes then have their left and right nodes set to the boss to make it connected.


---

## **Node**

<iframe src="https://blueprintue.com/render/j_2ou7bj/" style="width: 100%; height: 100vh; border: none;" scrolling="no" allowfullscreen></iframe>

* Represents individual progression points in the map tree.
* Stores depth, difficulty, and connections to `LeftNode`, `RightNode`, and `ParentNode`.
* Uses `ActorOnClick` and `Interfaces` to trigger selection and movement logic in `BP_Map`. (Interfaces in Unreal Engine | Unreal Engine 5.5 Documentation | Epic Developer Community, s.d.)
* Stores the enemy event after its generated, so when its clicked its sent to the map, which sends it to the battleManager.
* Has a border that changes its material depending on whether its valid or not to give a visual indicator to the player.
* Difficulty selected using the randomly selecting the current or previous depth, and feeding that into a switch that triggers different `Function Libraries` that contain getters to get data from data tables.
* This gets the range of stats in a `struct` which are then fed through `Structpop` to get the actual values. (Structs in Unreal Engine | Unreal Engine 5.5 Documentation | Epic Developer Community, s.d.)
* Using structs and function libraries feed into the more data oriented design i am going for, which makes it easily usable, scalable and changeable if i need to add more data.
* When the node is clicked on its checked whether its currently valid to be clicked, and then sent through a interface to the map to trigger the move.
---

## **Audio Manager**

<iframe src="https://blueprintue.com/render/4llax9j5/" scrolling="no" allowfullscreen></iframe>

* Handles sound effects and music cues across different parts of the game.
* Plays at the start, with a link to the options menu that will turn the music on and off. 

---




# Testing

Not clear what order to equip in, some click the item before selecting the hero to equip.
Not clear what is health or attack

[Video showing confusion](https://youtu.be/MOX6ynnFVkY)

When going between rounds the hero selected stays, so if you press a button it 'equips' even when one shouldn't be 

[Video showing Issue](https://youtu.be/MOX6ynnFVkY)

Player was unsure on how the order / distance of each of the characters are significant or work.
Some sort of explanation of it being random could be good.
They also beat the boss and there was no screen to retry or end, as i had forgotten to add one for that scenario while i was doing the losing one.
Some sort of visual indicator of damage taken was requested as if there's no deaths its somewhat hard to tell what has happened.

If the tester was fast enough they could click on a multiple nodes and skip, but non valid nodes could still not be clicked.



# Polish and Testing based fixes

[Link to results of survey](https://docs.google.com/forms/d/1U_z3QnWBpURIj_iwKYPRiUs4XDgG9Hy1ulCgtZFZiwg/edit#responses)

I fed the results into Chatgpt to give me key areas that need improvement or adding.
| Area             | Action Items                                                              |
| ---------------- | ------------------------------------------------------------------------- |
| Tutorial/Clarity | Add intro tutorial, improve UI clarity, fix overlapping text              |
| Player Feedback  | Better responses to actions (equip, win, fail), improve damage indicators |
| Animations       | Add simple animations inspired by JRPGs and tactical RPGs                 |
| Gameplay Systems | Consider risk-reward mechanics and experimental combat styles             |
| Visual Polish    | Refine character visuals and ensure UI readability                        |

The key take away from the feedback on things that can be improved is by giving better instructions on what to do, make it clearer on what is going on.
By fixing the texts and adding more for clarity and explanations, and then adding animations or effects to show interactions and feedback.

Attack animations, moving the text and background music.



## Animations and skins

Got skeletal mesh and attack animations from mixamo.
Tried attack and idle animations, using `Play Animation` to add a simple animation on the attack, but the one i used moved the character while in the animation and because the character also moves it causes some issues. So rather than using an animation that moves, having the character move and the animation be an in place one should fix without having to overcomplicate things.
Added event to character called take damage to play a getting hit animation when it is targeted in the battlemanager.
Added animation to walk back while reseting but check if it needs to move and doesnt play animation if doesnt.


## UI And Options

<iframe src="https://blueprintue.com/render/1sty41yg/" scrolling="no" allowfullscreen></iframe>

Moved around the text and added more to explain things better.

## Fixing Boss win and map problem

Checks if the current node is the boss node when it wins.
need to stop being able to click, or triggering the selecting node.



# Reflection

## Research
I've made use of a range of research, whether it be from academic, games and documentation. I used academic sources to affect some decisions in related to the underlying game, being the decision to use turn based for the game as apposed to live battling. By looking at games like super auto pets and other turn based battlers, it helped decide how the turns would laid out, where the option of one after the other, or the front ones at the same time. This game having the enemies be one big one rather than multiple small enemies, having the game be one after the other fits better.
I think perhaps having a better idea around the underlying systems of the games i took interest in, such as Peggle for its map, or super auto pets for the item equipping, may have let me have a better idea of how they were made and why they were done like that to either change the way i made it or make it easier in my implementation. 
Perhaps having a better overview of the technical hurdles i would overcome from the beginning and instead making quick separate prototypes of all my systems, and researching what way would be the best to go forward would help in being more efficient in the structure and implementation.

## Positive
I really enjoyed the problem solving involved in creating the Map's node tree, going through multiple iterations of where and how it was done. Being able to step back and look at another way of implementing it enabled me to use the TMap and learn how they worked. As i went,  i felt i made use of better structuring techniques, such as 
when to use functions and being more concise in layout and variable etc usage. 
The change in style of how i made the game, where instead of using object oriented design, using data oriented and managers, was successful in showing there are alternate ways of organising a project. The managers made it easier to control and figure things out, but having to send things around to places did get a bit tedious, but i wouldn't be surprised if there were better ways of doing it. 
I'm glad i made use of some testing, to get feedback on whether the game was good to play and what parts in the ui needed fixing. 

## Negative Analysis

My biggest issue was definitely the lack of a clear structure and 'plan of attack' on how to get to the end goal. This led me to make a lot of it up as i went, and led to inefficiencies and mess when connecting back to a previous system. It also led me to having a bit of a negative attitude in terms of getting into doing the work, as the unknown's somewhat crushed my willingness to start working. 
I think that a more refactor open mindset to the systems would have benefitted me, as there were a few occasions that i was limited or slowed down by previous systems or ideas, that were probably not the best done, that did not work very well with what my idea was at the time, so it would take longer to get it to work correctly, than if i had redone the previous connection to work better.
I think my mindset in terms of creating something that was more professional could have been better, as I felt like i was treating it less seriously as a 'public facing' project, so certain things like polishing more in a player facing way was lacking until the end which made it more rushed than it should have. 
I also wished i made better use of the trello board to keep up with times, and plan better. But as i lost track of the priorities of the project, i mostly neglected the trello board as i went.

## Next Time

In the next big project i do, i want to ensure i have a more defined architectural plan, possibly going to a designer to properly design the different systems required, with more expertise. This clarity would then allow more structure and better code and systems, and make it look more professional. 
Lending more time to creating visuals like vfx etc could be good, as i had neglected those components until the end making those additions need to be added at end messily rather than built from the start.
Making the project more modular and structured to make development easier and more understandable is something i would also like to do more of.  


# Bibliography

Team Wood Games (2021) Super Auto Pets [Video game]. Developed and published by Team Wood Games.

Red Hook Studios (2016) Darkest Dungeon [Video game]. Developed and published by Red Hook Studios.

Mäkelä, V. and Schmidt, A. (2020) 'I Don’t Care as Long as It’s Good: Player Preferences for Real-Time and Turn-Based Combat Systems in Computer RPGs' In: Proceedings of the Annual Symposium on Computer-Human Interaction in Play. CHI PLAY ’20: The Annual Symposium on Computer-Human Interaction in Play. Virtual Event Canada: ACM. pp.231–240. At: https://dl.acm.org/doi/10.1145/3410404.3414248 

Geschwärzt, J. (2022) Procedural Generation of Buildings Using Wave Function Collapse. Bachelor’s Thesis. HAW Hamburg. Available at: https://reposit.haw-hamburg.de/bitstream/20.500.12738/15709/1/BA_Procedural%20Generation%20of%20Buildings_geschw%C3%A4rzt.pdf 

Map Containers in Unreal Engine | Unreal Engine 5.5 Documentation | Epic Developer Community (s.d.) At: https://dev.epicgames.com/documentation/en-us/unreal-engine/map-containers-in-unreal-engine .

How to... Map Variables (2021) At: https://www.youtube.com/watch?v=3mHjybsLhc0 


Event/functions, what’s the main difference between them? - Programming & Scripting / Blueprint (2016) At: https://forums.unrealengine.com/t/event-functions-whats-the-main-difference-between-them/351110 

3D Wave Function Collapse Unreal Overview (2024) At: https://www.youtube.com/watch?v=ZFA3uCg_Peg 

Structs in Unreal Engine | Unreal Engine 5.5 Documentation | Epic Developer Community (s.d.) At: https://dev.epicgames.com/documentation/en-us/unreal-engine/structs-in-unreal-engine 

Working with Data in Unreal Engine; Data tables, Data Assets, UPROPERTY specifiers and more! | Tutorial (2024) At: https://dev.epicgames.com/community/learning/tutorials/Gp9j/working-with-data-in-unreal-engine-data-tables-data-assets-uproperty-specifiers-and-more 

Interfaces in Unreal Engine | Unreal Engine 5.5 Documentation | Epic Developer Community (s.d.) At: https://dev.epicgames.com/documentation/en-us/unreal-engine/interfaces-in-unreal-engine 


## Declared Assets

Chatgpt

All animations and skeletal meshes from Mixamo

Music from Pixabay:
punch | Royalty-free Music (s.d.) At: https://pixabay.com/sound-effects/punch-95294/ (Accessed  22/05/2025).
Medieval Adventure | Royalty-free Music (s.d.) At: https://pixabay.com/music/beats-medieval-adventure-154671/ (Accessed  21/05/2025).
