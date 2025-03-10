# 2204331 Ben Powell
# Ben Powell Project Commentary

### Planninng for term

<P> After using mostly blueprints for the prototype, i want to take the current state of the game and use it to practice C++ and specifcally Unreal C++, and as i already have things done in the project it will be easier than figuring it out from scratch. 
<p> To better figure out how to turn it from blueprints, to C++ i want to create a proper map of the workings of the project, so i can better see how the different parts and managers interact with each other. This will help me be able to fix or change things, and then also how to expand it from the current.
<p> I will use user feedback to inform my choices going from my prototype and see what people would or expect there to be in the game.
<p> I also want to try to use procedural generation to create a roguelike system, as i have not used it before. So there may be some issue making that work with the overall context of the game.
<p> I want to create a game that feels good for someone to play, where the choices of which item or choice they pick will be satisfying. And it will build over time to create powerful characters to defeat dangerous bosses.

## Project Outcome


## Research

### Battle Style
![alt text](RealTime.png)
<br></br>
"The key characteristic of RT systems is that all, or almost all, of the gameplay takes place in real-time."

![alt text](TurnBased.png)
<br></br>
"combatants act in turns, usually one at a time. Other combatants are typically unable
to move or perform actions outside of their own turn"
<br></br>

![alt text](RTWPause.png)
<br></br>

From the evaluation made by this paper, using infomation gathered from forum posts to generate overall opinions on the strengths and weaknesses of the different battle styles. Real time seems to point towards single character, intense action and being problematic having multiple party members. Also as there is no direct control while the combat is going, having real time actions do not make sense.
Real time with pause is a possible idea, as it allows party management and tactical depth. However it also does not really gain from being real time with the features planned. 
Turn based does have some issues with it being possibly boring or tedious due to the same animations being played over and over. Also some turn based games can be predictable if there is an obivious un-changing order to the combat. With 


## UI



## Initial User feedback

### Results

Big part was UI and not knowing what the attack value was.

<iframe src="https://blueprintue.com/render/ygfjkdp-/" scrolling="yes" allowfullscreen></iframe>





![alt text](<Untitled video - Made with Clipchamp.gif>)
![alt text](image-1.png)

From the questionaire, the main consensus is selecting the item first, and then the character wanting to be equipped. 
Dragging the item is also a popular way of equipping the items, and it gives a good visual of actually 'equipping' the items. This will help with the confusion felt by the testers on, what order they need to click things and what characters are being equipped.
Having effects and visuals will help show whats going on a provide a feedback effect to the player on what they're doing. 
The super auto pet; shop and item drag mechanic, creates a clear and easy to tell way of selecting an item, and then showing the selecting of the character to add the item to. The item having clear details on what it does and how much it is. 

![alt text](image-2.png)

The clear details on what things do really makes it easier to play smoothly in Super Auto Pet's. Form the feedback, knowing what is equipped and how that is affecting the character, as well as seeing the stat values of the characters easily is something that is important.





## Implementation

### Process

Created structure diagram of the program to better see what each part did, and to easier build from it.

Adding way to see what character is selected.
When selecting a character it will now show what character has been selected.
creating a sphere to show selcected as a place holder for a better looking effect. It starts invisible and an event dispatch triggers an event in the selected hero that makes it visible, until the next selection of a hero where it sets it back to invisible.



To make it clearer i want an aura or some visual signifyier that its been selected.
Also an outline when hovering the characters to show its selectable.




Creating the map/ progression

using a data table to create bounds, with a difficulty number to use to generate enemies for levels of encounter.
I will then create a map, and populate each node with a different enemy encounter. Using a function library to read the rows, and then functions with the map actor to get those ranges and get the random numbers.
However using random numbers, to create a runtime, random in future layout, i will have to change how my previous enemy loading works as from what i could see online, data tables cannot be edited during runtime, so i cant then save my create enemies into a data table to be read easily with my current system. Apparently there are packages on the store that enable this, but im not sure how worth it would be to use this, rather than just re do it, which could probably help with readability and make it more efficient.




https://www.fab.com/listings/5c77947a-5096-438f-91fb-a28729a34b57
Possible?
https://forums.unrealengine.com/t/load-csv-data-table-in-runtime-builds/414548/4
https://blueprintue.com/blueprint/8zkq31hh/
https://forums.unrealengine.com/t/set-data-table-row/85844/7



Redoing the enemy set up, to use the created enemies rather than the set enemy data in the table. 


because i used a function library, it means as long as i handle the inputs in the same way, i can just change the function to fit with the new array, and there isnt alot of logic to change.
<iframe src="https://blueprintue.com/blueprint/fvsuyzz1/" scrolling="yes" allowfullscreen></iframe>

<iframe src="https://blueprintue.com/blueprint/7hzjewmd/" scrolling="yes" allowfullscreen></iframe>


While realising i may need to redo some parts which is fine, upon reflection on the project, I felt a bit lost on the steps i need to take to make the game better/ good, from what i currently have. I want to properly go through and break down the steps i need to take to make the parts, so i can more easily work on it.
I do have a concern that alot of the games like this, where you have roguelike progression and battles like i want, have good artstyles that make it fun or gimicky, and as i dont have the best art ability, my mechanics will not fill the gap with the current plan. 
After talking through it i realised i did not have as big an issue than i thought i did.
Also that using an array to store the enemies is a correct idea, as it works similar to a hash table being used to save a row of a large data table in a game that would need it.
And it shouldn't be that difficult to change what i have to work with an array of structs rather than the structs from a data table.


As the map will have a different camera, i will need to have it move from the main view to the map view. This will go into the menuManager, it will need to happen at the start of the game, and then back to the map view after a fight has happened.