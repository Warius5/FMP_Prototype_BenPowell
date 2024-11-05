# Ben Powell Development Journal


### Time Keeping

>To help with time keeping for the project, i was recommended to use Trello to plan out the different sprints with parts of the game.
<br> I will still need to research into what good versions of these systems are in similiar games, as well as research how things with work or be done.




<iframe src = "https://trello.com/b/ckvr7f3T.html" frameBorder="0" width="50%" height="300"> </iframe>


> Attempting to get the trello board to embed into the markup to better show it off rather than using screen shots, however it has not seemd to work so far, even when going to different html sites. 
<br>
> After narrowing it down to the public/ private access of the board, i changed it to public and after seemingly it not working, it did and now embedds into the markdown file. I think it may have just taken a bit for the board to update to being public. (1)










Bibliography
(1)||262588213843476 (s.d.) Embed public Trello cards/boards. At: https://gist.github.com/moraDmp30/8ae9304e0c2ec149fa6ec7a4bcc6190b (Accessed  01/10/2024).






Design

I started to research different games such as autobattlers and rogue likes for system i could mimic or use.


![Super Auto Pets](SAP.png)
\SAP.png










MVP

For the minimun viable product i will need a combat system that automatically battles, but in a turn order one at a time. 
I will also need some sort of inventory system. 

Will need a base character class to create the different ones like the enemies and the player characters.

For the turn based combat i will need an initiative array to put the different characters in to determine order that the units will attack.
I will probably want to give an indication that a unit is attacking before using animations.




Set up the camera and mode settings

Created a base character to build upon.
Realised that a turn order could be difficult in how it would work.
either gather all the characters into a list and sort it by speed/ initiative. 
Or to make it avaliable to be affected during play, perhaps going through all the characters in the battle and find the current lowest in the initiative. and after the go add 20. (Make each combat 'phase' have 20 )

I got the sorting to work, and used some debug prints to figure out if it did.
It was adding an extra item in the index. Made it so that extra was at the end, and then removed it. This seemed to work but will have to look back at it.


Then i wanted to make the turn sequence. 

I put the sorting the turn order into its own event to play at the beiginning.
Then it will start the turns. 
Tried to use a for loop to go through the intiative list and trigger an attack for each one.
I tried to add a delay so that it wouldn't trigger ti all at once. But from what i can tell delays dont work very well for loops.
I might ask for advice on what to use, possibly using a state machine to go through it.
Im also getting an error.

I spoke with Assad about my issues using a for loop and he said i should look into data driven ECS to create a combat manager.

Upon having a rethink about how the combat manager.
Changed the sorting to the maangar and did it in a better way.

https://forums.unrealengine.com/t/find-actors-then-sort/445169/2

Waned to check what would happen if two of the characters had the same speeds.
Also created child classes of the basecharacter, one for the hero and one for the enemy, so that non shared functionality could be done.
Added functions on the battle manager to better organise the code and not have it all on the event graph
Created a damage calc and attack logic.
Because im using a loop to go through the turns, i cant use delays. So im figuring out how to use timers to trigger the functions instead.
Having more issue with putting delays in, so instead focusing on the damage.
The targetting and damaging was having issues, but turns out i had used the wrong lists.
Sometimes the text would not update even if the health had been taken off, and it would change the wrong one.
I move it to being a variable and it seemd to work.
To try and get the delay to work, i got the macro of the loop and copied it in, so to see if that works.
Still didnt work so using a manual go through rather than a loop might be the answer.
Still not really working, but repeating the combat event successfully continues. Will need to properly add logic to that, and have some sort of overall looping. 
Instead of using the for loop, which causes issues for delaying between the turns.
Using a button to trigger each movement, just so i can show it working. Used an event dispatcher, https://www.youtube.com/watch?v=5GYsTTcGGJo. To catch the keyboard press and then trigger the event in the battle manager.
Once ive got something going i may make more use of these.
It does go through the whole thing, now i need to make sure it doesnt do more than one thing while its 'moving' / an attack is going.
Checking whether the enemy is dead or the players are dead.
