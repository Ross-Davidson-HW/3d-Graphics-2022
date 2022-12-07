This folder covers the Interactive segment of the course.

04/12/2022: Thus far, there has being absolutely no success with OpenGL. While I can run the template and move the Dog around in the window, that is the extent of my success. Loading in my own models caused them to become a distorted mess coloured as if the normal map was the base texture. as can be seen below.

![image](https://user-images.githubusercontent.com/50166106/205504398-82617764-65ca-4e72-aaa5-9473c8a91203.png)

Presuming this was caused by exporting every model from my scene, I instead resolved to test single models, leading to varying degrees of failure. The following is just one segment of The Tower model for example.

![image](https://user-images.githubusercontent.com/50166106/205504429-cbd6d7e8-2896-413d-b117-fb1da9eee4cd.png)

While this next one is the Sword model with the normals removed.

![image](https://user-images.githubusercontent.com/50166106/205504469-36110846-7027-4268-9866-abb18fad0cf7.png)

As a test, I imported the gltf of the dog model into blender to examine what made it so different to my own, as well as re-exporting it with the same settings as my tower models to see if that also distorted it, and it did not, leaving me none the wiser as to why this refuses to work. 

In the end, to at least make some progress, I attempted to get the W and S keys to work. Checking the update() method, shows that the W and S keys are tracked by the program already.

![image](https://user-images.githubusercontent.com/50166106/205504565-dcac8326-d6d4-4d3e-9fc9-7e9da75e5272.png)

which meant the problem had to be elsewhere. Scrolling down, I found that the modelMatrix method has adjustments for both X and Y values, but not for Z, as such, I added a new line of code, 309 in the following picture.

![image](https://user-images.githubusercontent.com/50166106/205508033-fef61290-ac79-4117-8d25-1e8949b34577.png)

Unfortunately, this also did not work at first, leading to more frustrations, until I realised I needed to change modelRotation to modelPosition, which fixed the problem. From here, I figured out how that I can set 6 keys to adjust the camera, and 6 to rotate the model, but making use of modelPostion.x/y/z and modelRotation.x/y/z.

![image](https://user-images.githubusercontent.com/50166106/205508744-806f9f31-342f-4f2c-8b60-d5139f2f41ab.png)

![image](https://user-images.githubusercontent.com/50166106/205508758-b1b6a6da-085c-4229-b450-1b8f341a2c37.png)

Thus giving me at least some small progress.

The only other success thus far was in changing the window dimensions to better match what shape my model should be if it imported correctly.

![image](https://user-images.githubusercontent.com/50166106/205504672-08b2af97-0135-4d95-b35e-16aa49ef4063.png)

But this is hardly an accomplishment as this is an incredibly simple adjustment of a variable. This is all immensely frustrating, as the model does render correctly if loaded as a GLTF into other renderers, meaning the issue lies with my inability to solve this code.

06/12/2022: Progress has been very slow as the model bugs continue to frustrate, to the point even a basic cube was not properly displaying, with the camera seemingly inside the model at all times, no matter what I changed, making it very difficult to parse what was happening. I even rewrote the view script to try and resolve this, setting the camera to be 100f on the Z axis to move it away from the default position, yet the cube seemed to follow it. This is despite the position being set to 0, 0, 0 by default. The only difference in terms of code only occurred after this began occurring, pointing to the issue possibly been the environment, my laptop instead of my PC. As I did nto have access to my PC at this time, I have had to delay trying to fix that until later.