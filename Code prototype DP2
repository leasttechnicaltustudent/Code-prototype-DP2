##--- Imports
import digitalio
import board
import neopixel
import time
import random

##--- Variables
state_wait = 0
state_start_game = 1
state_wait_button_press = 2
state_red_wins = 3
state_blue_wins = 4
state_green_wins = 5
state_magenta_wins = 6
state_onderweg_blue = 7
state_onderweg_red = 8
state_onderweg_green = 9
state_onderweg_magenta = 10
current_state = 0

# Button variables
red_pin = board.D7
red_button = digitalio.DigitalInOut(red_pin)
red_button.direction = digitalio.Direction.INPUT

blue_pin = board.D13
blue_button = digitalio.DigitalInOut(blue_pin)
blue_button.direction = digitalio.Direction.INPUT

green_pin = board.D4
green_button = digitalio.DigitalInOut(green_pin)
green_button.direction = digitalio.Direction.INPUT

magenta_pin = board.D2
magenta_button = digitalio.DigitalInOut(magenta_pin)
magenta_button.direction = digitalio.Direction.INPUT

# For the Chainable LED:
pin_leds = board.D3
num_leds = 1
leds = neopixel.NeoPixel(pin_leds, num_leds, auto_write=False, pixel_order=neopixel.GRBW)

led_off = (0, 0, 0, 0)
led_red = (255, 0, 0, 0)
led_blue = (0, 0, 255, 0)
led_white = (0, 0, 0, 255)
led_green = (0, 255, 0, 0)
led_magenta = (204, 0, 204, 0)

# Timer variables
timer_duration = 0
timer_mark = 0

##--- Functions
def set_led_color(color):
    global leds
    leds.fill(color)
    leds.show()

def set_timer(duration):
    global timer_duration, timer_mark
    timer_duration = duration
    timer_mark = time.monotonic()

def timer_expired():
    global timer_mark, timer_duration
    if time.monotonic() - timer_mark > timer_duration:
        return True
    else:
        return False

##--- Main loop
while True:
    if current_state == state_wait:
        set_led_color(led_off)
        current_state = state_start_game

    elif current_state == state_start_game:
        if timer_expired():
            set_led_color(led_white)
            set_timer(30)
            current_state = state_wait_button_press

    elif current_state == state_wait_button_press:
        if red_button.value:
            print("Hulp")
            current_state = state_red_wins
        elif blue_button.value:
            print("Water")
            current_state = state_blue_wins
        elif green_button.value:
            print("koffie")
            current_state = state_green_wins
        elif magenta_button.value:
            print("bed")
            current_state = state_magenta_wins
        elif timer_expired(): 
            print("Check up on patient")
            set_led_color(led_white)
            time.sleep(1)
            set_led_color(led_off)
            time.sleep(1)
            set_led_color(led_white)
            time.sleep(1)
            set_led_color(led_off)
            time.sleep(1)
            set_led_color(led_white)
            time.sleep(1)
            set_led_color(led_off)
            time.sleep(1)
            current_state = state_start_game

    elif current_state == state_blue_wins:
        set_led_color(led_blue)
        time.sleep(5)
        current_state = state_onderweg_blue

    elif current_state == state_red_wins:
        set_led_color(led_red)
        time.sleep(5)
        current_state = state_onderweg_red
    
    elif current_state == state_green_wins:
        set_led_color(led_green)
        time.sleep(5)
        current_state = state_onderweg_green
        
    elif current_state == state_magenta_wins:
        set_led_color(led_magenta)
        time.sleep(5)
        current_state = state_onderweg_magenta
        
    elif current_state == state_onderweg_blue:
        print("Ik kom eraan!")
        set_led_color(led_blue)
        time.sleep(1)
        set_led_color(led_off)
        time.sleep(1)
        set_led_color(led_blue)
        time.sleep(1)
        set_led_color(led_off)
        time.sleep(1)
        set_led_color(led_blue)
        time.sleep(1)
        set_led_color(led_off)
        time.sleep(1)
        current_state = state_wait
    
    elif current_state == state_onderweg_red:
        print("Ik kom eraan!")
        set_led_color(led_red)
        time.sleep(1)
        set_led_color(led_off)
        time.sleep(1)
        set_led_color(led_red)
        time.sleep(1)
        set_led_color(led_off)
        time.sleep(1)
        set_led_color(led_red)
        time.sleep(1)
        set_led_color(led_off)
        time.sleep(1)
        current_state = state_wait
        
    elif current_state == state_onderweg_green:
        print("Ik kom eraan!")
        set_led_color(led_green)
        time.sleep(1)
        set_led_color(led_off)
        time.sleep(1)
        set_led_color(led_green)
        time.sleep(1)
        set_led_color(led_off)
        time.sleep(1)
        set_led_color(led_green)
        time.sleep(1)
        set_led_color(led_off)
        time.sleep(1)
        current_state = state_wait
        
    elif current_state == state_onderweg_magenta:
        print("Ik kom eraan!")
        set_led_color(led_magenta)
        time.sleep(1)
        set_led_color(led_off)
        time.sleep(1)
        set_led_color(led_magenta)
        time.sleep(1)
        set_led_color(led_off)
        time.sleep(1)
        set_led_color(led_magenta)
        time.sleep(1)
        set_led_color(led_off)
        time.sleep(1)
        current_state = state_wait
