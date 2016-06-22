# FAQ / How To

I'd better name this section "FAQ / OAC", including the Once Asked Questions. When I receive a
question that requires a detailed answer, I post it here as well so there's no need for asking /
answering the same question again :)

[TOC]

#### How to control the vehicle from scripting

Write a custom input script that gets a reference to the VehicleController component, then modify
its input properties as you wish: _steerInput_, _throttleInput_, _brakeInput_ and _handBrakeInput_.

You can check out the scripts VehicleStandardInput.cs and VehicleRandomInput.cs script as examples
on how to control the vehicle with custom code.

#### How to create vehicles at runtime

The order of events for creating vehicles at runtime is:

1. Create the root GameObject and disable it ([GameObject.SetActive](http://docs.unity3d.com/ScriptReference/GameObject.SetActive.html)(false))
2. Build the hierarchy with child GameObjects and components
3. Configure all the components and references. In particular, ensure that the _wheels_ list in
	the VehicleController component is populated properly.
4. Enable the root GameObject (GameObject.SetActive(true))

These properties cannot change while VehicleController is enabled

- Number of elements at VehicleController.wheels
- References to the WheelColliders in the wheel elements

#### Arcade cars: quicker turns, minimal sliding

These settings at the Vehicle Controller component turn most vehicles into arcade vehicles
a'la Mario Kart or Outrun:

- Tire Friction: 3
- Anti-roll: 0.9
- Force Curve Shape: 0.99

#### How to configure a car for drifting

A prefab **Sport Coupe Drift** is included. The key settings for configuring the drifting behavior
are:

- _Center Of Mass position_: slightly biased towards front, 0.55 - 0.60
- Large _Max Steer Angle_: 45-50 degrees
- Either rear drive wheels, or all wheel drive balanced 95% rear and 5% front (_Drive Balance_)
- Large _Max Drive Force_: around 5x the mass of the car (i.e. 5000 for a 1000 Kg car)
- Large _Max Drive Slip_: 11-13. **This is the key value for configuring _more_ or _less_ drifting**.
- _Handling Bias_: slightly oversteer, +5 - 10%
- _Traction Control_: disabled
- _Steering Assist_: enabled, 0.6 - 0.8

#### How to match real-world cars

Edy's Vehicle Physics (EVP) is designed to allow configuring the vehicle's behavior with a few
parameters. These parameters don't have a correspondence with real world parameters.

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

- Accelerating and burnouts: Max Drive Slip, Drive Force To Max Slip, Traction Control, Drive
	Balance.
- Braking and brake locks: Max Brake Slip / Ratio, Brake Force To Max Slip, Brake Assist, Brake
	Balance.
- Steering: Max Steer Angle, Steering Limit, Steering Assist, Handling Bias.

The longitudinal position of the center of mass has great influence on the handling and behavior as
well. A good practice is to ensure the suspension to be properly configured according to the weight
distribution as for the the CoM position (i.e. stiffer springs where more weight is supported).

You can also start with one of the included prefabs. Choose the one that is most similar to the
vehicle you want to resemble. Then carefully configure the parameters in order to fine tune the
handling and behavior.

If you need to match the specifications of real cars accurately, then you should take a look at
[Vehicle Physics Pro](http://vehiclephysics.com). VPP is specifically designed to use real-world
specifications and simulate the actual behaviors of the cars based on their realistic setup.

---