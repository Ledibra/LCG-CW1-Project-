# Linear Congruential Generators

import time
import numpy as np
import matplotlib.pyplot as plt


time1 = time.time() # this gives the time in seconds


n = int(input("Insert how many random numbers do you want to generate? "))
all_numbers = np.zeros(n) # this variable holds all the random numbers that has been generated 

option = int(input("Choose how you wish to insert your seed, where '1' is the seed of your choice, '2' for system time, and '3' through a .txt file:  "))
   
if option == 1:
        
    seed = int(input("insert a seed number:  "))
    
elif option == 2:

    seed = time1  #Here we use the time from the computer. 
                  
elif option == 3:
    
    userinput = input('Enter name the of file: ')
    f = open(userinput, 'r') 
    seed = int(f.readline())
        
def RNG(m=2**31, a=1103515245, c=12345): #Paramatres. one of the most common parametres used for LCGs.

    global seed  # declaring seed as a global in order for the se ed to update and get a new random number
    
    seed = int((a*seed + c) % m) # formula used to create new seed
    
    return seed  

for i in range(n):
    
    all_numbers[i] = RNG()
  
    print("seed number =", seed, "random number generated =", RNG())

plt.hist(all_numbers, bins=10, color='green', alpha=0.3, edgecolor='black')
plt.show() #this section i create a histogram to have an idea of where our random numbers are scattered, 
           #and know if they are scattered somewhat evenly.     
