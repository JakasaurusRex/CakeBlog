**Jake Torres**

# October 29th 2024, Animal Jam Project Showcase 🐺🐢🦏

On Thursday October 24th, our Creative Embedded Systems class got to showcase the interactive media projects we have been working on for the last couple weeks. We were tasked to create an interactive display using our ESP32s, input devices like a joystick, button and potentiometer, and Processing with an enclosure to make it like an actual device! I had a blast checking out everyones cool demos and trying to get a high score on as many games as I could! The Animal Jam showcase also went great and I was super excited to show everyone what I had been working on. Here is a video showcasing all the features of the demo recorded the night before the showcase! 

https://github.com/user-attachments/assets/1d521944-f9e4-4f81-8811-269576a1856b

## Animal Jam like the video game? ( no D: )

Like I mentioned in my project proposal, my goal was to create a fun interactive 3D model viewer where you could create silly displays using low-poly (low polygon/resolution) animals. The vision in my head for what this was going to look like was inspired by [sneepsnorp3d on YouTube](https://www.youtube.com/@sneepsnorp3d)! I love low-poly animals and had made some animal models in the past that I could use for the project. 
<img width="1483" alt="Screenshot 2024-10-09 at 11 31 20 AM" src="https://github.com/user-attachments/assets/3d8ae603-79cb-4da4-8daf-e35c0262c2a7">

These are some of SneepSnorps most recent twitter posts

![image](https://github.com/user-attachments/assets/dd6a4447-cd54-4744-9832-d80e8151b31e)

<blockquote class="twitter-tweet" data-media-max-width="560"><p lang="en" dir="ltr">low poly sandhill crane chilling and relaxing <a href="https://t.co/j9rCTf6KEs">pic.twitter.com/j9rCTf6KEs</a></p>&mdash; sneepsnorp (@sneepsnorp3d) <a href="https://twitter.com/sneepsnorp3d/status/1835731336692453858?ref_src=twsrc%5Etfw">September 16, 2024</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

My original plan was to have an animal rotating along the z-axis and doing a little dance and allow for the user to customize some features about the model viewer such as the colors of the animal, adding hats to the animals, changing the size, changing background pastel color, and the animal itself with a couple of animal options.

In the end I was only able to get 1 animal displaying, a capybara, without the dancing, but it still ended up working out awesomely as I got the rest of the features into the app! You are able to switch pastel colors for the background, capybara and a thick outline around the capybara similar to how sneepsnorps cute low poly animals are rendered. Additionally, I was able to get 4 hats, also with outlines, working in the display. Heres what the final display looked like!

https://github.com/user-attachments/assets/ed123b97-e29a-4352-bdad-b31400c29764

## Setting Up the Stage

To organize myself over the course of the project I created a Trello board, that would keep track of progress and the things I needed to work on, especially as someone who jumps around sometimes and works on different things at different points and with other class projects going on. Heres a picture of what it looked like in the middle of the project. 

![image](https://github.com/user-attachments/assets/7057b985-1c8d-4d89-99a4-95b52fd15592)

Before starting my work on the app itself, I started my work on getting my ESP32 serial writing using the input devices we were provided. I originally was struggling quite a lot with this, though, I think the issue ended up being that there was some issues with the breadboard I was given. After rewriring multiple times and moving stuff around my breadboard, I eventually did get the serial monitor to display the inputs provided by each of the devices! The circuit I designed was built off of the work that we did in class with just the addition of the potentiometer pretty much and some reshuffling of what pins each device was connected to.

![image](https://github.com/user-attachments/assets/4ac651e6-0c75-4c69-b9ee-b75580fd2b1b)

The next thing I did to set the stage for the animals was creating my enclosure. I used OnShape to create my enclosure due to the ease of use like we talked about in class. It was really easy to start learing how to use it, especially because I have used other CAD softwares before. My goal was to create an enclosure where the ESP32 and all the cabling would fit inside and there would be a slot on one side where I could plug in a cable to. I wanted to abstract the complexity away from a user and make it easy to just plug in and start using my app! Because of this, I ended up making some pretty rough estimates for how large I wanted the enclosure to be and thankfully it worked out on my first print where everything snugly fit into the enclosure (with a little bit of smushing, a lotta tape and some foam). I went to the Columbia makerspace in order to print the shell and it was super easy to get the print started. I did almost accidentally break a bunch of printers though by unrolling the shelf which had the printers and one printer fell of the shelf and landed on another printer. That was really scary.

The last thing I did to start was get the app up and running with the keyboard acting as user input. This is where most of my technical issues arose. The first technical issues that I had was figuring out how to get 3D models working in processing. Thankfully, processing has some awesome prebuilt-in functionality for displaying 3D models using OpenGL. I watched [this video by J Stephen Lee on Youtube](https://www.youtube.com/watch?v=61NvrPsrcVc&ab_channel=J.StephenLee) which was a great overview of the features avaialble for use and also [this article by Jeremy Behreandt on Medium](https://behreajj.medium.com/3d-models-in-processing-7d968a7cede5) which talks about going out of bounds of the available features and the ability to use OpenGL directly to modify 3D models, which was going to be useful later on! It was super easy to get the capybara up in the app and starting to spin! Something critical to me however, was getting the outline to work as that emphasized the art direction I was going for and would sell the cozy and cute vibes of the project. In order to recreate this however was a lot more difficult than I had anticipated. I originally created my outline in Blender, where I created my models, using some modifiers that use an emission material. Unforunately, .obj files, the only 3D model file type that processing's OpenGL stuff uses, do not support emissive materials. Because of this, I had to look to implement the outline in a different way. I ended up discovering that I could flip the normals of the model and use a technique called backface culling to make it appear as if any surface that the camera is directly looking at is invisible and all the other surfaces are visible. This created the outline affect that I wanted! If you are interested in the techniques I used and how I solved this issue, I went into depth about this in the [previous update section](#october-17th-2024-animal-jam-project-update-) and talked about the math I used! 

After solving this issue, I had a lot less technical challenges moving forward. In order to get color changing working for the capybara and its outline, I had to create image textures that would only update the faces of the body and not the eyes so that the eyes could stay black. Then I created a function which would change all of the pixels of the image texture to the new color I wanted to change the capybara/outline to and then update the texture applied to the model. This ended up working out really well and was a perfect solution to this problem. After this I worked on an animation system for switching modes, which was definitely unnecessary but a fun addition to the app. I originally wanted it to bounce in fast and bounce out, but instead I create a fading bezier animation temporarily and I would revist the mode changing animations if I had time. The last thing I worked on before involving the Arudino input was the file parsing system which is partially completed. Originally, I anticipated having multiple animals all with different hats, and I had created some extra models, but I realized that I was not going to have enough time to do all of that. Before I had realized this though, I was working on a system to read through the data directory in the processing project folder and parse through all the animals and create a new Animal class which I had created which would contain lists of all the different things needed to visualize the animal. I think this would have been really useful if I had multiple animals, but since I was just using the capybara, it was ok to hardcode all the string file paths to the models, the hats and the textures. You should check out the [Github repo and read through my code](https://github.com/JakasaurusRex/AnimalJam) if you are interested in seeing how the incomplete file parsing systen was implemented! Essentially, I would read through the directory and find a list of all of the base animal objs and add a string of that animal to a list. Then I would iterate through the list of animals, create a mapping from the string to a new Animal object using a HashMap and then fill out the details of the object depending upon the file read in the loop. It probably would have needed to be fleshed out a little more to work but it was fun thinking through how to get that to work.

Something else I worked on for the app but never used was also this sprites for the different modes. At the moment, the modes boxes just show the number corresponding to the mode, but I had created these sprites to replace them and never put them in. 
![image](https://github.com/user-attachments/assets/4f9234f8-4857-4c20-94f4-591f0d998843)

The eye corresponded to mode 0 where you would just be able to view the capybara and the mode box would disappear. The paint bucket corresponded to the background coloring. The brush corresponded to the animal coloring and the top hat corresponded to changing the hat of the animal. I think I needed to put some more time into these sprites, I spent around an hour working on them, but I wasn't super happy with how they all turned out. I really liked the bucket though! 

## Welcome to the Jam

With everything all setup it was time to put everything together. First thing I did was start soldering all the cables together so that everything was connected. I go into depth about this process in my [GitHub README](https://github.com/JakasaurusRex/AnimalJam), but I just had to make sure that the cables were not directly soldered to the ESP32 so I didn't have to desolder them for future projecs. Along the way soldering I had some pretty funny moments where I may have done a questionable job soldering.

![image](https://github.com/user-attachments/assets/063614d4-78bd-42f0-a417-fb366e2db780)

With all my cables soldered and everything still working as intended, I smushed everything into my enclosre, which was a little tight but it ended up working. Figuring out how to get support within the enclosure is something that I never figured out while working through this. I tried using foam and tape and it wasn't super well supported despite my efforts. Something that did workout, however, was the cap that I hot glued to the potentiometer to make it easier to turn. Because the potentiometer was so small it was really difficult to turn it. In order to fix that I cut up a cap of an electronic piece in the design lab and glued it to the top of the potentiometer and it fit in my enclosure making this way easier to use the potentiometer and change its values.

I used some screws to close the enclosure that fit perfectly in length. I didn't end up using the heatset inserts because the screws fit perfectly into the plastic already and it was easy to get it screwed in. This is a video showcasing what the final enclosure looked like and a picture of what the components looked like inside.

https://github.com/user-attachments/assets/aa24dc87-b02d-4697-90d2-d5dc69ed5811

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


