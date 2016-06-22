# FAQ / How To

I'd better name this section "FAQ / OAC", including the Once Asked Questions. When I receive a
question that requires a detailed answer, I post it here as well so there's no need for asking /
answering the same question again :)

#### How to control the vehicle from my code

Write a custom input script that gets a reference to the vehicle, then modify its input properties
as you wish: steerInput, throttleInput, brakeInput and handBrakeInput.

You can check out the scripts VehicleStandardInput.cs and VehicleRandomInput.cs script as examples
on how to control the vehicle with custom code.

#### Creating vehicles at runtime

https://mail.google.com/mail/u/0/#inbox/14f896e16632c70f

#### Match real-world cars

Edy's Vehicle Physics (EVP) is designed to allow configuring the vehicle's behavior with a few
parameters. These parameters don't have a correspondence with real world cars.

You can configure the vehicles in EVP to resemble the _feeling_ and behavior of actual cars.
Some hints:

Suspension and height of the center of mass
:	Set stiffer suspension, shorter suspension distances, and lower center of mass for sports cars.
	Softer suspension, larger suspension distances, and higher center of mass for family cars /
	pickup trucks.

Engine force and shape
:	More Max Drive Force and higher Force Curve Shape for high-acceleration sports cars. Less drive
	force and lower curve shapes for real street cars.

Max Speed Forward, Aerodynamic Drag, Rolling Friction
:	The combination of these define the final top speed on flat road.

Vehicle Balance
:	These settings define how the parameters are balanced among front and rear wheels. They may be
	used for compensating or enforcing certain behaviors on specific situations (example: move the
	brake balance to the rear wheels for enforcing oversteer on braking).

These parameters affect the handling and behavior:

- Accelerating and burnouts: Max Drive Slip, Drive Force To Max Slip, Traction Control.
- Braking and brake locks: Max Brake Slip / Ratio, Brake Force To Max Slip, Brake Assist.
- Steering: Max Steer Angle, Steering Limit, Steering Assist.

The longitudinal position of the center of mass has great influence on the handling and behavior as
well. A good practice is to ensure the suspension to be properly configured according to the weight
distribution caused by the CoM (i.e. stiffer springs where more weight is supported).

If you need to match the specifications of real cars accurately, then you should take a look at
[Vehicle Physics Pro](http://vehiclephysics.com). VPP is specifically designed to use real-world
specifications and simulate the actual behaviors of the cars based on their realistic setup.

#### Quicker turns, minimal sliding

https://mail.google.com/mail/u/0/#search/friction+anti-roll/1521a1780d403a51

#### Drift settings, indications

https://mail.google.com/mail/u/0/#inbox/15313411adc76d4f


---