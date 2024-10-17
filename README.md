**Jake Torres**

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


# The Fall
When I first heard the theme, I immediately thought of scenes from the Legend of Zelda: Tears of the Kingdom where Link, the protagonist, dives into the unknown from islands high above the lands of Hyrule. While you are falling you are able to truly witness the vastness of the kingdom of Hyrule and the regions to explore. During these times playing the game I feel excitement about all the things to do and see, but also I feel peace. The wind blowing against your face and slowly floating in the air above an unexplored world.

![giphy](https://github.com/user-attachments/assets/b0fa5ed1-78ab-445a-897c-20f44ed00feb)

Originally, I wanted to explore this idea, but I was having difficulty figuring out how to spin it in a unique way that felt substantial. Becasue of this, I decided to reroute my idea and try to explore the idea of peace while falling in a different lens. I was laying on my bed listening to music trying to brainstorm ideas when the idea of what I was currently doing came to me. I thought of the peace felt from getting home from a long day or work or school and just sitting on my bed and floating away and I wanted to lean into that. 

# Jumping In
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

# The Void
The final steps of the project was creating the envelope enclosure for ESP. Our envelopes were originally white and I thought it contrasted too much with my display and ideas so I painted it black and added some music notes to it to continue the ideas of the display onto its housing. This is what my housing looked like after I painted it!
![372923229-43b45b57-20ef-4173-a7bc-2eb4713d1a58](https://github.com/user-attachments/assets/6ff2de89-7038-4e77-8ff9-eb7a2ec2f4a1)

After painting my envelope, I connected the battery to my ESP and taped the battery and ESP into the envelope. Then I looped some yarn through the envelope and tied it to a popsicle stick so we could set up our art display. This is the timelapse of our class setting up all of our art!

![timelapse](https://github.com/user-attachments/assets/8d6f5f21-5476-442f-869e-103e9541d32b)


# The Future
This project was a awesome and fun way to start using our ESP32s and I had a lot of fun coming up with ideas for what to display. I am also glad I got to do some pixel art in Aseprite! In the future, I would love to work with a larger screen size to do something similar. The T-Display is awesome for its pixel density but working with a larger screen would definitely have given me more creative flexibility. I also think it would be interesting to research how to display my images using different methods or libraries on the screen.


