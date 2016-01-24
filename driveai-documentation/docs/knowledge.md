# Introduction
This is where everything we know about self driving vehicles will be found. We're eager to have people join, learn from, and contribute to our project.

## What are they?

Autonomous vehicles (AV's), also known as self-driving cars, are vehicles that drive themselves. For now, the vehicles are generally required to be supervised by a driver, but the goal is for the cars to be able to drive themselves on their own.

## Why are they important?

Autonomous vehicles will have an impact similar to the internet in magnitude and nature. The internet allowed us to move information at a reduced cost and without human interaction. Autonomous vehicles will have the same effect on the transportation of physical goods.

More importantly, autonomous vehicles are going to save a tremendous amount of lives. Driver error is a leading cause of death, and self-driving vehicles will make the roads safer because they aren't prone to making the same types of errors.

## How do they work?

Autonomous vehicles use an array of sensors, including GPS, cameras, and radar, to gather information about the world around them (more about sensors [here](TODO)). Data from these sensors is then processed by state of the art algorithms to interpret the world in a meaningful way. They then use this interpretation to make fast and reliable decisions.

# Chapter 1: Levels of autonomy

According to the [National Highway Traffic Safety Administration](http://www.nhtsa.gov/), there are 5 levels of autonomy (including Level 0: No Automation). We've shortened their definitions for brevity, but the full definitions can be found [here](http://www.nhtsa.gov/staticfiles/rulemaking/pdf/Automated_Vehicles_Policy.pdf).

* *Level 0 - No Automation:* The driver is soley resposible for monitoring the roadway, and for safe operation of all vehicle controls.
* *Level 1 - Function-specific Automation:* The driver can choose to cede limited authoiry over a primary control (as in adaptive cruise control), the vehicle can automatically assume limmited authority over a primary control (as in electronic stability control), or the automated system can provide added control to aid the driver in certain normal driving or crash-imminent situations (e.g., dynamic brake support in emergencies).
* *Level 2 - Combined Function Automation:* The driver is still responsible for monitoring the roadway and safe opperation and is expected to be available for control at all times and on short notice. At level 2 in the specefic operation conditions for which the system is designed, an automated operating mode is enabled such that the driver is disengaged from physically operating the vehicle by having his or her hands off the steering wheel and foot off the pedal at the same time.
* *Level 3 - Limited Self-Driving Automation:* Vehicles at this level of automation enable the driver to cede full control of all safety-critical functions under certain traffic or environmental conditions and in those conditions to rely heavily on the vehicle to monitor for changes in those conditions requiring transition back to driver control. The driver is expected to be available for occasional control, but with sufficiently comfortable transition time. At level 3, the vehicle is designed so that the driver is not expected to constantly monitor the roadway while driving.
* *Level 4 - Full Self-Driving Automation:* The vehicle is designed to perform all safety-critical driving functions and monitor roadway conditions for an entire trip. The driver is not expected to be available for control at any time during the trip.

# Chapter 2: Sensors

Autonomous vehicles rely on several sensors to gather information. These sensors vary widely in how they work and the types of information they provide, so recent autonomous vehicles generally use most or all of them.

## Lidar
Lidar is one of the most prominent sensors on an autonomous vehicle, with units frequently mounted a few inches above the roof of the vehicle in the center. Lidar units typically scan in all directions around the vehicle, delivering information about the postitions of cars, buildings, and everything else. Lidar data is relatively precise, fast, and reliable, and for these reasons it can be thought of as the primary sensor for an autonomous vehicle.

Lidar works by shooting a laser pulse and measuring the time it takes for the light to strike something and be reflected back. The time it takes for the light to travel is used to determine the distance to the nearest object in whichever direction it was pointing. Lidar units spin the laser and shoot pulses hundreds of thousands or millions of times each second in different directions to capture the environment in 3D. Repectable lidar units are able to determine the brightness of the object struck (by measuring the intensity of the light reflected back) to capture the environment in black-and-white, and can detect multiple strikes from one laser pulse (such as if one pulse strikes a raindrop and travels through to another object behind it), helping them to work in adverse conditions.

Because of the precision required of them, lidar units start at $8000 and can cost many times more. A new technology, solid-sate lidar, promises to reduce that cost (supposedly by [next year](http://spectrum.ieee.org/cars-that-think/transportation/sensors/quanergy-solid-state-lidar)). Solid-state lidar works mostly the same, but instead of having moving parts, it changes the angle of the laser pulse by sending it through a crystal to bend the light at an electronically-adjustable angle. While this doesn't allow for full 360-degree coverage, a few units together could provide the same sensory coverage as current units for a cost many times lower.

## Radar
Radar is in some ways similar to lidar. Radar works by firing pulses of radio waves in a general direction and measuring how those waves are reflected by objects they encounter. Radar tends to be much less precise than lidar, but operates more quickly and reliably, making it helpful for tasks like keeping a safe following distance. Radar also offers the advantage that it can directly measure the speed of objects (based on the wavelengths of radio wave reflections), a task which is deceptively tricky for other types of sensors.

## Cameras
Cameras are used by autonomous vehicles to read visual information from the environment, including lane markings, traffic lights, and signs. While people have no problem interpreting this visual information, telling a computer how to interpret images in a meaningful way is an area of active research and modern techniques often require lots of computational power.

Cameras work by using a lens to focus light from a particular direction onto an array of photosensors. These photosensors measure the total amount of light that hits them (in color cameras, the total amount of each color light that hits them) and each photosensor's measurement results in one pixel of the resulting image. It is then up to complicated computer vision algorithms to make deductions from the image.

There are a few creative ways to use cameras. Infrared cameras can detect the heat emited by objects, helping the vehicle identify pedestrians or vehicles. Using two cameras together, side-by-side, allows the vehicle to detect how far away objects in the image are (using some intense computation). Less commonly, the lens on a camera can have its focal length quickly adjusted and the distance to an object can be deduced by which focal length makes it appear most clearly in the camera's images.
