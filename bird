import pygame
from random import randrange
import random
import numpy as np


pygame.init()
ird = pygame.image.load('player1.png')
fon = pygame.image.load('fon.png')
be = pygame.image.load('base.png')
pip = pygame.image.load('pipe.png')
clock =pygame.time.Clock()
fpip = pygame.transform.flip(pip,False,True)








class NN:
	def __init__(self):
		self.neron = None
		self.biats=[]
		self.weights=None
		self.flg =False
		
		
		self.weights=np.array([np.random.random(),np.random.random(),np.random.random(),np.random.random()])
		
		
	def setup(self,bird,pipe):
		self.neron = np.array([pipe._x - bird._x,pipe.y - bird._y,pipe.y-130 - bird._y,bird._y])
		self.s = 0
	def set(self):
		pass
		
		


	def ner(self):
		n=0
		while n < 3 :
			self.s+=(self.weights[n]*self.neron[n])
			n+=1
		if self.s<=0.5:
			self.flg = True
		else : self.flg = False




class Bird:

	def __init__(self,x,y):
		self._x = x
		self._y =y
		self.jumps = 5
		self.gravity = 2
		self.live =True

	def draw(self,win):
		win.blit(ird,(self._x,self._y))

	def jump (self):
		self._y-=self.jumps
	def move(self):
		self._y+=self.gravity
	def coli(self):
		if self._y <=12 :
			self.live = False
		else: self.live = True		


class Pipe:
	def __init__(self,x):
		self._x = x
		self.y= randrange(192,320)
		self.yf = self.y-320- 130
		self.speedp = 3
		self.flag = False
		self.de = False
	def draw(self,win):
		win.blit(pip,(self._x,self.y))
		win.blit(fpip,(self._x,self.yf))
	def move (self):
		self._x-=self.speedp
		if self._x < 100:
			self.flag = True
		else : self.flag = False
		if self._x == 0 :
			self.de = True
		else: self.de = False

		
	def coli(self,bird):
		if (bird._x-12 <= self._x and bird._x >self._x -52 and bird._y <=self.y +320  and bird._y>=self.y+12 ) :
			# print ("выход с низу ")
			bird.live = False
			
		elif  (bird._x-12 <= self._x and bird._x >self._x -52 and bird._y <=self.yf +320  and bird._y>=self.yf+12 ) :
			# print("выход сверху")
			bird.live = False
			


			
	

	# def get_s(self):
	# 	return self._x
		
class Base:
	def __init__(self,x):
		self.y = 512-112
		self.x = x 

		
	def draw (self,win):
		win.blit(be,(self.x-288,self.y))
		win.blit(be,(self.x,self.y))
	def move(self):
		self.x-=1
		if self.x==0:
			self.x=288
	def coli(self,bird):
		if (bird._y >= self.y+12) :
			# print("плита")
			bird.live = False
	





base = Base(288)
# pipe = Pipe(288)
birds = []
nn = []
l= 0 
while l <=15:
	birds.append(Bird(100,250+(l*3)))
	nn.append(NN())
	
	l+=1

def draw(win,bird,pipes):
	win.blit(fon,(0,0))
	for bird in birds:
		bird.draw(win)
	# pipe.draw(win)
	base.draw(win)
	for pipe in pipes:
		pipe.draw(win)
		pipe.move()


	pygame.display.update()
def main():
	
	win = pygame.display.set_mode((288,512))
	
	
	pipes = [Pipe(287)]
	ddlg = True
	
	u=0 
	o=0
	

	


	while ddlg:
		keys = pygame.key.get_pressed()

		
		clock.tick(120)
		
		
		base.move()
	
		
		if pipes[-1].flag:
			pipes.append(Pipe(287))



			

		
		for z in birds:
			for nero in nn:
				z.move()
			

				nero.setup(z,pipes[-1])
				
				nero.ner()
				
				
				z.coli()
				base.coli(z)
				if nero.flg:
					z.jump()
		for pi in pipes:
			pi.coli(z)
			if pi.de:
				pipes.pop(0)

					
					
				
				# print(nn.weights)
			# if birds==[]:
			# 	pass
		if birds[u].live==False:
			birds.pop(u) 
			nn.pop(	u)
			u+=1
				


		

		draw(win,birds,pipes)
		
		
		for event in pygame.event.get():
			
					
			if event.type == pygame.QUIT:
				exit() 



main()








