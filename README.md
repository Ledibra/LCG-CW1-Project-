# Linear Congruential Generators

import time
import numpy as np
import matplotlib.pyplot as plt

time1 = time.time() # this gives the time in seconds

n = 10000
all_numbers = np.zeros(n) # this variable holds all the random numbers that has been generated 

seed = time1 #Here we use the time fri=om the computer. 
             #If we want to set the program to ask a seed from the user we use 
             #'int(input("insert a seed number: "))'

def RNG(m=111323, a=5, c=9): #Paramatres 
    
    global seed  # declaring seed as a global in order for the seed to update and get a new random number
    
    seed = int((a*seed + c) % m) # formula used to create new seed
    
    return seed

for i in range(n): 
        all_numbers[i] = RNG()
    
    print("seed number =", seed, "random number generated =", RNG())

plt.hist(all_numbers, bins=10, color='green', alpha=0.3, edgecolor='black')
plt.show() #this section i create a histogram to have an idea of where our random numbers are scattered, 
           #and know if they are scattered somewhat evenly.      

        
