# Potassium's DiffusionBee Macros
***[Macro and guide created by Captain K. Potassium (Potassium#0001)](https://www.youtube.com/watch?v=OS2aLrcCvbI)***  

### Software Requirements
- [DiffusionBee](https://github.com/divamgupta/diffusionbee-stable-diffusion-ui/releases) (obviously lol)
- [Keyboard Maestro](https://www.keyboardmaestro.com/)

# Quality-of-Life Update (2022-10-28)
These other macros are basically *quality-of-life* improvements to DiffusionBee. I don't know when/if the dev will implement these features, so in the meantime...    
![Thanos gif: "Fine, I'll do it myself](https://u.cubeupload.com/CaptainPotassium/thanosfineilldoitmys.gif)  
*lol*

### Keyboard Shortcuts! ✨NEW✨ 
- **⌘1** : *Open the "Text to Image" tab*
- **⌘2** : *Open the "Image to Image" tab*
- **⌘3** : *Open the "Inpainting" tab*
- **⌘4** : *Open the "Outpainting" tab*
- **⌘5** : *Open the "History" tab*
- **⌘Enter** : *Start "generating" a new image*
  - Rather than needing to click the button, now you can keep your hands on the keyboard!
  - Works in "Text to Image", "Image to Image", "Inpainting", and "Outpainting".
	- Press ⌘Enter again to stop it early.
- **⌘I** : *Open* `~/.diffusionbee` *in Finder*
  - This is where images created using DiffusionBee are stored by default.
- **⌘L** : *Open the Logs*
- **⌘N** : *Import a new image*
  - Works in "Image to Image", "Inpainting", and "Outpainting".
- **⌘⇧R** : *Start the DiffusionBee Dreaming macro*
  - Only works in the "Image to Image" tab.
  - To stop the DiffusionBee Dreaming macro, hold down the R or ESC key as an image finshes generating. 
  - The macro will halt autmatically if DiffusionBee is not the focused window when the current generation ends.
  - For more information about this macro, click [here](https://github.com/CaptainPotassium/Potassium-DB-Macro/new/main#diffusionbee-dreaming-dreaming-animation-using-dbs-img2img-tool).


## Installation / How to Update
0. Make sure you've installed both [Keyboard Maestro](https://www.keyboardmaestro.com/) and [DiffusionBee](https://github.com/divamgupta/diffusionbee-stable-diffusion-ui/releases)
1. [Download the latest macro-file.](LINK-GOES-HERE)
2. Open Keyboard Maestro, and delete your old "DiffusionBee Dreaming" Macro.
3. Double-click on [this file] to open it and import it into Keyboard Maestro. (Don't worry, the "DiffusionBee Dreaming" macro is included in this macro group).

***If you have any questions, feel free to ask them on the official [DiffusionBee Discord](https://discord.gg/Q3QP6HjG)!***

---

## DiffusionBee Dreaming macro: 'dreaming' animation using DB's Img2Img tool

You can use this macro to created undirected "dreaming" animations by repeated sending the output of Img2Img as the new input. You can get some really cool and trippy results, but it can take a while depending on how long you want your animation to be (and what you want its FPS to be).  

Here is an animation I made using this tool:

https://user-images.githubusercontent.com/26673393/198810901-231ddc61-c46e-4ebb-ad25-878e0df9c839.mp4


- This macro (as well as several of the other macros) uses on the pixel coordinates of the DiffusionBee window to click on the right buttons. [The DiffusionBee window must use exactly 50% of your main screen, and it must be on the right](https://u.cubeupload.com/CaptainPotassium/diffusionbeearrangem.png). Keyboard Maestro will resize the DB window automatically.
- Currently, the macro relies locating buttons visually. 

### Steps for using DiffusionBee Dreaming
1. **Open Keyboard Maestro**
2. **Open DiffusionBee (and ensure that it remains your focused window)**
3. **Open the "Image To Image" tab of DiffusionBee and choose your starting image.** 
	- Leave the number of images set to 1.
	- Enter your prompt.
	- *Input Strength:* For smoother, more graduation transformations, I recommend a higher input strength (like 0.7). This would be best for longer animations, IMO. If you're making a shorter animation, you're better off with a lower input strength (like 0.5). I found that input strength values lower than 0.4 resulted in too much frame-to-frame variation to create a good animation... but experimentation is encouraged!

5. **Press ⌘⇧R to start the DB-Dreaming macro.**
	- You will be prompted to enter the number of times you want to the macro to run. This is how many images it will generate if it is left running. If DiffusionBee is not kept as the focused window, the macro will stop automatically after the current image is done processing.
	- After you click "OK", the macro will start automatically regenerating images when the current image finishes processing.
	- **To stop the macro early:** you need to be holding down either R or Escape when the current image finishes processing.

***That's it! You've now made a bazillion images of whatever nonsense you asked for! lol***

### Ok, now what?
- Rather than downloading each image individually, open `~/.diffusionbee/images/` (⌘I). From there you can copy them to anywhere you want on your drive.
- I recommend FFMEG to make a .MP4 or .MOV image from the images you've generated.
	- Installation: `brew install ffmpeg`
		- click [https://brew.sh/] to install brew if you do have it.
	- To ensure that the process works properly, you should rename your images sequentially by the order they were created (they are not named sequentially by default). To easily do that: 
	- open the folder that you copied your of images to in Finder and ensure that your images are sorted by creation date.
	- select all your images and use the built-in Finder function to rename them all at once. 

	- creating an MP4: `cd PathToYourFolder; ffmpeg -framerate YourDesiredFramerate -i YourFilePrefix%05d.png -vcodec libx264 -pix_fmt yuv420p YourOutputFile.mp4`
		- example: `cd ~/Documents/db-animations/motorcycle-jesus; ffmpeg -framerate 15 -i BadassJesus%05d.png -vcodec libx264 -pix_fmt yuv420p Bad2daBone.mp4`
		- This is assuming that your files are named "YourFilePrefix00001.png", "YourFilePrefix00002.png", etc.

- If you want to make a .GIF and you have a lot of images (more than 50), use imagemagick. Keep in mind, the file size can get big quickly. If you only have a few images, [EZgif.com](https://ezgif.com/maker) works pretty well lol.

---

*Last updated on October 28, 2022*  
