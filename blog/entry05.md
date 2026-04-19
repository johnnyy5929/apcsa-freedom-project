# Entry 5
##### 4/19/2026

## context
For this year-long project, I decided to use Godot as my tool. Godot is a game engine for making 2D or 3D games. After doing my learning logs, I decided to stay with Godot as my tool. My partner and I planned to create a racing game. We decided to use the 2D mode for this on Godot, as we wanted to make a 2D top-down racing game. We've been talking to each other outside of school and in school about what we have done. Until now, we had a plan for our MVP, and started our prototype, which you can see at the bottom. 

##### What I have done, so over the break, I finished my MVP, which you can see below. 

![](../tool/IMG_5907.jpg)
![](../tool/IMG_5906.jpg)
![](../tool/IMG_5904.jpg)
![](../tool/IMG_5905.jpg)



````` js
extends Area2D

class_name Car
@export var max_speed: float = 380.0
@export var friction: float = 300.0
@export var acceleration: float = 150.0
@export var steer_strength: float = 2.0
@export var min_steer_factor: float = 0.5
@export var bounce_time: float = 0.8
@export var bounce_force: float = 30.0


var _throttle: float = 0.0
var _steer: float = 0.0
var _velocity: float = 0.0
# Called when the node enters the scene tree for the first time.
func _ready() -> void:
	pass 


# Called every frame. 'delta' is the elapsed time since the previous frame.
func _process(delta: float) -> void:
	_throttle = Input.get_action_strength("ui_up")
	_steer = Input.get_axis("ui_left", "ui_right")
	
func _physics_process(delta: float) -> void:
	apply_throttle(delta)
	apply_rotation(delta)
	position += transform.x * _velocity * delta
	
func apply_throttle(delta: float) -> void:
	if _throttle > 0.0:
		_velocity += acceleration * delta
	else:
		_velocity -= friction * delta
		
	_velocity = clampf(_velocity, 0.0, max_speed)
		
func get_steer_factor() -> float:
	return clamp(
		1.0 - pow(_velocity / max_speed, 2.0),
		min_steer_factor,
		1.0
	) * steer_strength
		
		
func apply_rotation(delta:float) -> void:
	rotate(steer_strength * delta * _steer)
	
	
func bounce() -> void:
	set_physics_process(false)
	_velocity = 0.0
	position += -transform.x * bounce_force
	await get_tree().create_timer(bounce_time).timeout
	set_physics_process(true)
	
func hit_boundary() -> void:
	bounce()

`````
````` js
extends Node

class_name Track


func _on_track_area_entered(area: Area2D) -> void:
	if area is Car: area.hit_boundary()


func _on_finish_line_area_entered(area: Area2D) -> void:
	if area is Car: area.lap_completed()

`````

So, what I did for my freedom project is that I made the track, the car and made it so when you hit the track walls you get kicked back and you have to wait a second to go on. I write this code above where you can see this and made it so when you finish the race it tells you that you finish. 
## Sources 
So one of the sources I used was the Learning Logs. [learning log.md](../tool/learning-log.md). This is where I compile everything I've learned and explain what I've done, which is updated weekly. Second, I used many videos like [Godot video](https://www.bing.com/videos/riverview/relatedvideo?&q=godot&&mid=06E46AEA6253FB5EBB5F06E46AEA6253FB5EBB5F&&FORM=VRDGAR), [Godot video](https://www.bing.com/videos/riverview/relatedvideo?&q=godot&&mid=842503585F8EDF547044842503585F8EDF547044&&FORM=VRDGAR) and [Last one](https://www.bing.com/videos/riverview/relatedvideo?q=godot&&mid=01A5C13D2D83499014DE01A5C13D2D83499014DE&FORM=VCGVRP). These videos help with getting an understanding of how to use the app and the ways of making games, also one of the videos shows me how to make a racing game and I watch those video to help me out. 

## EDP 
EDP or Engineering Design Process is the part of the project you are on. I am still on the prototype phase; however, this time I finished the coding part and am now making improvements on my project. 
## skills

The skills I learned are the same as last time
1. Research
Research is really important; you get a lot of good information from it. Like when I was researching the tool I was using. I found ways of using it differently and how to connect different tools with it. Also, you need to research more since you get to learn things you wouldn't have if you didn't research. Overall, I think researching is one of the most important parts. 

2. Communication
While researching, I've noticed that communication is a very important part because to work together is to communicate. We need to communicate to make changes while advancing in technology. Communication is how we share ideas and knowledge. Like for the freedom project, I have a partner, so we must communicate, as for this blog, both of us communicated and were talking about what we should do over the week.

3. AI
I have learned one more thing, which is that AI isn't that bad sometimes if you use it for the right things, like asking it questions that can later guide you to the answers you want. Don't use the tool to do it for you, but instead use it to give you ideas and help you out with questions you might have that you couldn't get. So these are the skills I learned so far, and I will be adding more to this on my next blog.

[Previous](entry04.md) | [Next](entry06.md)

[Home](../README.md)
