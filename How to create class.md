How to create class, a ball class here.
    -  Class allows us to store some data which is `position`, `speed` and [[functionality]] is you can move the ball, render the ball etc
    - `myball = Ball(10.0, 15.0, 0.0, -5.0)`
    - `myball` is An object is an instantiation of a class `Ball`  ; `Class` of type `Ball`
    - the [[constructor]] is just the name of the [[class]] and some information of what I want my object to be
    - See what [[constructor]] does.
    - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fsuperbeliever%2FUS0ebb3mHR.png?alt=media&token=a7391fb4-8ee9-4702-827d-d35ac60ba43a)
    - here the number `3000` is an address, it just a [[pointer]] to where it is.
    - I've the data and all the [[functionality]] that comes with that class
    - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fsuperbeliever%2FkUY3HYTKNX.png?alt=media&token=a95d6e53-4559-40ef-a41f-54e51703c062)
    - We can do that all day long, we can create as many objects as we want.
    - [[dot expression]] can be used to get the values
      - Either the data and [[functionality]] using the [[dot expression]] associated with the object
      - We can also access [[functionality]] like `ball1.update_position(0.1)`
      - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fsuperbeliever%2F_bKpZ-JYaG.png?alt=media&token=5ca2208a-e217-4200-891c-adbff2ead8a4)
	  - Creating a Ball Class

```python
import drawSvg as draw
D = draw.Drawing(200, 200, origin = 'center') #define drawing canvas
#Here CAPTICAL LETTERS ARE USED TO DENOTE GLOBAL VARIABLES,
#ALTHOUGH IT'S NOT ADVISED TO USE ANY GLOBAL VARIABLE AT ALL
EARTH_GRAVITY_ACCELARTION = - 9.8 #	acceleration due to gravity, m/sec^2
BALL_RADIUS = 10 #Radius of the ball in pixels

class Ball:
		def **init**(self, start_x, start_y, start_v_x, start_v_y, color = 'blue'):
		#Ball location and velocity
			self.x = start_x
			self.y = start_y
			self.v_x = start_v_x
			self.v_y = start_v_y

			#Ball color, for drawing purposes
			self.color = color

		def update_position(self, timestep):
			self.x = self.x + timestep * self.v_x
			self.y = self.y + timestep * self.v_y

		def update_velocity(self.timestep):
			self.v_y = self.v_y + EARTH_GRAVITY_ACCELARTION

		def animate_step(self, timestep):
			self.update_position(timestep)
			self.update_velocity(timestep)
		def draw(self):
			D.append(draw.Circle(self.x, self.y, BALL_RADIUS, fill = self.color))
```

### [[constructor]] [[__init__]]

```python
def __init__(self, start_x, start_y, start_v_x, start_v_y, color = 'blue'):
	#Ball location and velocity
	self.x = start_x
	self.y = start_y
	self.v_x = start_v_x
	self.v_y = start_v_y
```
	


- ==very special==
        - **Every single class created in python has call called construction and it's job is to allocate memory, assign data and return address**
        -  [[constructor]] for more
        - The `__init__` must must have the first argument `self`
        - `self`
            - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2Fsuperbeliever%2FUS0ebb3mHR.png?alt=media&token=a7391fb4-8ee9-4702-827d-d35ac60ba43a)
            - `self` point to the address `3000`
    - [[functionality]]

```python
myball = Ball(10.0, 15.0, 0.0, -5.0)

myball.update_position(0.1) #update_position(myball, 0.1)

def update_position(self, timeself):
	self.x = self.x + timestep * self.v_x
	self.y = self.y + timestep * self.v_y
```

- When you print a ball it doesn't mean anything.

```python
b = Ball(10, 15, 0, -5)
print b
<ball.Ball instance at 0x100499a70>
```
If you want to print the ball use [[special function]]  [[__str__]]

```python
def __str__(self):
	return str(self.x) + "," + str(self.y)
```


 ```python
   b = Ball(10, 15, 0, -5)
    print(b)
    0, 0
```
 - [ ] Animating two balls in [[Jupyter]]
