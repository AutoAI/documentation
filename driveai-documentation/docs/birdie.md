#The Birdie
The Birdie is our second vehicle. It is currently being worked on by members of the AutoAI team.
#Introduction
After completing the Cockroach, we decided that our next vehicle should be larger and more robust to accomodate for our growing capabilities. The go kart frame has reached its maximum potential, and a new vehicle is in order that can expand to meet our needs is needed. Therefore, we bought a golf cart capable of reaching 20mph with a range of about 10 miles in order to continue growing.

#Specifications
The Birdie is an early 2000s [Club Car] (http://www.clubcar.com/us/en/golf-operations/fleet-golf.html) with heavy modifications.
##Drivetrain
- The cart uses a 3hp 36v series-wound dc motor fed by 6 Trojan T-105 batteries at 6 volts each. Cables in this assembly are 6AWG since at full speed the nominal current is around 60 amps.
- Speed control of the motor is done using a high power mosfet-based controller, which is fed an external source of pwm and handles switching of the motor power. This device is fairly robust, as it has to handle over 2000 watts of power.
- All miscellaneous electromechanical systems on the cart have been removed and replaced with solid-state control logic. This was done to make actuation simpler and more reliable, while decreasing weight and improving range.
- The steering column has been completely removed, and a 6" stroke linear actuator has been attached where the rack and pinion mechanism would usually be.
- The brake pedal has been removed and replaced with a 2" stroke linear actuator to supply braking force.
