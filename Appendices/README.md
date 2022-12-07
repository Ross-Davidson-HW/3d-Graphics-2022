# CRITICAL ANALYSIS

This anaylsis covers the three areas of the project. As of now, Render and Animation are complete, and thus written about here, and in futuree coding will be appended.

## Modelling

The main thing here is that I did not know Blenders tools, and coming from Maya, had a lot of difficulty adjusting. In many aspects, having examined the tools more, there is many areas I could gretly improve my flow in future. Perhaps foremost amongst these is that I did not use the mirror tool at all, but having seen it in use, I could see that it would have been greatly useful for the creation of the sword, spear and hammer models. This alone would have made my production much faster, and likely better quality.

To form the sword and spears more ornate sections, I had to manually record multiple vector locations, figure out the distances, then adjust the vectors on the opposite side of the model to match, to keep the model consistent in dimensions. This greatly slowed down the speed of modelling as a result. While there are no doubt other areas I could greatly improve in as well, this was the greatest hindrance and area to improve I would say. On the flipside, by figuring out how to manipulate individual vectors so much made filling in hollows, such as the inside of the letters, or the gaps in the hammer, much easier, as the edges often do not extrude quite as you might expect. Lining up the XYZ of the vertices made fixing this much easier, and my method of ensuring the vertices were symetrical ensured I could do this quickly and easily.

## Animation

Overall, this was MUCH smoother than last time I worked with Unreal. Blender imported the models correctly laid out, and outside of some minor fixes such as reapplying textures, there was little broken with it. My animation this time however was much more ocmplicated, while last year it was relatively simple. I encountered a few problems with the sequencer immediately, and didn't realsie I need to place a camera cut into the sequencer itself to record form it, so even once my animation was done, I ended up wasting more time trying to find out how to get it to record the correct camera and not just the default 0,0,0 position of the scene.

Another issue I encountered was that certain keyframes would inexplicably link together, so I'd change one, and it would then change another, even if deleted and remade from scratch, whichw as immensely frustrating, and is why there is a slight judder to the camera when it climbs up the outside of the tower. The sheer number of objects I had to move also took significant time, and in hindsight, i likely could have apreneted them together to only need to adjust them as sets, instead of all individually. These mistakes cost me time, but thankfully I still managed to complete these two stages well in advance of the deadline.

## Interaction

This was easily my weakest area, fueled by both out of University issues, and my own lack of skill with the C++ language, and by extension OpenGL written in C++. This is in part my own fault for been too confident, and not allocating enough time to properly learn the material. In the latter half of the course especially, I should have put in far more effort than I did, much earlier. Unfortunately, I was unable to attend most of the labs, as the job I was forced to get due to the current cost of living crisis requires me to work Thursday afternoon/evenings overlapping with the labs time.

This is not an excuse, merely an explanation. The moment this happened, I should have reached out for help and support and I did not. While I am happy that I started to get a handle on some parts of it, I simply left it too late. I will be rectifying this over the next few months as C++ is an industry standard in many ways, and my knowledge of C# and Java will not carry me forwards.

Areas for improvement:
- C++ as a whole
- OpenGL specifically
- Time management
- GLTF trouble shooting
- Asking for help instead of bruteforcing

Should I solve these issues, I should be able to perform this task properly in future.

C++ is a much different language than I am used to, and simple pieces of syntax, such as declaring the void methods in the same way you do variables, is not something that I thought to do at first. These silly little errors greatly impeded my progress, though at least taught me what to be aware of in future. Creating my own LookAt camera and callback methods was also a help, rather than using those already included in the template.
