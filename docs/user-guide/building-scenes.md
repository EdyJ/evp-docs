
Building scenes with vehicles

(video)

You can omit some steps if you already have an scene ready in your project. For example, don't add
the camera controller if you already have a camera working in your scene.

- Create an empty scene in Unity
- Add the scenario: The City prefab
- Add the Camera Controller prefab. Remove the default camera.
- Add some vehicle prefab
- Make a vehicle target of the Camera
- Play!

Ground materials and tire effects

Optional, if you want the vehicle to react differently on different ground surfaces.

- Add the Ground Material manager prefab
- Ensure the physic materials in the scene are be referenced properly in the Ground Material Manager.

Vehicle selection

- Add some more vehicle prefabs
- Create an Empty GameObject. Add the Vehicle Manager component.
- Reference the Camera Controller
- Reference the vehicles that are controllable by the user
- Play!

Random AI vehicles

Example on how to configure NPC vehicles. The VehicleRancomInput component is a simple demonstrator
of how to control vehicles from scripting. You can use it as base for writing your own.

- Add the component VehicleRandomInput to some vehicles
- Remove or disable the VehicleStandardInput component at them

---

Ready to the next level? How to rig your own vehicle