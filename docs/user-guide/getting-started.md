# Getting started

**Welcome to Edy's Vehicle Physics!** The best vehicle kit for developing fun and realistic vehicles
in Unity 3D.

Import the package in the Unity Editor. You may either create an empty project, or import it into
any existing project (it's completely harmless). All content is imported into the folder EVP.

### The simplest scene

Load and play one of the demo scenes:

- **EVP \ The City - Simple Scene**: A standard street pickup truck.
- **EVP \ The City - Simple Scene - Drift**: A sports coupe configured for drifting.
- **EVP \ The City - Vehicle Manager**: Many vehicles in the scene each one configured in a different fashion.

(picture)

Play around with the vehicle. Check out the keys below:

Key                             | Function          | | Key                             | Function
------------------------------------|---------------|-|---------------------------------|-------------------
<kbd>left</kbd><kbd>right</kbd> | Steering          | |<kbd>R</kbd> 					| Repair vehicle damage
<kbd>up</kbd> 					| Throttle          | |<kbd>T</kbd> 					| Toggle slow time mode
<kbd>down</kbd> 				| Brake / Reverse   | |<kbd>P</kbd> 					| Pause vehicles. Camera and vehicle selection can be used while in pause.
<kbd>space</kbd> 				| Handbrake         | |<kbd>Y</kbd>, <kbd>shift-Y</kbd>	| Show / hide telemetry, change telemetry mode.
<kbd>enter</kbd> 				| Reset vehicle     | |<kbd>E</kbd> 					| Throws the gray stone in the air (useful for load tests)
<kbd>C</kbd> 					| Change camera     | |<kbd>Esc</kbd> 					| Reset scene
<kbd>Tab</kbd>, <kbd>Page up</kbd><kbd>Page down</kbd> | Select vehicle (Vehicle Manager scene)

### Vehicle components

The component providing the vehicle behavior is **VehicleController**. The vehicle in the scene
contains this component. The vehicle gizmo shows visual hints for the most relevant settings:

(picture)

- **Wheels:** references to the WheelCollider and assign wheel roles (steering, drive, brake...)
- **Center Of Mass:** position and height of the center of mass.
- **Vehicle Setup:** general settings on maximum speed, tire friction, stability, steering and aerodynamics.
- **Motor:** acceleration and wheel spin (_drive slip_) as for the drive power. Note! Traction Control limits the wheel spin.
- **Brakes:** braking force and allowed wheel lock (_brake slip_). Note! Brake Assist prevents the wheel lock.
- **Vehicle Balance:** front-rear balance configuring the vehicle handling in different situations.
- **Driving Aids:** make driving easier (or more difficult) in different aspects.

These settings configure the behavior of the vehicle and the gameplay in a variety of ways. Feel
free to play with the settings in Play mode and observe the effects on the fly.

VehicleController
:	The only component required for a vehicle to be a vehicle. Other vehicle components provide
	additional features and are optional. You may use them directly, or take them as base for
	writing your own.

VehicleAudio
:	Plays the audio effects: engine, transmission, wheel skid, impacts, wind... Note that the engine
	RPMs are calculated by this component just for audio, as VehicleController doesn't simulate
	the engine nor the gearbox.

VehicleDamage
:	Deforms the vehicle meshes and colliders on impacts.

VehicleStandardInput
:	Reads Unity standard Input and applies throttle, brakes, and steering accordingly.

VehicleRandomInput
:	Applies random input to the vehicle. It's a demonstrator of writing an custom input component.
	The green pickup truck in the Vehicle Manager scene contains this component.

VehicleTelemetry
:	Shows the numeric values from the vehicle in real time. Useful while configuring the vehicle.

VehicleVisualEffects
:	Provides visual effects such as the rotation of the steering wheel and the brake lights.

### Camera

The camera is a stand-alone GameObject containing the VehicleCameraController component and a
standard Camera component.

Note! The Camera component should be in a child GameObject for supporting VR properly.

(picture)

Check out the Camera Controller object in the demo scenes. A prefab _Camera Controller_ is included
with the controller and the camera ready to be used.

VehicleCameraController
:	Provides the different camera modes and the camera collision feature (prevents the camera to go
	through other geometry).

VehicleViewConfig
:	Add this component to the vehicle for specifying certain camera settings. VehicleCameraController
	looks for this component in the vehicle and apply the settings to the camera if present.


### Ground Materials

The Ground Material Manager is a stand-alone GameObject containing the GroundMaterialManager
component, and the components for drawing the tire marks (TireMarksRenderer) and the particle
effects (TireParticleEmitter). It manages the available ground materials for providing different
friction, drag, tire marks and particle effects on each ground type.

(picture)

Each ground material is bound to a specific PhysicMaterial in the scene. The parameters of the
physic material affect the impacts and the collider - collider interaction (friction, bouncing).
The associated ground material defines the properties applicable to the vehicle's wheels: grip,
drag, tire marks, particle effect.

Check out the Ground Material Manager object in the demo scenes. A prefab _Ground Material
Manager_ is included containing the ground material manager and a set of tire marks renderers and
tire particle emitters for the most common ground types (asphalt, offroad, sand, grass).

GroundMaterialManager
:	The list of ground materials available and their properties. Each ground material references a
	PhysicMaterial (or _None_ for affecting the colliders without a physic material), grip and
	drag coefficients, the surface type and the components for rendering tire marks and particle
	effects.

TireMarksRenderer
:	Component for drawing tire marks based on different parameters

TireParticleEmitter
:	Component providing the particle effects based on different emission parameters. Requires a
	standard ParticleSystem component for defining the particles.

VehicleTireEffects
:	Add this component to the vehicle for the tire marks and particle effects to work in the scene.
	It defines the vehicle's specific settings for tire marks and tire smoke.

### Multiple vehicles

You may include any number of vehicles in the scene, and manage them your way. The _Vehicle
Manager_ scene is an example of a simple vehicle management.

(picture)

VehicleManager is a simple component allowing the user to select among different vehicles. Controls
the vehicle's input (i.e. leaves unselected vehicles braked) and changes the camera's target to the
selected vehicle. You can also use VehicleManager as base for writing your own.

VehicleManager also demonstrates how to use a single VehicleStandardInput component for all
vehicles, instead of each vehicle having its own input component. Same with VehicleTelemetry.

---

Is everything clear here? Then head to "building scenes"!