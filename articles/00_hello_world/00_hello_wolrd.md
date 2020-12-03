### Achievement "*Hello world!*"

[![](https://github.com/E1e5en/armory3d-blog.github.io/blob/master/articles/00_hello_world/picture/logo.jpg)](logo)

*Armory3D* is a free open source 3D game engine fully integrated with *Blender* (https://www.blender.org/). It turns out that *Blender* becomes not only a tool for creating materials for a game, but the engine editor itself (we make levels, we program, and an interface...).

**Technologies:** Utilizing Kha multimedia framework.

**Programming languages:** Haxe (https://haxe.org/), GLSL (https://ru.wikipedia.org/wiki/OpenGL_Shading_Language), visual programming (Logic Node).

**For which platforms you can make games:**
- Windows, Linux, Mac
- HTML5
- Android, iOS
- PS4, Xbox One, Switch

You can read about the Haxe language here https://haxe.org/documentation/introduction/, in general, game engines (*Kha*, *Heaps*, *OpenFL* and others) have been developed in this language and games such as *Dead Cells* have been created on them. *Northgard*, *Papers, Please* and others. It itself is similar to C#.
Visual programming (*Logic node*) also allows you to quickly get used to and understand what functions are in the tool and do something simple. Of course, creating complex algorithms using nodes is dreary, time consuming and (paradoxically) difficult, but no one bothers to use both the Haxe code and visual programming (you can create your own node with the algorithm and then use it). This is already a jungle, but I will use this particular method until I get bored, because it looks beautiful and interesting, as if you are playing a game, creating a game (such a *Human Resource Machine* and *7 Billion Humans* are obtained).

**Installation**

1. Download *Blender* (https://www.blender.org/download/). Currently version 2.83.4.
2. Download *Armory3D* (https://armory3d.org/download.html). At the moment, the latest version of *ArmorySDK-2020-8* .
3. Install *Blender*.
4. Unpack *Armory3D*.
5. Install the engine. It is installed like a regular add-on in *Blender*: select *Edit* -> *Preferences* -> *Add-ons*, find the Install button, select `armory.py` in the engine directory. As soon as *Render: Armory* appears in the list of addons, check the box next to it and restart *Blender*.
6. Done.

The link to the documentation is https://github.com/armory3d/armory/wiki.
 There are many examples (some may not work because the developers do not have time to update them) - https://github.com/armory3d/armory_examples.
Examples, materials from the lessons: https://github.com/armory3d/armory_tutorials.
Templates (templates for some types of projects) are also interesting, here is the link - https://github.com/armory3d/armory_templates.
And here is a video demonstrating templates:
1. https://www.youtube.com/watch?v=zVjk_WOdk2Q 
2. https://www.youtube.com/watch?v=b3TxkGWWpzM 
3. https://www.youtube.com/watch?v=z4TDx0qppTs 
4. https://www.youtube.com/watch?v=5b97eR5_fQI 

**Hello world**

We have everything set up and installed, now let's launch *Blender*.
At startup, there will be a standard scene (cube, light, camera). It's enough.

[![](https://github.com/E1e5en/armory3d-blog.github.io/blob/master/articles/00_hello_world/picture/1.jpg)](1)

Since the *Armory3D* engine is installed, we will see the corresponding item in almost every section of the object properties panel (*Armory Traits*, *Armory Props* and others).
Save the current scene by creating a folder "*00_hello_world*", save `00_hello_world.blend` in it. And now you can start the current scene on the engine: in the properties panel, in the *Render Properties* section, find the *Armory Player* item and press Play (or by pressing *F5*).

[![](https://github.com/E1e5en/armory3d-blog.github.io/blob/master/articles/00_hello_world/picture/2.jpg)](2)

And we see the result.

[![](https://github.com/E1e5en/armory3d-blog.github.io/blob/master/articles/00_hello_world/picture/3.jpg)](3)

Now let's make the cube rotate along one of the axis by clicking on the window. To do this, switch the bottom panel in the *Editor* Type to the *Logic Node Editor*.

[![](https://github.com/E1e5en/armory3d-blog.github.io/blob/master/articles/00_hello_world/picture/4.jpg)](4)

The visual programming editor will open. Next, let's write a script to rotate the object.

Note. As in many engines, the script is written by itself and can be attached to any object, so having written one such code for rotation, you can apply/bind it to any number of objects. In each engine, everything is individual, but for a general understanding, you need to know this.

We create a new script by clicking on the *New button*. Let's give it a name and set the *Fake User* switch so that the script is not deleted as unused (since we have not linked it yet). Add nodes (via the *Add* menu item in this panel) and link them as shown below.

[![](https://github.com/E1e5en/armory3d-blog.github.io/blob/master/articles/00_hello_world/picture/5.jpg)](5)

Nothing is specified in the *Object* field of the *Rotate Object Around Axis* node, which means that this field will refer to the object to which the script will be attached. You can, of course, specify a specific object on the scene, but if the described behavior applies only to a specific object, it is better to do so.
And in the code everything is written simply, now the user clicks the code in the window with the left mouse button, the cube will rotate along the Y axis by 0.069 radians (or 4 degrees).
Now let's bind the script to the object: select the cube, in the properties panel, select the Object properties section, in the *Armory Traits* item, click the plus, select *Nodes*, click *OK*.
Having selected an empty item in the list, select the *CubeRotation* script we created from the Tree drop-down list.

[![](https://github.com/E1e5en/armory3d-blog.github.io/blob/master/articles/00_hello_world/picture/6.jpg)](6) 

Save and run (*F5*).
Now we click anywhere in the window with the left mouse button and the cube rotates. Now let's unload this into a separate application.
On the properties panel, go to the *Render Properties* section in the *Armory Exporter* item, add the platform to the list, select `Windows (Krom)` from the drop-down list and click *Publish*.

[![](https://github.com/E1e5en/armory3d-blog.github.io/blob/master/articles/00_hello_world/picture/7.jpg)](7)  

As a result, the application will be located in the project folder in the `..\build_00_hello_world\krom-windows` directory. Can be copied and redistributed.
I'll export to HTML5 and post it here (https://e1e5en.github.io/armory3d-blog.github.io/00_hello_world/). So that you can see (having an upload to the web is cool).

**The achievement "*Hello world*" has been received**

