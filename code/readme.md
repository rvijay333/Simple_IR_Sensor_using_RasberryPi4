

### Program :

```python
import RPi.GPIO as GPIO
import time

irs_pin = 26   # IR sensor pin
led_pin = 17   # LED pin
buzz_pin = 24  # Buzzer pin

GPIO.setmode(GPIO.BCM)

GPIO.setup(irs_pin, GPIO.IN)
GPIO.setup(led_pin, GPIO.OUT)
GPIO.setup(buzz_pin, GPIO.OUT)

try:
    while True:
        if GPIO.input(irs_pin) == 0:
            GPIO.output(led_pin, True)
            GPIO.output(buzz_pin, True)
            print("OBSTACLE DETECTED :) !!!")
            time.sleep(0.1)
        else:
            GPIO.output(led_pin, False)
            GPIO.output(buzz_pin, False)
            print("NO OBSTACLE DETECTED!! :(")
            time.sleep(0.1)
        

        

except KeyboardInterrupt:
    pass

finally:
    GPIO.cleanup()

