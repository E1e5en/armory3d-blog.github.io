### Achievement "*First Step*"

The first step is to develop simple game mechanics. As it will be a clone of an old game from phones, in which there is a ball, gravity acts on it and the player can move it left and right, while the platforms on which he stands move up. The task is not to let the ball go beyond the edges of the screen (up or down). Such an intricate undertaking.
In our hands is *Blender*, in which I throw a game from simple elements.

[![](https://github.com/E1e5en/armory3d-blog.github.io/blob/master/articles/01_first_step/picture/1.jpg)](1)

The elements are there, it remains to program them.
The walls on the left and right are ordinary rectangular parallelepipeds (we add them as child objects to the *WallsLR* object). With `Rigid Body` with *Passive* type.
Bottom and top are cones with `Rigid Bodies` of type *Passive* (add them as child objects to the *WallsTB* object).
For our main character, the ball, we add a physical body in the form of a `Rigid Body` with an object for collision in the form of a sphere.
Management is as follows:
1) the player pressed the screen (the `On Surface` event was triggered);
2) we get the coordinates where the player clicked, and take the value along the X axis from it (the `Surface Coords` and `Separator XYZ` nodes);
3) get the width of the screen (`Window Info` node) and divide by 2 to find out the middle of the screen in width;
4) we compare the obtained values, if the value is greater, then it means that the player clicked on the right side of the screen, and apply force to the ball along the X axis with a value of 0.5 (i.e., move to the right), and apply the value -0.5, if left side of the screen.

[![](https://github.com/E1e5en/armory3d-blog.github.io/blob/master/articles/01_first_step/picture/2.jpg)](2)

We also hang the second script on the main character, in which we check whether he has come into contact with the "thorns".

[![](https://github.com/E1e5en/armory3d-blog.github.io/blob/master/articles/01_first_step/picture/3.jpg)](3)

In each frame, we check who the ball collided with (we get an array of objects from the `Get Contacts` node and loop through it in the `Array Loop` node). If it touched an object whose parent is an object named *WallsTB*, it means that it touched a spike, and we switch to the game ending scene (*GameOver*).
*Blocks* that will go up are rectangular parallelepipeds. When a move event/message is received, they will move up at the expense of linear velocity.

[![](https://github.com/E1e5en/armory3d-blog.github.io/blob/master/articles/01_first_step/picture/4.jpg)](4)

The code is just as simple, when an event is received in the `On Event` node, the position is set relative to the respawn point (on the Y axis, the parent of the block will be the respawn object itself, so here not world coordinates are used, but local ones) and give acceleration with the value in the speed property. The property itself is added to the object during its initialization (the `On Init` node), as well as the check property (about which a little later).

[![](https://github.com/E1e5en/armory3d-blog.github.io/blob/master/articles/01_first_step/picture/5.jpg)](5)

The object for spawning blocks (*SpawnBlocks*) is *Arrow* (in fact, an empty object that indicates a point in 3D space). Its code consists of three parts:
1. initialization (`On Init` event) - to define a property with a block speed value;

[![](https://github.com/E1e5en/armory3d-blog.github.io/blob/master/articles/01_first_step/picture/6.jpg)](6)

2. respawn (an `On Event` node that waits for a spawn event/message) - here, by calling, a random block from the *Blocks* collection (1 of 8) is taken, cloned (the respawn object is specified as a parent), the speed value is passed to the property and the event is sent to it/move message (to start moving). Thus, there will be several blocks in the collection (in my case, 8), so there is no need to bother with the code for a random horizontal arrangement, but we will prepare them in advance (manually, so to speak);

[![](https://github.com/E1e5en/armory3d-blog.github.io/blob/master/articles/01_first_step/picture/7.jpg)](7)

3. timer (`On Timer` event) - every 1.5 seconds the speed of all blocks (created and new) will increase by 0.5.

[![](https://github.com/E1e5en/armory3d-blog.github.io/blob/master/articles/01_first_step/picture/8.jpg)](8)

There are two more additional objects in the scene:
1. trigger for respawn (*TriggerSpawn*) - as soon as the block comes into contact with it, then it sends a spawn event/message to the respawn block (to create a new one). Thus, the blocks are not created by a timer, and so it is easier to regulate their movement by changing only the speed, and the distance between them will always be the same (with the respawn timer, I had to adjust 2 values: the respawn time and the speed);

[![](https://github.com/E1e5en/armory3d-blog.github.io/blob/master/articles/01_first_step/picture/9.jpg)](9)

2. trigger for deleting unnecessary blocks (*TriggerDeleteBlock*) - as soon as a block touches it, it is removed from the scene.

[![](https://github.com/E1e5en/armory3d-blog.github.io/blob/master/articles/01_first_step/picture/10.jpg)](10)

As a result, the scene looks like this.

[![](https://github.com/E1e5en/armory3d-blog.github.io/blob/master/articles/01_first_step/picture/11.jpg)](11)

The check property for the block (*Blocks*) was added so that the respawn message is sent once, since "Physically" the block intersects with the trigger for some time and the event is executed every frame, but we need to execute only once.
You can launch this miracle in the browser using the link or put it on your Android smartphone.


**The achievement "*First Step*" has been received**

