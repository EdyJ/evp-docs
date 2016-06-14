
## Edy's Vehicle Physics

---

Edy’s Vehicle Physics brings realistic and fun vehicles to your games in [Unity 5](http://unity3d.com)!
Designed for gameplay, ease of use, and realistic behavior.

Stay tunned! Follow **[@VehiclePhysics](https://twitter.com/VehiclePhysics)** on Twitter for the
latest news and announcements.

---

### FAQ

I'd better name this section "FAQ / OAC", including the Once Asked Questions. When I receive a
question that requires a detailed answer, I post it here as well so there's no need for asking /
answering the same question again :)

#### Using my own input / controlling vehicle with custom code

The best solution is is writing a custom input script. You can check out the scripts
VehicleStandardInput.cs and VehicleRandomInput.cs script as examples on how to control the vehicle
with custom code.

#### Creating vehicles at runtime

https://mail.google.com/mail/u/0/#inbox/14f896e16632c70f

#### Match real-world cars

Edy's Vehicle Physics (EVP) is designed to allow configuring the vehicle's behavior with a few
parameters. These parameters haven't a correspondence with real world cars.

You can configure the vehicles in EVP to resemble the _feeling_ and behavior of actual cars.
Some hints:

- Suspension and height of the center of mass. Set stiffer suspension, shorter suspension distances,
and lower center of mass for sports cars. Softer suspension, larger suspension distances, and higher
center of mass for family cars / pickup trucks.

- Engine force and shape. More Max Drive Force and higher Force Curve Shape for high-acceleration
sports cars. Less drive force and lower curve shapes for real street cars.

- Max Speed Forward and Aero Drag. The combination of both define the final top speed on flat road.

These parameters affect the handling and behavior:

- Accelerating and burnouts: Max Drive Slip, Drive Force To Max Slip, Tc Enabled / Tc Ratio.
- Braking and brake Locks: Max Brake Slip / Ratio, Brake Force To Max Slip, Abs Enabled / Abs Ratio.
- Steering: Max Steer Angle, Esp Enabled / Esp Ratio.

The longitudinal position of the center of mass has great influence on the handling and behavior as
well. A good practice is to ensure the suspension to be properly configured according to the weight
distribution caused by the CoM (i.e. stiffer springs where more weight is supported).

If you need to match the specifications of real cars accurately, then you should take a look at
[Vehicle Physics Pro](http://vehiclephysics.com). VPP is specifically designed to use real-world
specifications and simulate the actual behaviors of the cars accurately.


#### Quicker turns, minimal sliding

https://mail.google.com/mail/u/0/#search/friction+anti-roll/1521a1780d403a51


#### Drift settings, indications

https://mail.google.com/mail/u/0/#inbox/15313411adc76d4f

---