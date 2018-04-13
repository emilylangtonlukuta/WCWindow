# WCWindow
Description  The Smart Window is a window that is controlled by a smartphone.It can be contolled by commands sent from your phone or device and does not need manual handling.It uses a internet connection to allow the commands to be sent back and forth from window to device.It also senses dry or wet conditions and acts according to the conditions,can be programmed to be closed or opened at certain intervals. 
# Project Synopsis
A Window that does no require manual handling but instead can be opened and closed using your and app on your smartphone , tablet etc as long as there is a internet connection. This smart window Automatically closes itself in wet conditions
# Code
import RPi.GPIO as GPIO
import time
cur_X = 0 #initial value of servo motor
def setup():
        GPIO.setmode(GPIO.BOARD)
        GPIO.setup(11,GPIO.OUT)
        global servo
        servo=GPIO.PWM(11,50)
        servo.start(2.5)
        servo.ChangeDutyCycle(2.5)
        #start pwm with Duty Cycle is 2% --> Pluse with = 2%*20ms = 0.4ms
#Create PWM on pin 11 with frequency 50Hz --> period 20ms
def ServoUp():
        global cur_X
        cur_X += 2.5
        if cur_X >12:
                cur_X = 12.5
        servo.ChangeDutyCycle(cur_X)
        time.sleep(1)
def ServoDown():
        global cur_X
        cur_X -= 2.5
        if cur_X <2.5:
                cur_X = 2.5
        servo.ChangeDutyCycle(cur_X)
        time.sleep(1)
def close():
        servo.stop()
if __name__ == '__main__':
        setup()
   # Motivation
   This project came about as i used to have troubles wit water entering my room as i was in another place.
