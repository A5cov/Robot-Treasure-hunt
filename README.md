import time
import random
from random import randint
from Tkinter import*
import io
import base64
import Tkinter as tk
from urllib2 import urlopen

class landmarks:
    def __init__(self, name, id, treasure, x1, x2, y1, y2):
        self.name = name
        self.id = id
        self.treasure = treasure
        self.x1 = x1
        self.x2 = x2
        self.y1 = y1
        self.y2 = y2
    def location(self, x1, y1, x2, y2):
        x1 = x1 + randint(0,580)
        x2 = x1 + 20
        y1 = randint(0,780)
        y2 = y1 + 20
        canvas.create_rectangle(x1,y1,x2,y2,fill="purple",outline="black")
        self.x1 = x1
        self.x2 = x2
        self.y1 = y1
        self.y2 = y2
        canvas.update()

class robots:
    def __init__(self, name, treasure, x1, x2, y1, y2, position, direction):
        self.name = name
        self.treasure = treasure
        self.x1 = x1
        self.x2 = x2
        self.y1 = y1
        self.y2 = y2
        self.position = position
        self.direction = direction
    def CreateRobot(self, x1, y1, x2, y2, position):
        x1 = randint(0, 1780)
        x2 = x1 + 20
        y1 = randint(0, 780)
        y2 = y1 + 20      
        self.position=canvas.create_rectangle(x1,y1,x2,y2,fill="blue",outline="black")
        self.x1 = x1
        self.x2 = x2
        self.y1 = y1
        self.y2 = y2
        canvas.update()
    def RobotMove(self, x1, y1, x2, y2, position, direction):
        if direction == 0:
            canvas.coords(position,x1-1,y1,x2-1,y2)
            self.x1 = x1 - 1
            self.x2 = x2 - 1
            time.sleep(0.003)
        elif direction == 1:
            canvas.coords(position,x1,y1-1,x2,y2-1)
            self.y1 = y1 - 1
            self.y2 = y2 - 1
            time.sleep(0.003)
        elif direction == 2:
            canvas.coords(position,x1+1,y1,x2+1,y2)
            self.x1 = x1 + 1
            self.x2 = x2 + 1
            time.sleep(0.003)
        elif direction == 3:
            canvas.coords(position,x1,y1+1,x2,y2+1)
            self.y1 = y1 + 1
            self.y2 = y2 + 1
            time.sleep(0.003)
        
            
class lights:
    def __init__(self, name, colour, x1, x2, y1, y2):
        self.name = name
        self.colour = colour
        self.x1 = x1
        self.x2 = x2
        self.y1 = y1
        self.y2 = y2
    def CreateLight(self, x1, y1, x2, y2, colour):
        canvas.create_rectangle(x1,y1,x2,y2,fill=colour,outline="dark"+colour)
    def LightCommand(self, w1, z1, w2, z2):
        global colour
        colour = random.choice("Green", "Red")
        self.w1 = Phil.x1
        self.z1 = Phil.y1
        self.w2 = Phil.x2
        self.z2 = Phil.y2
        if colour == "Green":
            Phil.x1 = w1
            Phil.y1 = z1
            Phil.x2 = w2
            Phil.y2 = z2
        if colour == "Red":
            Phil.x1 = Phil.x1 + 0
            Phil.y1 = Phil.y1 + 0
            Phil.x2 = Phil.x2 + 0
            Phil.x2 = Phil,y2 + 0
        
LightOne = lights("LightOne", "Green", 0, 0, 0, 0)
LightTwo = lights("LightTwo", "Green", 0, 0, 0, 0)
LightThree = lights("LightThree", "Green", 0, 0, 0, 0)
Phil = robots("Phil", 0, 0, 0, 0, 0, "", 0)
Sebastion = robots("Sebastion", 0, 0, 0, 0, 0, "", 0)
Robots = (Phil, Sebastion)
Pyramid = landmarks("Pyramid", 1, "false", 0, 0, 0, 0)
Sphinx = landmarks("Sphinx", 2, "false", 0, 0, 0, 0)
ValleyoftheKings = landmarks("Valley of the Kings", 3, "false", 0, 0, 0, 0)
LondonEye = landmarks("London Eye", 4, "false", 0, 0, 0, 0)
StatueofLiberty = landmarks("Statue of Liberty", 5, "false", 0, 0, 0, 0)
EiffelTower = landmarks("Eiffel Tower", 6, "false", 0, 0, 0, 0)
NorthPole = landmarks("North Pole", 7, "false", 0, 0, 0, 0)
MountEverest = landmarks("Mount Everest", 8, "false", 0, 0, 0, 0)
StBasilsCathedral = landmarks("St.Basil's Cathedral", 9, "false", 0, 0, 0, 0)

