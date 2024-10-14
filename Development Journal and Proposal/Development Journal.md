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