**Jake Torres**

# October 3rd 2024, Falling into the Void 🕳️🍂🎵

As we enter fall, our Creative Embedded Sytems class was tasked to create an art display with the theme "**Fall**" using our ESP32 TTGo T-Display devices. I created "**Fall**ing into the Void", a display that evokes feeling of serenity and peace while you float away on your bed listening to music. Here is what my final display looked like!

![372914465-cff865c5-66ac-42ee-b49b-f6057763ecab](https://github.com/user-attachments/assets/4b65cb79-f968-4f3b-825e-c67a30c94945)


# The Fall
When I first heard the theme, I immediately thought of scenes from the Legend of Zelda: Tears of the Kingdom where Link, the protagonist, dives into the unknown from islands high above the lands of Hyrule. While you are falling you are able to truly witness the vastness of the kingdom of Hyrule and the regions to explore. During these times playing the game I feel excitement about all the things to do and see, but also I feel peace. The wind blowing against your face and slowly floating in the air above an unexplored world.

![giphy](https://github.com/user-attachments/assets/b0fa5ed1-78ab-445a-897c-20f44ed00feb)

Originally, I wanted to explore this idea, but I was having difficulty figuring out how to spin it in a unique way that felt substantial. Becasue of this I decided to reroute my idea and try to explore the idea of peace while falling in a different lens. I was laying on my bed listening to music trying to brainstorm ideas when the idea of what I was currently doing came to me. I thought of the peace felt from getting home from a long day or work or school and just sitting on my bed and floating away and I wanted to lean into that. 

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


