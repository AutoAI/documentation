#The Birdie
The Birdie is our second vehicle. It is currently being worked on by members of the AutoAI team.
#Introduction
After completing the Cockroach, we decided that our next vehicle should be larger and more robust to accomodate for our growing capabilities. We wanted The go kart frame has reached its maximum potential, and can not be developed any further. We wanted something capable of carrying people around that had a familiar form factor. Therefore, we bought a 2 seat golf cart capable of reaching 20mph with a range of about 10 miles. This vehicle has plenty of potential and allows us to continue developing our platform.

#Building a Birdie-Class Vehicle
It is worth noting that building a Birdie-Class vehicle out of an electric golf cart is a very involved process. We recommend a basic general understanding of electronics and electromotive systems prior to attempting this build. It is also very important to note that while many of the parts and concpets involved in such a project are similar, the more you and your team deviate from our specifications, the more likely it is that your exact experience building a vehicle will differ, so plan accordingly. We advise that if you are not very comfortable with the concepts contained within to try to match what we did as closely as possible to avoid any unforseen issues.

With that being said, building a Birdie-Class vehicle is a great way to get you and your team started towards researching Autonomous Vehicles. We designed the Birdie itself with flexibility and expandability in mind, and hope that the platform suits your needs. 

##Buying the Vehicle
It goes without saying that the first step in building the platform is to purchase a vehicle. We bought an early 2000s [Club Car] (http://www.clubcar.com/us/en/golf-operations/fleet-golf.html) with a 36V electrical system and no digital controls. The exact specifications of your vehicle may vary, but some of the more important features to look for are:
- The voltage of the motor and batteries. The most common systems operate at 36 or 48 volts DC.
- The style and output power of the motor. We used and recommend a 3 horsepower series-wound brushed motor or similar.
- The mechanism by which you brake and steer the vehicle. Ours uses rack-and-pinion steering and cable-activated disk brakes. This is important when it comes to actuating the vehicle later on.
- The number of potential mounting points for sensors and the like. One thing to consider is whether or not the car can easily mount a LiDAR. In our case, we used the roof, which was very convenient.

##Working on Your Vehicle
Congradulations on the purchase of your vehicle!
Once you've purchased your vehicle, you can begin to prepare your work area. We find this important to mention because while at first the golf cart seems easy to transport and work with, you will quickly find that the time between gutting the old systems and launching your custom ones is more logistically complicated than it seems. People quickly forget that vehicles of this size are heavy and difficult to transport, especially when they have no form of propulsion. A garage or shed with good protection from the elements is what we used, and you should find something similar to suit your specific needs.

Even with a comprehensive guide like this one, no amount of documentation or paperwork will serve as a replacement for the proper tools and equipment. Make sure that you have access to and are trained on using tools such as drills, bolt cutters, angle grinders, and a full suite of socket wrenches and screwdrivers.

##Removing Old Systems
Before you can install your shiny new actuation system, you have to remove the existing components on your vehicle. For vehicles like golf carts, be familiar with how everything is assembled. Pictures go a long way when remembering how everything comes apart, since you'll eventually have to put everything back together. The first step is often removing the trim, seats, canopy, and similar non-critical parts. Our golf cart had a lot of trim, which was mostly screwed and bolted on. We also removed some of the body panels to get access to the steering column and suspension. The overall goal of this step is to make sure you can easily access the steering assembly, braking mechanism, battery compartment, and motor. It's good practice to keep the hardware and parts you remove around until you're absolutely sure they won't be needed. It's a lot easier to consult a scrap pile than ebay listings for replacements.

###Technical Points of Contention
- We removed the portion of the steering system from the rack-and-pinion mechanism all the way up to the steering wheel. This was done to make room for the linear actuator responsible for steering. Your individual situation may cary depending on whether or not you want to retain the manual steering mechanism.
- Our braking mechanism was replaced by a linear actuator. We did this by removing the foot pedal and attaching the appropriate mechanical linkage under the vehicle where the brake cable meets the pedal assembly.
- Our golf cart had a mechanical speed controller installed, which was not suitable for our needs. We removed all of the mechanical electronics and wiring in order to reconfigure it to our needs later. NOTE: Be sure to lift the vehicle off the ground and disconnect the batteries before working on the electrical system! Lead acid batteries can generate massive currents capable of melting metal and the vehicle could enter a runaway situation if any mistakes are made. Safety first!

##Installing New Controls
You're now ready to install your new actuation system! We recommend that you install and test one control at a time to avoid having to track down mistakes later. The best order to install the controls depends on the specific model of your golf cart. We installed the steering first. The brakes were installed second, and the motor controller was installed last.

###Steering
When installing the steering actuator, the objective is to apply force in the same way a rack-and-pinion system would. Mount your actuator as close to as where the manual steering hardware was as possible. This will reduce the chance of running into mechanical issues. Often you will find that the actuator fits in mounting holes previously used by the manual steering, which is very convenient.

###Braking
Installing the brake actuator is much like installing the steering actuator. This portion of the installation will likely require you to drill mounting holes in the floor of the cart to attach the actuator. We attached ours to the main brake cable to take the place of the foot pedal. Your approach may vary if you want to leave the manual brakes in place as well.

###Motor Controller
The motor controller is one of the most complex devices on the cart to setup. You have to take into account the physical location of the controller and how to deal with variables such as thermals, external weather, and cable access. We found that mounting the controller under the floor near the battery bay worked well. The location is secure and generally out of harm's way. The sheet metal of the floor provides good thermal dissipation when the controller is under load, and we added thermal paste to further improve heat transfer. Our wiring situation was so favorable such that we were able to reuse cables from the mechanical control system for our new installation. This is a good example of how keeping parts you strip from the cart can be helpful later on.

##Building an Actuation Controller
All of these controls require large amounts of DC power to operate that far exceed what any computer's GPIO pins are capable of supplying. Therefore, the next step in this build is to fabricate what we call an actuation controller. In short, this is a device that takes in serial commands, DC power from the batteries, and sensor readings. It outputs precisely measured power and signals to the actuators and motor controller, respectively. The specifics of this device will vary greatly between vehicles and is based on your needs, but the general format to use is as follows:
- Use an Arduino or similar type device to control all logic and switching.
- Implement PWM motor drivers to power the linear actuators.
- Install a buck converter to provide power for the arduino and sensors.
- For safety, install a remote switch with the ability to power off the controller from a distance.
Our actuation controller was soldered together on a perfboard and mounted inside a plastic project controller. We used GX25 style aviation connectors to serve as the interface between the controller and the rest of the cart. There are many different connectors that may suit your needs, these are worth doing some research on to decide what best suits your needs.

The Arduino will need code to make sense of the many inputs and outputs of your controller. You could write your own software from scratch if you're comfortable with the languages involved, but otherwise we offer a generic Arduino sketch that powers the Birdie for your use. You may need to modify the code to meet your needs, since the exact layout will vary from vehicle to vehicle.

##Testing Procedures and Good Practices

##Birdie Specifications
Here are more detailed specifications of the Birdie. The body of this guide often leaves out technical details in the interest of being applicable to more vehicles. Those interested in learning more about the specifics can see more here.

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
- The controller was built into a plastic [Project Box] (https://www.amazon.com/gp/product/B00LGKG1BA)
- Controller I/O and power is negotiated with [GX25 Aviation-grade Connectors] (https://www.amazon.com/dp/B015K3Z5AG). These connectors are very robust and offer a screw locking mechanism, which is perfect for a vehicular environment. 
