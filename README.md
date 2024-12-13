**Jake Torres**
- [Road Trippin'](#december-11th-2024-road-trippin-%EF%B8%8F%EF%B8%8F)
- [Emergency Situations with a Spaceteam](#november-19th-2024-emergency-situations-with-a-spaceteam-)
- [Crafting Stories - Related Works Overview](#october-29th-2024-crafting-stories---related-works-overview-)
- [Animal Jam](#october-29th-2024-animal-jam-project-showcase-)
- [Falling into the Void](#october-3rd-2024-falling-into-the-void-%EF%B8%8F)

# December 11th 2024, Road Trippin' 🚘🗺️🏕️
The last two weeks I have been crafting my final project for Creative Embedded Systems! Originally, I wanted to create a Manga/EReading device using an e-ink display with capacitive touch input. After thinking about this, this was way out of scope of the project for this class, but a cool idea. My next idea was to create a interactive poster like I had mentioned in my related works section! I was inspired by Irene Posch's interactive book, and I wanted to make a accessory for my room that could also be interacted with and light up. This led me to come up with the idea for Road Trippin'!

Here is some videos of how it came out in the end!

![395319214-3114050b-bd0d-4b95-a6f5-8b75c1d5440b](https://github.com/user-attachments/assets/2a955c42-ec0c-4f29-b909-35839a9a151c)

![395319236-3c49ca83-3195-4fd0-9835-08253edf2750](https://github.com/user-attachments/assets/ae672c27-0349-44ba-bca9-bd41ce0ceb2f)

![395319267-2d4a3518-fba8-4c80-a636-13e1aa54d181](https://github.com/user-attachments/assets/515abd13-2ebf-4347-b6f0-98ef9b13c18e)



## Charting the trip 🗺️
Over the last couple of years, my friend Dylan and I have been going on road trips around the country to explore and hang out with each other, since we don't get to see each other much since we graduated high school. Our first Road Trip took us from Miami, Florida -> Nashville, Tennessee -> Chicago, Illinois -> Denver, Colorado (where we went to high school together) -> Yellowstone, Wyoming -> Seattle, Washington (where I was interning at Microsoft for the summer)! This road trip was a blast and we got to camp a couple times during it as well. We decided to do another Road Trip this year up the east coast states from Miami, Florida -> Charlotte, North Carolina -> New River Gorge, West Virginia (one of the most beauitful places I have ever been) -> Washington D.C. -> Phillidelphia, Pennsylvania -> New York City -> Boston, Massachusettes. This trip was also a blast and I wanted to commemerate these times and showcase them on my wall! Here's some pictures from the road trips for those interested!

<img width="416" alt="Screenshot 2024-12-12 at 10 57 25 AM" src="https://github.com/user-attachments/assets/9748bcf9-8fe4-4124-bdf5-355e5c6a0d17" />

<img width="462" alt="Screenshot 2024-12-12 at 10 58 34 AM" src="https://github.com/user-attachments/assets/6cef1b44-cd66-43dd-aa04-3aa0e2f4fe20" />

<img width="571" alt="Screenshot 2024-12-12 at 11 00 39 AM" src="https://github.com/user-attachments/assets/f8016844-232a-4d5e-b74d-48c8d880ae5c" />

<img width="418" alt="Screenshot 2024-12-12 at 11 02 59 AM" src="https://github.com/user-attachments/assets/62ce5c6f-6992-4a5c-b806-60142e1cc01f" />


Originally, my plan was to create a map of the country and be able to place pegs into a state to light it up. Then you would be able to connect the pegs using yarn to showcase your travels! Original feedback I got about this idea was that it was too large scope still. To alieve this issue, I reduced the amount of states to just the east coast states, which was still quite large scope but hopefully doable in the amount of time we had. Like Irene, I wanted to use conductive crafting materials to make the poster seemelessly interactive. I planned to use conductive tape and magnetic pins that would activate reed sensors to complete the circuit. It was suggested that this was also too complicated and I should look into using the touch capacitive pins on the ESP32! I ended up doing this instead as well! Originally, I wanted to have a button that would keep track of the states you activate to be able to replay it back. Unfortunately there was not enough pins on the board after I had setup the lights and capacitive touch capabilities to allow for another input device, so I had to abandon this idea.

With these pieces of feedback the vision of my project was created! I would laser cut out states on a map of the east coast states and light them up when a user places a conductive pin into a hole on the map, this would then touch a capacitive touch sensor and light up the state.

## Starting the Car 🚙

My first step in completing the project was to design the map that I would laser cut and display! For the design of the map I was inspired by wooden maps with an underglow or this map that I found on google.

![image](https://github.com/user-attachments/assets/8925dd5b-0d34-4bb7-a06f-468c95051c09)

With that in mind, I hopped into Adobe Illustrator and I started working on the map to be cut! I found a map online that I using image tracing on to turn it into a vector. Then I cleaned it up and made sure all the shapes were closed and cuttable. I seperated out the states so that each one could be cut out individually. Here is the resulting sketch that I created after a couple hours of cleaning up!

<img width="435" alt="Screenshot 2024-12-12 at 12 54 18 PM" src="https://github.com/user-attachments/assets/d3ea4d2f-b3cf-491d-9a21-6018fce353f8" />

If you are interested in how I turned this into the map check out my [Github Repo](https://github.com/JakasaurusRex/RoadTrippin) where I got into more detail about how I went from the sketch to the final map that I used! This is how the final map turned out!

<img width="411" alt="Screenshot 2024-12-12 at 1 25 41 PM" src="https://github.com/user-attachments/assets/ac567b86-dff7-442e-a5ff-6a521aab55a5" />
<img width="236" alt="Screenshot 2024-12-12 at 1 25 30 PM" src="https://github.com/user-attachments/assets/530df44d-b1dc-4ec2-8f97-b594cf74b7e5" />
<img width="183" alt="Screenshot 2024-12-12 at 1 25 35 PM" src="https://github.com/user-attachments/assets/c856e063-2e08-4221-91b4-2f96c4d309ff" />

## Filling up the tank ⛽

Next I turned my eyes to designing and setting up the circuit I would add to my laser cut map! I built off the work we had done in class and created 2 designs for circuits in Tinkercad and Fritzing. Both do not include the touch capacitance parts of the design as I could not figure out how to set that up in the apps. Here is one of the designs I came up with that would allow for the LED circuits to be activated, the other design can be found on my [github repo](https://github.com/JakasaurusRex/RoadTrippin)!  

<img width="832" alt="Screenshot 2024-12-12 at 1 32 46 PM" src="https://github.com/user-attachments/assets/20de241f-fb0e-4fc7-bcba-1ab0fc132d22" />

While setting up the circuit I encountered many problems. First I did not think about the amount of pins available on the ESP32. The ESP32 has 7 touch capacitive sensors so I had to limit the amount of states that would glow to 7. Coincidentally, there was exactly 7 additional pins that I could use for my LED circuits! Another problem I encountered while setting up the circuit was trying to find a way to keep everything low profile, while also keeping everything connected. I decided to use a pin board and plug my ESP32 into that and solder all the cables to the pin board! This gave me some flexibility in how the pins were soldered while also staying lower profile than a breadboard! This is what my pin board looked like after I had setup: 

<img width="446" alt="Screenshot 2024-12-12 at 1 39 24 PM" src="https://github.com/user-attachments/assets/9147d21e-0324-430e-8417-169f5ead9b28" />

It was a little bit of a mess at first but I later labeled all the cables and taped the related cables together to keep it organized. After soldering 14 wires, 7 for touch capacitance and 7 for the LED cicruits I tested everything out! For some reason 2 of the pins, 37 and 38, were not working. I decided I would revist this later and try to get as much of the project working as possible done first! Heres what the working touch capacitive circuits look like!

https://github.com/user-attachments/assets/08620575-165a-4ce0-ae97-ec82dad61286

With this done, I started working on the pins that I could connect to the map. The holes I had cut out were much smaller than I had originally wanted because the map was small to fit in the scope of the project. Because of this, it was hard to find pins that would fit the size of the holes. I tried laser cutting little pegs that I could stick safety pins into to plug into the holes but they ended up being really fragile and then when placing conductive tape on the edge, they would be hard to fit in the holes again and get stuck. To fix this I ended up just wrapping the conductive tape around the safety pins. I was able to read minor changes in the capacitive sensors values with the conductive taped pins which was perfect for the enclosure! 

My code can be found in the [github repo](https://github.com/JakasaurusRex/RoadTrippin) linked earlier as well! Originally, my code to allow for the capacitive touch to light up the LEDs was actually quite simple. I had just checked if the values of the touch pins are below a certain threshold value and if they are I light up the LED corresponding to that touch pin. I originally noticed the touch pins were very sensitive so I had to do some testing to find a good threshold value and I settled on 50! 

Heres what my setup looked like while I started getting ready to put it all together!

<img width="425" alt="Screenshot 2024-12-12 at 2 16 11 PM" src="https://github.com/user-attachments/assets/696a0119-e4c8-408e-ac99-a72fa19e16a6" />

## Approaching the final stop!

To finalize the poster, I tried using a lot of tape to try to get everything neatly compact in the back. I ended up having a lot of difficulty with the copper conductive tape though while setting this up. It was flimsy and sometimes just wouldn't activate which was pretty frustrating. It was rip apart really easily so it was hard to use this with my touch input.

Additionally, how I had originally approached the code was just simply checking if a user had completed the circuit with the touch pins by touching the circuit with something conductive. However, I learned while finishing the assembly that the circuit would only complete when something electrical touched the circuit, such as human skin (since our body produce electricity). In order to get around this I reapproached my coding solution. Instead of just simply checking when the circuit was complete and lighting the light then, I would turn the light on when someone touched it and turn it off when you touched it again. I added some time between these checks so that if someone took a while to release there hand from the conductive pins it would be ok. Now to ignite the lights, you need to touch the tape with a conductive pin. When the connection is made, the light will turn on. Then when you grab the pin to remove it, the light would turn off. This behavior produced the video shown below.

![395319214-3114050b-bd0d-4b95-a6f5-8b75c1d5440b](https://github.com/user-attachments/assets/2a955c42-ec0c-4f29-b909-35839a9a151c)

In the end, I was not able to get everything hooked up. It took me multiple hours to just get 1 state working and set up and there was not enough time to finish the rest of the states and keep everything nice and tidy in the back. There is a proof of concept here though, I was able to successfully light up a state with a signal gathered from touching the tape with a conductive pin, something that could be applied to the other states to get them all working! Additionally, the light from the LED is visible from the front of the map, especially in dark rooms where its super bright! 

The change to the code makes a big difference and its a lot easier to turn on and off the lights now! 

## Reflecting on the drive

Overall I had a lot of fun working on this project! It was really hard to get everything done with multiple other final projects and graduate school applications all due within this week, especially since my project was mostly hardware components which required me to use the makerspace/design center during lab hours. I think some lessons I learned is having teammates when working on projects that involve hardware is super useful. It was really difficult to test if my circuits were working while I was alone, I had to touch my pins while also holding up the multimeter to different ends of the circuits (this definitely tested the flexability of my hands). Additionally, having another person to lean on for this type of work would have been really useful whenever I got stuck. I also wish I had more time to work on this project. I really wanted to create something I had been super excited about and having to keep cutting down the vision was saddening. I think I should have originally chosen a project with a smaller scope, but getting to work on a passion project did make it fun while I was working on the project.

I would love to keep working on the project in the future and make it something super awesome! Along the way, the technical challenges I faced have allowed me to become a much better solderer, circuit designer and maker, and wood worker! The skills I gathered from the project, even if incomplete, will be really useful for my future as a creative, tinkerer, and designer! 


# November 25th 2024, Road Trippin' - Final Project Proposal 🚘🗺️🏕️

As we approach the end of the semester, our class has been tasked to start thinking about the final projects we want to do. Originally, I wanted to make a kindle like eReader using a eInk display I could use it to read Manga. After thinking more about this idea, it seemed like it might be hard to implement with the time we have remaining and also hard to handle a large eInk display with the small amount of memory available on the ESP32. Because of this I have been reflecting over the time we spent in class this semester to think of another potential project I am interested in. I eventually thought back to my related work overview about Crafting Stories by Irene Posch where I mentioned a future work could be to create an interactive poster with similar technology. A previous project I have been wanting to make was a wooden laser cut map of the country to chart my travels and road trips I have went on with my friends. Over the last 3 years I have went on country spanning road trips stopping in national parks and cities. I decided that I could combine my ideas and create an interactive map that could display road trips I have been on and have lights the light up the states I have been to. 

My idea of how the end product would look like would be a wooden map with a place in every state that you can attach a conductive magnets to to indicate you have been to that state. After doing that, the state would light up with an array of LEDs below the map. The states would have some cutout around them to glow or have some way of lighting up. 

My inspiration for the lights comes from [this video by Moonshotkidz](https://www.youtube.com/watch?v=3m_HP4Xm4Z8). In the video, the creator uses conductive tape, magnets and leds to make an interactive poster. I would like to use a similar method of interaction with my map. I could use the ESP32 as the source of energy instead of the battery used in the video. I was also inpsired by the work by Irene Posch like I previously mentioned. 
<img width="777" alt="Screenshot 2024-11-22 at 9 49 28 PM" src="https://github.com/user-attachments/assets/84ec04cb-6134-44c5-a81a-d613c89e44f1">

In the end, the map might look like this but with magnets slotting into holes on the map instead of pins. 
![image](https://github.com/user-attachments/assets/8925dd5b-0d34-4bb7-a06f-468c95051c09)

I think I can involve some extra interaction and coding by adding a button that lets you change how the lights glow and potentially feature a mode where the lights would light up in the order of attachment to tell a story of traveling around the country. I would enclose the design in multiple layers of wood with a hollow behind to leave room for the components, similar to painting frames. 

I think I would need the following parts to create this project:
- Plywood to laser cut (available in the Makerspace or at stationary stores on broadway)
- Paint (also available in the makerspace)
- [Conductive tape to set up the circuits more easily than using cables](https://www.amazon.com/Conductive-Adhesive-Shielding-Connections-Grounding/dp/B0CND2DFTN?source=ps-sl-shoppingads-lpcontext&smid=A3P43Z824VGWMI&th=1)
- Button (available in Design lab)
- LED lights (available in Design Lab - but maybe I would look into other types of LEDs)
- [Reed Switches used to connect circuit](https://www.aliexpress.us/item/3256806005788370.html?gps-id=platformRecommendH5ForSpider&pvid=a15ac806-c360-475e-a6bb-8b27ded3af59&_t=gps-id:platformRecommendH5ForSpider,pvid:a15ac806-c360-475e-a6bb-8b27ded3af59,tpp_buckets:668%232846%238114%231999&pdp_npi=4@dis!EUR!0.23!0.23!!!1.80!1.80!@2101efac17219248121376690ecc35!12000036244460111!rec!IT!!AB&gatewayAdapt=glo2usa4itemAdapt)
- [Neodymium Magnets for connecting pins to the board](https://www.harborfreight.com/10-piece-rare-earth-magnets-67488.html)

Here is the timeline I would like to complete the work by:
- December 3rd - Laser cut and painted map
- December 10th - Hooked up circuitry with LEDs with some example pins setup
- December 12th - Button to cycle between lighting modes + final documentation


# November 19th 2024, Emergency Situations with a Spaceteam 👾
This week I worked with Mila, Mori and Sushi to modify the Spaceteam game given to our creative embedded sytems class. In the original game given to us, players have to tell others tasks that appear on their screen for the other players to complete. Every player has 2 tasks that another player might need to complete. They can complete the task by pushing the respective button! Our new features include:
- Change in the layout of the screen (basically added boxes, made the text smaller, added B1 and B2 so the user knows which buttons are which, added a background photo, changed the color of some features)
- Add a multiplayer command that requires all players to press both buttons at the same time. This is indicated by a task being received in all caps! The new tasks follow the sillyness of the original game!
- Change the progress bar color to green;
- Fixed the timer and added a number timer;

Heres all of our new features in action!

![ezgif com-video-to-gif-converter](https://github.com/user-attachments/assets/2fb8312f-4c34-42a8-b380-7c3d8be5a621)

[Check out this youtube video to hear the silly spedup noise and view the video in higher quality!](https://www.youtube.com/shorts/_mIWQXVgbx4)

## Fixing up the Skeld

After playing the original game, our first thoughts were that the UI was cluttered, confusing and broken in some places. For example the timer bar was not working, so that was something we set out to fix. We also wanted to improve the text color as we thought the green was harsh against the background. Originally, we thought it would be cool to create a way to have every player have unique colored text based on their mac address. We did not end up going through with this but I think it would be a fun addition for the future! We ended up changing the color of the text to white to make it easier to read as well as evoking more of the space theme the original iOS game created. We also added some indicators to the bottom of the screen of which button is which to make it easier for new users to figure out how to play the game. 

We really wanted to recreate the space themeing that exists in the original game that got lost in the transition from iOS to EPS, probably due to the smaller screen allowing for less information to be communicated to a player. To bring back that energy, we added a space background to the game to evoke the feeling of traveling through space. Some issues we had encountered along the way while implementing this was the fact the screen doesn't referesh in the main game loop, so we could only draw this during the setup of the game or else it would cover UI elements and we also wanted the text and UI to still be visible. To make sure everything was clear, we added borders to the text boxes and highlighting on the text to help it stand out from the background. With all of these visual changes, the game feels fresh and way more aligned with the space theming!

Another feature that we wanted to add was an improved timer. We felt the visual bar of the timer was not enough information to convey to the players alone so we worked to add timer text to the corner that counted down while your task's timer was ticking. This combined with a fixed timer bar makes it more clear how long you have until your task is about to expire!

Here is a sneak of what the new UI looks like: 

<img width="364" alt="Screenshot 2024-11-18 at 9 42 46 PM" src="https://github.com/user-attachments/assets/cf58eb2c-b232-4286-a78e-1340c47e82d9">

## Emergency Meeting!

The last feature that I worked on for the team was a multiplayer task. The multiplayer task is a task that appears 1/10 times and requires all other players to press both buttons at the same time in order to be completed. This was a pretty technically challenging feature to implement. The first step to making this new feature was adding a new set of tasks. To indicate that a task given to you was a multiplayer task, I made the new tasks in all capital letters, to indicate the urgency of the task and make it feel like it was an emergency. I also added some Among Us references to the tasks to remind players of another space themed game with emergency situations! I created the same amount of possible tasks as the original game had so that I could use the same code to generate a random multiplayer task.

<img width="1201" alt="Screenshot 2024-11-18 at 9 25 18 PM" src="https://github.com/user-attachments/assets/457656db-c121-4bd2-ad1c-86db614766a6">

After doing this, I modified the receive callback function to support the functionality of 2 new commands, M for multi followed by the multiplayer command and C for compelte. When a host received and took a task using the M command, it would start a timer, like normal tasks did and also reset variables used for multiplayer commands. The M command is sent by another ESP when they are sending a command. There is a 1/10 chance that the command sent will be a multiplayer task instead of one of the 2 tasks present on the display. If the command sent will be a multiplayer task, the task is generated and an M command is sent containing the new task. 

After a host has started a multiplayer task, it will receive C commands from other players. C commands are sent when a player has pressed 2 of their buttons at the same time. After the C command is sent to the host of the multiplayer task, the host then adds the players mac address to a list. Once the host has received a repsonse from ever mac address it has heard from while playing the game, it will complete the multiplayer task.

To identify and store different mac addresses I used an array of 100 uint8_t. This means there can only be up to 100 players playing with this feature at a time, but I didn't think that was going to be a case we were going to have to handle. The uint8_t that I am storing is the 4th uint8_t of the mac address. I found online that the last 3 ints of the mac address are the device specific parts of the address while the first 3 are manufactorer specific. In order to try make sure that no players would have the same key for a mac address I used a int from the device specific part of the mac address. I beleive there is a very small chance that the players will have the same key as there are 2^8 possible values. If this does turn out to be an issue, a solution could be to add all of the uints of the mac address and use that as the key, which would have an even smaller chance of an overlap occuring. In order to read more about my implementation, [check out our github repo](https://github.com/JakasaurusRex/arduinospaceteam)! 

## Crewmate Victory

In the end, this feature ended up working and being super fun to play with. It requires the game to pause and every to focus on sending over the 2 button input! All of our features combined act as a nice overhaul of the original ESP32 spaceteam port and greatly improve the players experience, which is what we were hoping to accomplish! I had fun working with everyone as a *Spaceteam* 😎!!

# October 29th 2024, Crafting Stories - Related Works Overview 📚🔨⚡

Today I had the chace to explore the world of creative works that utilize embedded systems to acheive their artistic visions, specifically with a story book in Crafted Stories. Crafted Stories is a project by a Slovenian researcher at the University of Art and Design in Linz, Austria, Irene Posch. Irene project seeks to explore books as a medium for using "ubiquitous, smart, electronic, and computational technologies" (quoted from [her paper](https://dl.acm.org/doi/pdf/10.1145/3430524.3446076)). The goal of the Crafting Stories project was to create an interactive story telling experience where readers will be able to experience a crafted story through different sense such as touch, hearing and sight. 

![image](https://github.com/user-attachments/assets/3994fbee-99c2-4351-8cea-3ce4afe3c5ea)


The idea for the project originates from Irene's grandma, who made a textile book for her when she was a child. The book was crafted to be interacted with using buttons, clips and snaps to rearrange, move, or change elemnets of the pages bringing the stories to life. Irene revisited this book years later from a new perspective as a researcher looking to bridge humans interactions with computing devices. She used smart and interactive textiles in order to recreate her grandmothers book using interactive technology to bring even more life into the book. She wanted to create the book "her grandma would have made" if she had access to modern technology and smart electronic textiles.

## Crafting the Crafted Stories

The book itself was created using cardboard and light blue fabric layed on top of it and the movable elements are crochetted. On the spine of the book is an [Arduino Nano controller](https://store.arduino.cc/products/arduino-nano?srsltid=AfmBOop8xO9Ha9rjVWdpz6pkWOByjKyqc0p84GKbER_rzWt2RncV-Zth) which handles all the input and output processing of the device. The Arduino connects to the differnet pages using textile cables ([probably something like these, but smaller and not braided](https://juheko.com/shop/en/textile-cable)) so that the book can be flexbile and the users would not have to worry about breaking electronic components inside of it. It seems like all the indvidual pages from there using their own circuits to handle the interaction. For example the first page of the book features a Christmas tree with attachablable candles and a star in a pouch. The candles can be attached to the tree by metal conducting snaps and the star is crochetted using silverized copper thread. When the star is placed on the page with the candles on the tree, it completes the circuit due to coppers coductive properties of the star which turns on the LED lights on each of the candles. The circuit connecting each of the lights is probably ran underneath the light blue fabric on the cardboard layer when is then connected to the Arduino. Another example is the page featuring a cat. The hair on the cat is a rya knot weave using wool and stainless steel. This allows the fur to double as a cozy interactive element and a pressure sensitive sensor that lets the cat vibrate as you pet it and purrs. 

![image](https://github.com/user-attachments/assets/cdcf9709-5ab3-4966-95e7-0bd3d8328686)


Throughout the book, Irene also used different types of paints such as Thermochromatic paints that change the color of objects when exposed to different conditions such as heat or UV light. For exmaple one  of the pages features a kid sitting on a sled with a white background. When exposed to the sun, the white background becomes blue and the picture is more clear of a kid sitting on a snow slope sledding down.

![image](https://github.com/user-attachments/assets/3fd838bd-7371-4aec-b982-56e548c2c37a)


The book is powered using a lipo battery and features a cable that rolls out of the spine of the book. 

![image](https://github.com/user-attachments/assets/fa724041-ff7e-41d9-a36f-b1813ef6595f)


## Wool Wonders

This project is so awesome and exciting. Creating interactive handmade stories is such a creative application of the technology used in the book. Especially the use of conductive elements throughout the book that double as interactive and part of the electronic design! Crafted Stories also seems like a great way for teaching children as interaction is one of the key methods of education. I wish the video included some more videos of children interacting with the book as that was one of the most interesting parts for me - seeing how other people interact with this technology without knowing of its existence. 

![image](https://github.com/user-attachments/assets/5ce07666-e00a-4a59-91b7-44ed27c50f61)


I think this technology has so much use in creative applications! I think the use of a book as a medium limits the space and interactive capabilities of the technology (I think the book was a great exploration and usecase though!!), so my first ideas for how this could be used is with room decore since its a lot larger scale. A lot of room decore is kind of static, such as posters and displays hung on the wall. Using this technology and hand crafting decorations for a childs room would be a really cute application of this. For example, maybe a nightlight in the room can be built into a poster that requires someone to move one crochetted element from one place to another and this could possibly provide a learning opportunity if the poster has a story of some sort on it. 

# October 29th 2024, Animal Jam Project Showcase 🐺🐢🦏

On Thursday October 24th, our Creative Embedded Systems class got to showcase the interactive media projects we have been working on for the last couple weeks. We were tasked to create an interactive display using our ESP32s, input devices like a joystick, button and potentiometer, and Processing with an enclosure to make it like an actual device! I had a blast checking out everyones cool demos and trying to get a high score on as many games as I could! The Animal Jam showcase also went great and I was super excited to show everyone what I had been working on. Here is a video showcasing all the features of the demo recorded the night before the showcase! 

<video width="640" height="480" controls loop=" " muted = " " autoplay="">
  <source src="https://github.com/user-attachments/assets/1d521944-f9e4-4f81-8811-269576a1856b">
</video>


## Animal Jam like the video game? ( no D: )

Like I mentioned in my project proposal, my goal was to create a fun interactive 3D model viewer where you could create silly displays using low-poly (low polygon/resolution) animals. The vision in my head for what this was going to look like was inspired by [sneepsnorp3d on YouTube](https://www.youtube.com/@sneepsnorp3d)! I love low-poly animals and had made some animal models in the past that I could use for the project. 

<img width="1483" alt="Screenshot 2024-10-09 at 11 31 20 AM" src="https://github.com/user-attachments/assets/3d8ae603-79cb-4da4-8daf-e35c0262c2a7">

These are some of SneepSnorps most recent twitter posts

![image](https://github.com/user-attachments/assets/dd6a4447-cd54-4744-9832-d80e8151b31e)

<blockquote class="twitter-tweet" data-media-max-width="560"><p lang="en" dir="ltr">low poly sandhill crane chilling and relaxing <a href="https://t.co/j9rCTf6KEs">pic.twitter.com/j9rCTf6KEs</a></p>&mdash; sneepsnorp (@sneepsnorp3d) <a href="https://twitter.com/sneepsnorp3d/status/1835731336692453858?ref_src=twsrc%5Etfw">September 16, 2024</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

My original plan was to have an animal rotating along the z-axis and doing a little dance and allow for the user to customize some features about the model viewer such as the colors of the animal, adding hats to the animals, changing the size, changing background pastel color, and the animal itself with a couple of animal options.

In the end I was only able to get 1 animal displaying, a capybara, without the dancing, but it still ended up working out awesomely as I got the rest of the features into the app! You are able to switch pastel colors for the background, capybara and a thick outline around the capybara similar to how sneepsnorps cute low poly animals are rendered. Additionally, I was able to get 4 hats, also with outlines, working in the display. Heres what the final display looked like!

<video width="640" height="480" controls loop=" " muted = " " autoplay="">
  <source src="https://github.com/user-attachments/assets/ed123b97-e29a-4352-bdad-b31400c29764">
</video>

## Setting Up the Stage

To organize myself over the course of the project I created a Trello board, that would keep track of progress and the things I needed to work on, especially as someone who jumps around sometimes and works on different things at different points and with other class projects going on. Heres a picture of what it looked like in the middle of the project. 

![image](https://github.com/user-attachments/assets/7057b985-1c8d-4d89-99a4-95b52fd15592)

Before starting my work on the app itself, I started my work on getting my ESP32 serial writing using the input devices we were provided. I originally was struggling quite a lot with this, though, I think the issue ended up being that there was some issues with the breadboard I was given. After rewriring multiple times and moving stuff around my breadboard, I eventually did get the serial monitor to display the inputs provided by each of the devices! The circuit I designed was built off of the work that we did in class with just the addition of the potentiometer pretty much and some reshuffling of what pins each device was connected to.

![image](https://github.com/user-attachments/assets/4ac651e6-0c75-4c69-b9ee-b75580fd2b1b)

The next thing I did to set the stage for the animals was creating my enclosure. I used OnShape to create my enclosure due to the ease of use like we talked about in class. It was really easy to start learing how to use it, especially because I have used other CAD softwares before. My goal was to create an enclosure where the ESP32 and all the cabling would fit inside and there would be a slot on one side where I could plug in a cable to. I wanted to abstract the complexity away from a user and make it easy to just plug in and start using my app! Because of this, I ended up making some pretty rough estimates for how large I wanted the enclosure to be and thankfully it worked out on my first print where everything snugly fit into the enclosure (with a little bit of smushing, a lotta tape and some foam). I went to the Columbia makerspace in order to print the shell and it was super easy to get the print started. I did almost accidentally break a bunch of printers though by unrolling the shelf which had the printers and one printer fell of the shelf and landed on another printer. That was really scary.

The last thing I did to start was get the app up and running with the keyboard acting as user input. This is where most of my technical issues arose. The first technical issues that I had was figuring out how to get 3D models working in processing. Thankfully, processing has some awesome prebuilt-in functionality for displaying 3D models using OpenGL. I watched [this video by J Stephen Lee on Youtube](https://www.youtube.com/watch?v=61NvrPsrcVc&ab_channel=J.StephenLee) which was a great overview of the features avaialble for use and also [this article by Jeremy Behreandt on Medium](https://behreajj.medium.com/3d-models-in-processing-7d968a7cede5) which talks about going out of bounds of the available features and the ability to use OpenGL directly to modify 3D models, which was going to be useful later on! It was super easy to get the capybara up in the app and starting to spin! 

Something critical to me however, was getting the outline to work as that emphasized the art direction I was going for and would sell the cozy and cute vibes of the project. In order to recreate this however was a lot more difficult than I had anticipated. I originally created my outline in Blender, where I created my models, using some modifiers that use an emission material. Unforunately, .obj files, the only 3D model file type that processing's OpenGL stuff uses, do not support emissive materials. Because of this, I had to look to implement the outline in a different way. I ended up discovering that I could flip the normals of the model and use a technique called backface culling to make it appear as if any surface that the camera is directly looking at is invisible and all the other surfaces are visible. This created the outline affect that I wanted! If you are interested in the techniques I used and how I solved this issue, I went into depth about this in the [previous update section](#october-17th-2024-animal-jam-project-update-) and talked about the math I used! 

After solving this issue, I had a lot less technical challenges moving forward. In order to get color changing working for the capybara and its outline, I had to create image textures that would only update the faces of the body and not the eyes so that the eyes could stay black. Then I created a function which would change all of the pixels of the image texture to the new color I wanted to change the capybara/outline to and then update the texture applied to the model. This ended up working out really well and was a perfect solution to this problem. After this I worked on an animation system for switching modes, which was definitely unnecessary but a fun addition to the app. I originally wanted it to bounce in fast and bounce out, but instead I create a fading bezier animation temporarily and I would revist the mode changing animations if I had time. 

The last thing I worked on before involving the Arudino input was the file parsing system which is partially completed. Originally, I anticipated having multiple animals all with different hats, and I had created some extra models, but I realized that I was not going to have enough time to do all of that. Before I had realized this though, I was working on a system to read through the data directory in the processing project folder and parse through all the animals and create a new Animal class which I had created which would contain lists of all the different things needed to visualize the animal. I think this would have been really useful if I had multiple animals, but since I was just using the capybara, it was ok to hardcode all the string file paths to the models, the hats and the textures. You should check out the [Github repo and read through my code](https://github.com/JakasaurusRex/AnimalJam) if you are interested in seeing how the incomplete file parsing systen was implemented! Essentially, I would read through the directory and find a list of all of the base animal objs and add a string of that animal to a list. Then I would iterate through the list of animals, create a mapping from the string to a new Animal object using a HashMap and then fill out the details of the object depending upon the file read in the loop. It probably would have needed to be fleshed out a little more to work but it was fun thinking through how to get that to work.

Something else I worked on for the app but never used was also this sprites for the different modes. At the moment, the modes boxes just show the number corresponding to the mode, but I had created these sprites to replace them and never put them in. 
![image](https://github.com/user-attachments/assets/4f9234f8-4857-4c20-94f4-591f0d998843)

The eye corresponded to mode 0 where you would just be able to view the capybara and the mode box would disappear. The paint bucket corresponded to the background coloring. The brush corresponded to the animal coloring and the top hat corresponded to changing the hat of the animal. I think I needed to put some more time into these sprites, I spent around an hour working on them, but I wasn't super happy with how they all turned out. I really liked the bucket though! 

## Welcome to the Jam

With everything all setup it was time to put everything together. First thing I did was start soldering all the cables together so that everything was connected. I go into depth about this process in my [GitHub README](https://github.com/JakasaurusRex/AnimalJam), but I just had to make sure that the cables were not directly soldered to the ESP32 so I didn't have to desolder them for future projecs. Along the way soldering I had some pretty funny moments where I may have done a questionable job soldering.

![image](https://github.com/user-attachments/assets/063614d4-78bd-42f0-a417-fb366e2db780)

With all my cables soldered and everything still working as intended, I smushed everything into my enclosre, which was a little tight but it ended up working. Figuring out how to get support within the enclosure is something that I never figured out while working through this. I tried using foam and tape and it wasn't super well supported despite my efforts. Something that did workout, however, was the cap that I hot glued to the potentiometer to make it easier to turn. Because the potentiometer was so small it was really difficult to turn it. In order to fix that I cut up a cap of an electronic piece in the design lab and glued it to the top of the potentiometer and it fit in my enclosure making this way easier to use the potentiometer and change its values.

I used some screws to close the enclosure that fit perfectly in length. I didn't end up using the heatset inserts because the screws fit perfectly into the plastic already and it was easy to get it screwed in. This is a video showcasing what the final enclosure looked like and a picture of what the components looked like inside.

<video width="640" height="480" controls loop=" " muted = " " autoplay="">
  <source src="https://github.com/user-attachments/assets/16f884c1-a71e-414c-9d7c-ab34a122121c">
</video>

![image](https://github.com/user-attachments/assets/f0de667c-1e11-4075-8d9d-42b87b3a7ee8)

I didn't really have that much time but I had also wanted to paint the enclosure to be a pastel blue or pink. I think this process and drying would have taken longer than I had wanted and I actually kinda liked the gray so I ended up not doing that, but I did sand the bottom and edges to make it more smooth! 

To get input with the ESP32 working with the app was super easy and only a couple of lines of code changes. I used the button to switch modes, the joystick to switch between options at that mode and the potentiometer to adjust the rotation of the capybara manually. These controls felt the most natural to me after using the app for a while but another consideration was making the potentiometer control how fast the object was spinning. One thing I did have to do was make it so the joystick input only registered if you fully moved it to its edge and also I had a timer that would wait a tenth of a second between inputs so that it didn't receive too many inputs at a time and scroll through the whole list of options which you were just trying to input one movement.

With all of that, the demo was complete and I got to showcase the Animal Jam in class! 

## Future Jamming

In the future, I would love to add more animals to this project. I think first I would try to finish the parsing system I was working on and then I would try to fix all the other incomplete features before I moved on to adding animals. Additionally I would wanna improve the enclosure design slightly to support all of the input devices better. Lastly I would love to get animations working but that seems like that would be super involved since obj files do not support aniamtion. 

# October 17th 2024, Animal Jam Project Update 🐸🐳🦈

Over the last week I have been hard at work at making my silly project Animal Jam. I had set 4 main tasks to accomplish over the course of the project: design and setup the circuit, setup communication between the breadboard, esp and processing, find out how to create my display in processing, and program the model viewer for customizability. Another goal that I forgot to set for myself is to spend some time in the makerspace designing my housing. 

This week, I have finished my circuit design, setup my processing project and came up with an idea of what I want the housing to look like! The circuit will be pretty simple since I will probably only be using the joystick and button. I am going to spend some time this weekend trying to figure out how I can involve the potentiometer as well though. I used fritzing to create a circuit diagram pretty similar to the one we used in class for the lab but just without the led lights. 

<img width="572" alt="Screenshot 2024-10-16 at 3 26 24 PM" src="https://github.com/user-attachments/assets/63149c07-f0a6-4531-8e44-3dd20f76b965">


I also tackled probably the most technically challenging portion of this project which was writing up the code for displaying my 3D models. I already had a capybara I had made a couple of months ago and I brought it into processing. Displaying 3D models was super easy and fast. Processing has a built in OpenGL library that it can use to display 3D models. The difficult part that I had was creating the outline for the model. I think I was too committed to trying to create the outline, but without it the colors felt flat and bland since there was no lighting in processing. Originally, I had created an outline shader for my model in Blender. The outline was not displaying when I brought it in and realized it is because .obj files, the file format used by processing, do not support a ton of features like the ones I was using to create the outline. Then, I went on a multi hour journey through documentation wormholes, endless of stackoverflow pages, dozens of youtube videos, and too many chat gpt questions until I realized that I was insanely overcomplicating the feature. I had been trying to find a way to use a OpenGL override to try to create my own shader in processing, which wasn't working and was confusing since processing a bunch of built in featueres already but I was trying to override those. Here is a picture that of a state I was trying to debug. 

![image](https://github.com/user-attachments/assets/9b557641-9bf0-4c9a-9f75-9c0ca4f7342e)

What I actually ended up doing was quite a nice solution. First, I created a second model that was slightly sized up, with inverted normals, (this means that the surfaces of the model has normals pointing in the opposite directions) and a slightly darker color. This is a model with inverted and regular normals.

![image](https://github.com/user-attachments/assets/98a14b15-c226-4183-b946-a3446b8b745f)

Then I brought that larger model into processing and did a minor OpenGL override that allowed me to turn on Back Face Culling. This meant that normals that were in the same direction as the camera. Here is a picture to help explain what backface culling does.

![image](https://github.com/user-attachments/assets/968f2a83-638c-4aeb-9342-875139d3c1e5)


Normally, this would hide the back of a model, but since I inverted the normals, it hid the front of the model. Then I displayed the normal model on top of that which results in a nice outline shader. Here are the final results!

![capyspin](https://github.com/user-attachments/assets/93c220ec-f7ab-4a48-af25-32782039e891)

I am super happy with how this turned out! I did spend many hours on this but it was a learning experience for sure! If you would like to see how this stuff works check out my [github repo](https://github.com/JakasaurusRex/AnimalJam)! With this done and my serial communication setup from Lab 2, I can start working on moving the model using the joystick! 

As for the housing, I would like to enclose all of my components in a case with just the interactive parts visible on the top. I would also like to cut out a hole for the USB C port of the ESP so that it can be easily connected to a computer. I am planning on 3D printing the enclosure and painting it a pastel blue to match the original concept! I would also like to add little pictures of all the animals I end up including around the box for decoration. I have not finished the design on OnShape yet but I am going to do that next probably! 

Also as a last goodie, here are some silly hats that I have available!

Croc Capy

![image](https://github.com/user-attachments/assets/a599da5a-05e4-4282-b78d-12f6b7b0677f)

Holy Capy

![image](https://github.com/user-attachments/assets/8e74a126-7638-477f-81e1-2f932d5f3bb6)

Ice Cream Capy

![image](https://github.com/user-attachments/assets/60cf3919-bc8d-4228-b3f9-a142aefb63fd)

Propeller Capy

![image](https://github.com/user-attachments/assets/9f0ec164-7764-40a1-9f59-51c29abc3201)

Cough Conscious Capy

![image](https://github.com/user-attachments/assets/c8a024fb-5320-4956-b294-10a0159f6582)




# October 10th 2024, Animal Jam Project Proposal 🐠🐻🐒

With our project introducing us to ESP's complete, I wanted to try to make a silly and more fun and interactive demo for our next project. The past couple of days I have been thinking about how I wanted to approach that and was in the middle of thinking about it when I was messaging the new Game Development Intiative committee I organized for Esports x Game Dev club. Another student asked to see some of my previous work involving the use of silly 3D models that I make sometimes and I shared them [my itch.io page](https://jakasaurus.itch.io/). Because of this 3D models have been in my mind and I suddenly had the idea of making an interactive 3D model viewer! 

The vision in my head for what this would look like is inspired by [sneepsnorp3d on YouTube](https://www.youtube.com/@sneepsnorp3d)! I love the cute lowpoly 3D models and I have some existing models I have made that look similar. I would like to have an animal rotating along the z-axis and doing a little dance and allow for the user to customize some features about the model viewer such as the colors of the animal, adding hats to the animals, changing the size, changing background pastel color, and the animal itself with a couple of animal options.
<img width="1483" alt="Screenshot 2024-10-09 at 11 31 20 AM" src="https://github.com/user-attachments/assets/3d8ae603-79cb-4da4-8daf-e35c0262c2a7">

For the user interactivity, I think the button will be used to be able to switch between different interaction modes and the joystick + potentiometer can be used for the actual interaction like scaling using input from the potentiometer and color changing using the inputs from the joystick. 

As for the housing containing my ESP, I can laser cut a housing in the makerspace, sand it down and paint it a pastel color to match the vibes of the app on the computer. 

In order to create this vision I will need to do the following steps.

1. Desgin and Setup my circuit on a breadboard. Setting up the circuit will involve making sure all the connectins are solid and I am able to get user input from all of the devices.
2. Setup Serial Reading and Writing to allow for interprocess communication between processing, Arduino IDE, and the ESP.
3. Research how to display 3D models using processing and setup a basic demo using one of my existing 3D models - like my Capybara which already has a bunch of hats I made for it.
4. Program the model viewer on my computer to completion after I have a working demo setup! Create more 3D Models and try to make it as fun as possible!

I am calling the project Animal Jam because its going to be a jam of all the animals dancing and having fun and you can join them in their jamming! 

# October 3rd 2024, Falling into the Void 🕳️🍂🎵

As we enter fall, our Creative Embedded Sytems class was tasked to create an art display with the theme "**Fall**" using our ESP32 TTGo T-Display devices. I created "**Fall**ing into the Void", a display that evokes feeling of serenity and peace while you float away on your bed listening to music. Here is what my final display looked like!

![372914465-cff865c5-66ac-42ee-b49b-f6057763ecab](https://github.com/user-attachments/assets/4b65cb79-f968-4f3b-825e-c67a30c94945)


## The Fall
When I first heard the theme, I immediately thought of scenes from the Legend of Zelda: Tears of the Kingdom where Link, the protagonist, dives into the unknown from islands high above the lands of Hyrule. While you are falling you are able to truly witness the vastness of the kingdom of Hyrule and the regions to explore. During these times playing the game I feel excitement about all the things to do and see, but also I feel peace. The wind blowing against your face and slowly floating in the air above an unexplored world.

![giphy](https://github.com/user-attachments/assets/b0fa5ed1-78ab-445a-897c-20f44ed00feb)

Originally, I wanted to explore this idea, but I was having difficulty figuring out how to spin it in a unique way that felt substantial. Becasue of this, I decided to reroute my idea and try to explore the idea of peace while falling in a different lens. I was laying on my bed listening to music trying to brainstorm ideas when the idea of what I was currently doing came to me. I thought of the peace felt from getting home from a long day or work or school and just sitting on my bed and floating away and I wanted to lean into that. 

## Jumping In
I knew that I wanted to use pixel art in someway so I started my work by designing the character that would be floating in the void. I wanted the character to be wearing headphones and listening to music. I chose a color pallete in Lospec, a pixel art community website, that matched the vibes of this feeling in my head. I chose a palette with lots of warmer blues and some yellows and oranges so that I could make things that standout against a black background, which was my idea at the time for where the character would be floating. 

I then started my work in Aseprite, my preferred pixel art editor, and came up with a couple of designs but these are the finals ones that I came up with for the character that would be floating and the music notes that would accompany them. 

<img width="368" alt="Screenshot 2024-10-02 at 3 50 01 PM" src="https://github.com/user-attachments/assets/52484aab-7e75-45b3-94cf-5fa7d8ec5e42">

When creating the character I wanted them to look comfy while also looking somewhat curious of their surroundings. I used art from the [Celeste official sountrack](https://www.youtube.com/watch?v=vZEObeV7bYc) as one of my inspirations and also this pixel art by user [@Lovethefox on PixilArt](https://www.pixilart.com/art/falling-into-the-void-848b278152eaa13) 

![image](https://github.com/user-attachments/assets/e08d7231-9603-46ca-a6d6-49d7d3c98e48)
![image](https://github.com/user-attachments/assets/393fd9cb-78d7-46c4-bfe7-6af176dee6d8)

After creating my artwork to use for the display I started thinking about how I wanted to create the vision in my head. I initially though of the person slowly moving around the screen while the notes would flash on the screen to indicate music is playing. In order to implement this, I used the [TFT_eSPI](https://github.com/Bodmer/TFT_eSPI) library to display my images as sprites on the screen and I moved the x and y position of the person sprite in the loop function and inverted the velocity when the person hit the edge of the screen. In order to flash the notes on the screen I randomly select the amount of time until the note will flash on the screen and I wait until that amount of time has passed using the ```millis()``` function. 

At this point, I thought the display was interesting but not as visually interesting as I would have liked. Additionally, it didn't really embody the feeling that I wanted to recreate. I though that adding rotation to the character would be a good first step to fixing the problem and could help give me more ideas. Upon implementing rotating the sprite I accidentally added the rotated sprite onto the original sprite, which caused a multiplicative afterimage effect rotating around the main person. This ended up looking super interesting and I took a bug in my code and made it part of my design! The spinning around the character gave me the feeling of floating off while not actually moving that I wanted to go for. 

Here is my final design on my display!

![IMG_8481](https://github.com/user-attachments/assets/b14ca1e1-8e7c-444a-a8df-fdc6b3ab47ff)

If you would like to see the code check out my [Github Repo](https://github.com/JakasaurusRex/FallingInTheVoidESP32)!

## The Void
The final steps of the project was creating the envelope enclosure for ESP. Our envelopes were originally white and I thought it contrasted too much with my display and ideas so I painted it black and added some music notes to it to continue the ideas of the display onto its housing. This is what my housing looked like after I painted it!
![372923229-43b45b57-20ef-4173-a7bc-2eb4713d1a58](https://github.com/user-attachments/assets/6ff2de89-7038-4e77-8ff9-eb7a2ec2f4a1)

After painting my envelope, I connected the battery to my ESP and taped the battery and ESP into the envelope. Then I looped some yarn through the envelope and tied it to a popsicle stick so we could set up our art display. This is the timelapse of our class setting up all of our art!

![timelapse](https://github.com/user-attachments/assets/8d6f5f21-5476-442f-869e-103e9541d32b)


## The Future
This project was a awesome and fun way to start using our ESP32s and I had a lot of fun coming up with ideas for what to display. I am also glad I got to do some pixel art in Aseprite! In the future, I would love to work with a larger screen size to do something similar. The T-Display is awesome for its pixel density but working with a larger screen would definitely have given me more creative flexibility. I also think it would be interesting to research how to display my images using different methods or libraries on the screen.


