#The Birdie
The Birdie is our second vehicle. It is currently being worked on by members of the AutoAI team.
#Introduction
After completing the Cockroach, we decided that our next vehicle should be larger and more robust to accomodate for our growing capabilities. The go kart frame has reached its maximum potential, and a new vehicle is in order that can expand to meet our needs is needed. Therefore, we bought a golf cart capable of reaching 20mph with a range of about 10 miles in order to continue growing.

#Specifications
The Birdie is an early 2000s [Club Car] (http://www.clubcar.com/us/en/golf-operations/fleet-golf.html) which has been heavily modified.
##Drivetrain and Electrical
- The cart uses a 2.97hp 36v (0.58Ω) series-wound DC motor fed by 6 Trojan T-105 batteries at 6 volts each. Cables in this assembly are all 6AWG since at full speed the nominal current is around 62 amps.
- Speed control of the motor is done using a [Kelly KDZ48200] (http://kellycontroller.com/kdz4820024v-48v200aseriespm-p-951.html) motor controller, which is fed an external source of pwm from the actuation controller and handles switching of the motor power. This device is fairly robust, as it has to handle over 2000 watts of power.
- All miscellaneous electromechanical systems on the cart have been removed and replaced with solid-state control logic. This was done to make actuation simpler and more reliable, while decreasing weight and improving range.
- - The electrical system is protected with a [200A Fuse] (http://kellycontroller.com/ane-200a-fuse-p-196.html)
- (TODO) auxiliary systems other than the drivetrain require 12v, so a large buck converter was installed.

##Actuation
- The steering column has been completely removed, and a 6" stroke [linear actuator] (https://www.firgelliauto.com/products/feedback-rod-actuator) has been attached where the rack and pinion mechanism would usually be.
- The brake pedal has been removed and replaced with a 2" stroke [linear actuator] (https://www.firgelliauto.com/products/feedback-rod-actuator) to supply braking force.

###Actuation Controller 3.0
After our second actuation controller was destroyed during a testing accident, we decided that the next iteration of our control system needed to be powerful and reliable. Thus, we intentionally overbuilt our actuation controller 3.0 as such:
- The steering and braking linear actuators consume 5A @ 12V each, so we control them with [Cytron 13A DC Motor Controllers] (http://www.robotshop.com/en/cytron-13a-5-30v-single-dc-motor-controller.html). These controllers include 13A of rated capacity and a full NMOS H-Bridge for bidirectional high-power operation.
- An [Arduino Micro] (https://www.arduino.cc/en/Main/ArduinoBoardMicro) handles low-level actuation control. It reads in the actuator positions and accepts commands over serial from the main computer. The Arduino code is available in the [Birdie Actuator Repository] (https://github.com/AutoAI/birdie-actuator/tree/master).
- The Arduino and related devices are powered by a [DROK LM2596 Voltage Converter] (https://www.amazon.com/DROK-Numerical-Switching-Adjustable-Stabilizers/dp/B00BYTEHQO/) that converts the controller's 12V input to 5V.

