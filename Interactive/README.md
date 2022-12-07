This folder covers the Interactive segment of the course.

*04/12/2022:* Thus far, there has being absolutely no success with OpenGL. While I can run the template and move the Dog around in the window, that is the extent of my success. Loading in my own models caused them to become a distorted mess coloured as if the normal map was the base texture. as can be seen below.

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

*06/12/2022:* Progress has been very slow as the model bugs continue to frustrate, to the point even a basic cube was not properly displaying, with the camera seemingly inside the model at all times, no matter what I changed, making it very difficult to parse what was happening. I even rewrote the view script to try and resolve this, setting the camera to be 100f on the Z axis to move it away from the default position, yet the cube seemed to follow it. This is despite the position being set to 0, 0, 0 by default. The only difference in terms of code only occurred after this began occurring, pointing to the issue possibly been the environment, my laptop instead of my PC. As I did nto have access to my PC at this time, I have had to delay trying to fix that until later.

*06/12/2022 Pt2:* Switching back to the PC did indeed help fix the issue mentioned above with the camera, allowing me to once again properly test the models I was importing. Doing this revealing something interesting:

![image](https://user-images.githubusercontent.com/50166106/206089163-72e305dc-51ac-4f3b-bf8b-e2d7077a74d3.png)

At first, this just appears to be my sword model viewed at a very low angle from the tip down, but in fact is the entire model, just scrunched down very small. However, if we contrast this with the flat granite platform that sits beneath the tower in my render normally:

![image](https://user-images.githubusercontent.com/50166106/206089261-cfc1b402-1bc2-4124-9840-d50effab6370.png)

Which has turned into a cube, or in other words been stretched out, it seems to me the template is somehow setting the model to a specific size on one axis. As to why or how it does this, I am uncertain. Unfortunately, I simply lack the grounding in C++ and OpenGL, having done neither in any of my 3 years at Uni or 3 years at College, a fact I was made aware was a glaring problem today when discussing it with another member of the cohort.

Through LearnOpenGL, I figured out that the template only loads a single VBO and VAA, instead of combing them together into VBAs. While I understand this is the major issue that prevents loading of multiple objects and textures, instead overwriting the previously loaded ones, I still lack the understanding of how to fix it at this time. Nevertheless, just figuring this out is at least progress. Due to this, while studying lighting, I also realised it woudl require implementation of more VBOs, and thus outside my area of knowledge, and not feasible in the time left.

Instead of focusing on what I have failed to achieve, I instead wish to focus on what I have:

- Implemented full control of the models postion and rotation via keyboard controls
- Implemented full control of the camera through the mouse.
- Implemented the ability to zoom in and out of the model using the scrollwheel.
- Eventually found a way to correctly display a model with a texture applied.
- Implemented a LookAt Camera from scratch to try and understand how it works

Working with C++ led to a lot more time spent trying to figure out why certain things did not work. Most of this ended up quite simple, such as declaring the method as a void much like you would a variable at the top of the program, and adjusting the glfw to use my callbacks instead of the ones in the template. Once complete, my mouse callback looks like: 
![image](https://user-images.githubusercontent.com/50166106/206096857-235ea7d9-ab4f-431d-b83c-4d3c7e9d8d2f.png)

This code is largely similar to that on *LearnOpenGL*, with some minor alterations. The same can be said for the scroll callback below:
![image](https://user-images.githubusercontent.com/50166106/206096943-04b9da87-dee4-44fc-a0de-82eed636f729.png)

While I could have used the mouse and scroll callbacks already in the template, I felt it better to implement my own from scratch to help me learn how it works.

Ultimately the majority of this not working out falls on myself for not fully preparing or realising how difficult C++ is, combined with my job requiring me to work every Thursday, thus missing the labs. All I can do now is try and learn this outside course time to improve and ensure I am ready once it comes time to join the industry.
