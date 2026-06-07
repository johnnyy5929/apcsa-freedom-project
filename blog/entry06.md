# Entry 6
##### 6/7/2026

## Content 
This is my blog 6. Throughout this school year, we had a year long project, which is theFreedom ProjectW we had to pick a tool and learn how to use it. We have coded an MVP up to this point, which is like a start to our project. After we did our beyond MVP which is making the game better. So the tool that I picked was Godot. So one of the sources I used was the Learning Logs.[learning log.md](../tool/learning-log.md). This is where I compile everything I've learned and explain what I've done, which is updated weekly. Second, I used many videos like [Godot video](https://www.bing.com/videos/riverview/relatedvideo?&q=godot&&mid=06E46AEA6253FB5EBB5F06E46AEA6253FB5EBB5F&&FORM=VRDGAR), [Godot video](https://www.bing.com/videos/riverview/relatedvideo?&q=godot&&mid=842503585F8EDF547044842503585F8EDF547044&&FORM=VRDGAR) and [Last one](https://www.bing.com/videos/riverview/relatedvideo?q=godot&&mid=01A5C13D2D83499014DE01A5C13D2D83499014DE&FORM=VCGVRP). These videos help with getting an understanding of how to use the app and the ways of making games, also one of the videos shows me how to make a racing game and I watch those video to help me out.  We had to make an elevator pitch and slides for our project. [Elevator pitch](https://docs.google.com/presentation/d/1Xha94trtsnaLeQvmWcMES36a6DfrxwlJvhMviE1Zjt8/edit) and the [THE SLIDES](https://docs.google.com/presentation/d/1toVzYBiBoBgLdgQ-t5FVJ-HRmxbUwU7pVsGvUUsiFGc/edit). 

![](../tool/IMG_5907.jpg)
![](../tool/IMG_5906.jpg)
![](../tool/IMG_5904.jpg)
![](../tool/IMG_5905.jpg)
### My code
`````js
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



## Takeaways of the Expo elevator pitch

One takeaway is that I should make more eye contact. In my opinion, I feel like I didn't look around enough. I feel that when I was talking to the teachers, I was just looking at my computer, which isn't good because I don't know what people were thinking when I was presenting, and I wouldn't know if they could hear me. This is the first takeaway. 

The last takeaway was that you should be prepared before the pitch. If we weren't ready, we wouldn't know who is doing what and what part is whose. This is something I was making sure we do before we present. Which made it so that it went smoothly. These are the takeaways for the class pitch, and there were takeaways for the class presentation. We know who was doing which part of it, so when we were talking, it went well. 

## Takeaways of in-class presentation 
One takeaway from the class presentation  is that I should spend some time thinking of a hook. I lost points because my hook wasn't the best, so I should have spent more time on my hook and made it interesting. 

Another takeaway is that I should make more eye contact. In my opinion, I feel like I didn't look around enough. I feel that when I was talking, I was just looking at my computer, which isn't good because I don't know what people were thinking when I was presenting, and I wouldn't know if they could hear me.

The last takeaway was that you should be prepared before presenting in class. If we weren't ready, we wouldn't know who is doing what and what part is whose. This is something I was making sure we do before we present. Which made it so that it went smoothly. Therefore, we know what to do next time, and these are my takeaways. Now we learned for next time.


[Previous](entry05.md) | [Next](entry07.md)

[Home](../README.md)
