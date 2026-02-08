# Entry 3
##### 2/8/2026
## context
For this year-long project, I decided to use Godot as my tool. Godot is a game engine where you can make 2D or 3D games. After doing my learning logs, I decided to stay with Godot as my tool. For Godot, I planned to create a racing game and collaborate with Bryan. We been talking to each other outside of school and talk to each other in school about what we have done. For now, I have done many learning logs and learned many new things about how this tool is used and how to make our freedom project from it. Below you can see what I learned so far. 

##### What I have done


Screenshot_8-2-2026_182622_docs.google.com.jpeg
Screenshot_8-2-2026_18268_docs.google.com.jpeg
Screenshot_8-2-2026_18263_docs.google.com.jpeg
Screenshot_8-2-2026_182558_docs.google.com.jpeg
Screenshot_8-2-2026_182551_docs.google.com.jpeg
Screenshot_8-2-2026_182539_docs.google.com.jpeg
Screenshot_8-2-2026_182534_docs.google.com.jpeg
Screenshot_8-2-2026_182720_docs.google.com.jpeg
````` js
extends Sprite2D

var speed = 400
var angular_speed = PI


func _process(delta):
	var direction = 0
	if Input.is_action_pressed("ui_left"):
		direction = -1
	if Input.is_action_pressed("ui_right"):
		direction = 1

	rotation += angular_speed * direction * delta

	var velocity = Vector2.ZERO
	if Input.is_action_pressed("ui_up"):
		velocity = Vector2.UP.rotated(rotation) * speed

	position += velocity * delta

`````

## Sources 
So one of the sources I used was the Learning Logs. [learning log.md](../tool/learning-log.md). This is where I compile everything I've learned and explain what I've done, which is updated weekly. Second, I used many videos like [Godot video](https://www.bing.com/videos/riverview/relatedvideo?&q=godot&&mid=06E46AEA6253FB5EBB5F06E46AEA6253FB5EBB5F&&FORM=VRDGAR), [Godot video](https://www.bing.com/videos/riverview/relatedvideo?&q=godot&&mid=842503585F8EDF547044842503585F8EDF547044&&FORM=VRDGAR) and [Last one](https://www.bing.com/videos/riverview/relatedvideo?q=godot&&mid=01A5C13D2D83499014DE01A5C13D2D83499014DE&FORM=VCGVRP). These videos help with getting an understanding of how to use the app and the ways of making games. This is everything I used. I shared this with my teammate so we can understand what each of us should have learned from here.

## EDP 
EDP or Engineering Design Process is the part of the project you are on. I am still in the brainstorming and planning phase, where I need to think about how to create a game, find ways to make it fun, and learn how to utilize my tools and code a well-made game using what I've learned. 

## skills

The skills I learned are the same as last time
1. Research
Research is really important; you get a lot of good information from it. Like when I was researching the tool I was using. I found ways of using it differently and how to connect different tools with it. Also, you need to research more since you get to learn things you wouldn't have if you didn't research. Overall, I think researching is one of the most important parts. 

2. Communication
While researching, I've noticed that communication is a very important part because to work together is to communicate. We need to communicate to make changes while advancing in technology. Communication is how we share ideas and knowledge. Like for the freedom project, I have a partner, so we must communicate, as for this blog, both of us communicated and were talking about what we should do over the week.

[Previous](entry02.md) | [Next](entry04.md)

[Home](../README.md)
