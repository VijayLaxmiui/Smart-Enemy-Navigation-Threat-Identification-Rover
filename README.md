# Smart-Enemy-Navigation-Threat-Identification-Rover
def stop():
    left_motor_forward.off()
    left_motor_backward.off()
    right_motor_forward.off()
    right_motor_backward.off()

def forward():
    left_motor_forward.on()
    left_motor_backward.off()
    right_motor_forward.on()
    right_motor_backward.off()

def backward():
    left_motor_forward.off()
    left_motor_backward.on()
    right_motor_forward.off()
    right_motor_backward.on()

def right_turn():
    left_motor_forward.on()
    left_motor_backward.off()
    right_motor_forward.off()
    right_motor_backward.on()

def left_turn():
    left_motor_forward.off()
    left_motor_backward.on()
    right_motor_forward.on()
    right_motor_backward.off()

print("Robot starting...")

try:
    while True:
        dist = ultrasonic.distance * 100  # in cm
        print(f"Distance: {dist:.1f}cm")
        if dist < 20:  # obstacle within 20cm
            stop()
            print("Obstacle detected! Taking photo...")
            picam2.capture_file("obstacle.jpg")
            print("Turning right...")
            right_turn()
            sleep(0.7)
            stop()
            sleep(0.5)
        else:
            forward()
        sleep(0.1)

except KeyboardInterrupt:
    print("Stopping robot...")
    stop()
    picam2.
