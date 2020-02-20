# guessinggame.py
# A Python Based LED Guessing Game
# A Random Number Guessing Game for Python
import random
import math
import pygame
from gpiozero import PWMLED
from gpiozero import Button, LED
from gpiozero.tools import negated
from signal import pause

led_higher = LED(17)
led_lower = LED(14)
led_correct = LED(27)
led_higher.off()
led_lower.off()
led_correct.off()

n = random.randint(1,100)
isCorrect = False
guess = int(input("Go on, take a guess between 0 and 100: "))
attempts = 1

while n != guess:
    if guess < n:
        print("Higher...")
        led_higher.on()
    elif guess > n:
        print("Lower...")
        led_lower.on()
           
    guess = int(input("Take a guess: "))
    attempts += 1
    led_higher.off()
    led_lower.off()
    
led_correct.on()
print("\nHuzzah!You guessed it! The number was " ,n)
print("You guessed it in ", attempts,"attempts")
input("\n\n Press the enter key to exit")
