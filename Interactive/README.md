This folder covers the Interactive segment of the course.

04/12/2022: Thus far, there has being absolutely no success with OpenGL. While I can run the template and move the Dog around in the window, that is the extent of my success. Loading in my own models caused them to become a distorted mess coloured as if the normal map was the base texture. as can be seen below.

![image](https://user-images.githubusercontent.com/50166106/205504398-82617764-65ca-4e72-aaa5-9473c8a91203.png)

Presuming this was caused by exporting every model from my scene, I instead resolved to test single models, leading to varying degrees of failure. The following is just one segment of The Tower model for example.

![image](https://user-images.githubusercontent.com/50166106/205504429-cbd6d7e8-2896-413d-b117-fb1da9eee4cd.png)

While this next one is the Sword model with the normals removed.

![image](https://user-images.githubusercontent.com/50166106/205504469-36110846-7027-4268-9866-abb18fad0cf7.png)

As a test, I imported the gltf of the dog model into blender to examine what made it so different to my own, as wlel as re-exporting it with the same settings as my tower models to see if that also distorted it, and it did not, leaving me none the wiser as to why this refuses to work. To make matters even more annoying, I attempted to get the W and S keys to work as zoom in and zoom out. Checking the update() method, shows that the W and S keys are worked by the program already.

![image](https://user-images.githubusercontent.com/50166106/205504565-dcac8326-d6d4-4d3e-9fc9-7e9da75e5272.png)

which meant the problem had to be elsewhere. Scrolling down, I found that the modelMatrix method has adjustments for both X and Y values, but not for Z, as such, I added a new line of code, 309 in the following picture.

![image](https://user-images.githubusercontent.com/50166106/205504598-8607ea87-803d-40fe-bb5c-8931114eb62b.png)

Unfortunately, this also did not work, leading to more frustrations, as I simply do not understand why this C++ code refuses to work as I expect it to from the other languages I have learned. The only success thus far was in changing the window dimensions to better match what shape my model should be if it imported correctly.

![image](https://user-images.githubusercontent.com/50166106/205504672-08b2af97-0135-4d95-b35e-16aa49ef4063.png)

But this is hardly an accomplishment as this is an incredibly simple adjustment of a variable. This is all immensely frustrating, as the model does render correctly if loaded as a GLTF into other renderers, meaning the issue lies with my inability to solve this code.