window = Tk()
canvas = Canvas(window, width=1800, height=800, bg='white')
canvas.pack()

#Desert
image_urldesert = "http://i.imgur.com/8Ui3Nn2.gif"
image_bytdesert = urlopen(image_urldesert).read()
image_b64desert = base64.encodestring(image_bytdesert)
desert = tk.PhotoImage(data=image_b64desert)
# City
image_urlcity = "http://i.imgur.com/X6xnrbm.gif"
image_bytcity = urlopen(image_urlcity).read()
image_b64city = base64.encodestring(image_bytcity)
city = tk.PhotoImage(data=image_b64city)
#Snow
image_urlsnow = "http://i.imgur.com/2ICSPuc.gif"
image_bytsnow = urlopen(image_urlsnow).read()
image_b64snow = base64.encodestring(image_bytsnow)
snow = tk.PhotoImage(data=image_b64snow)

canvas.create_line(600,800,600,0,fill="black",width=1)
canvas.create_line(1200,800,1200,0,fill="black",width=1)

canvas.create_image(0,0, image=desert, anchor=NW)
canvas.create_image(600,0, image=city, anchor=NW)
canvas.create_image(1200,0, image=snow, anchor=NW)

canvas.update()

colour = "Green"

LightOne.CreateLight(280,380,320,420,colour)
LightTwo.CreateLight(880,380,920,420,colour)
LightThree.CreateLight(1480,380,1520,420,colour)
Phil.CreateRobot(0,0,0,0, "")
Sebastion.CreateRobot(0,0,0,0, "")
Pyramid.location(0,0,0,0)
Sphinx.location(0,0,0,0)
ValleyoftheKings.location(0,0,0,0)
LondonEye.location(600,0,0,0)
StatueofLiberty.location(600,0,0,0)
EiffelTower.location(600,0,0,0)
NorthPole.location(1200,0,0,0)
MountEverest.location(1200,0,0,0)
StBasilsCathedral.location(1200,0,0,0)

randomtreasures = []
for x in range(0, 4):
    y = randint(1, 9)
    randomtreasures.append(y)

for x in range(0, 4):
    if randomtreasures[x] == Pyramid.id:
        Pyramid.treasure = "true"
    elif randomtreasures[x] == Sphinx.id:
        Sphinx.treasure = "true"
    elif randomtreasures[x] == ValleyoftheKings.id:
        ValleyoftheKings.treasure = "true"
    elif randomtreasures[x] == LondonEye.id:
        LondonEye.treasure = "true"
    elif randomtreasures[x] == StatueofLiberty.id:
        StatueofLiberty.treasure = "true"
    elif randomtreasures[x] == EiffelTower.id:
        EiffelTower.treasure = "true"
    elif randomtreasures[x] == NorthPole.id:
        NorthPole.treasure = "true"
    elif randomtreasures[x] == MountEverest.id:
        MountEverest.treasure = "true"
    elif randomtreasures[x] == StBasilsCathedral.id:
        StBasilsCathedral.treasure = "true"

atdestination = False
Sebastion.direction = 0
PhilDestination = Pyramid
z = 0

while atdestination == False:
    if Phil.x1 > PhilDestination.x1:
        Phil.direction = 0
    elif Phil.x1 < PhilDestination.x1:
        Phil.direction = 2
    elif Phil.y1 > PhilDestination.y1:
        Phil.direction = 1
    elif Phil.y2 < PhilDestination.y2:
        Phil.direction = 3
    
    Phil.RobotMove(Phil.x1,Phil.y1,Phil.x2,Phil.y2,Phil.position,Phil.direction)
    canvas.update()
    Sebastion.RobotMove(Sebastion.x1,Sebastion.y1,Sebastion.x2,Sebastion.y2,Sebastion.position,Sebastion.direction)
    canvas.update()

    if Phil.x1 == PhilDestination.x1 and Phil.y1 == PhilDestination.y1:
        y = randint(1, 9)
        if Pyramid.id == y:
            PhilDestination = Pyramid
        elif Sphinx.id == y:
            PhilDestinaton = Sphinx
        elif ValleyoftheKings.id == y:
            PhilDestination = ValleyoftheKings
        elif LondonEye.id == y:
            PhilDestination = LondonEye
        elif StatueofLiberty.id == y:
            PhilDestination = StatueofLiberty
        elif EiffelTower.id == y:
            PhilDestination = EiffelTower
        elif NorthPole.id == y:
            PhilDestination = NorthPole
        elif MountEverest.id == y:
            PhilDestination = MountEverest
        elif StBasilsCathedral.id == y:
            PhilDestination = StBasilsCathedral      
        
        z = z + 1
        if z == 10:
            atdestination = True

for robot in Robots:
    robot.LightCommand(robot.x1, robot.y1, robot.x2, robot.y2)
            
window.mainloop()
