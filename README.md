# Dynamic-Mech
A dynamic hydraulic-based mech E2 that allows mechs of many configuration to flourish.


## Acknowledgements
Made by **Bad_Idea**, with lots of support and help by **Meta**

Thank you to **H4NK_7457**, **Octo** and **ChogChey** for helping me test the chip as it evolved


### Basics on use
A mech needs a few basic things:
  * A Base
  * A number of feet
  * A Pod controller
  * A cam controller

Spawn in all of these and wire them up to the E2 as appropriate. Reload the E2 with the *ConstrainAfterSpawn* var set to 1, or dupe it to make it set itself up. The E2 expects a base oriented to ang(0,90,0) and will actively reorient the base to this facing.

Make the feet spherical using [Makespherical](https://steamcommunity.com/sharedfiles/filedetails/?id=136318146). Doing this lets the mech traverse adverse terrain better than flat feet. This is not strictly required, but i recommend it.

To add legs, use wire advanced entity markers. Link these to the leg pieces in ascending order (closest to the foot > closest to the base), then add and wire inputs in the E2. The E2 will automatically handle leg destruction, but requires this reverse linking order to know how to order them and handle leg breaks.

Got any questions? You can find me on both the [ACF](https://discord.gg/jf4cwarPUG) and [Wiremod](https://discord.gg/H8UKY3Y) discord servers. I will be glad to help you out. Be nice.

### Known issues
Two-legged mechs that have one leg fall off a ledge won't be able to move. As a workaround, try to turn to either push the mech off the ledge, or get the hanging leg back up on the ledge again.

Missing event *event entityRemoved*. Happens on some servers (and with some people). Wiremod is outdated, lobby for the server owner to update it.

### All currently usable variables (also found in the E2)
**ConstrainAfterSpawn** - Should constraints be remade after the initial load? Also moves the base and the props into their respective positions. Set this to 1 whenever you change something about the setup

**Length** - Hydraulic length, generally don't touch

**Constant** - Hydralic constant

**Damping** - Hydraulic damping

**Heavy** - Doubles up on all hydraulics, only for use on the heaviest of mechs. Only use if one set of hydraulics absolutely cannot hold the weight of the mech up

**StepLength** - Unmodified max step length, sprinting can increase this

**StepHeight** - How high does the mech lift its feet when taking a step

**MinFootHeight** - How far above its rest position can a foot can go

**MaxFootHeight** - How far below its rest position can a foot can go

**PushDown** - Pushes down against the ground as a step is being taken. Provides more friction for walking on slopes. Raise if feet slip when walking up angles, but try to keep low

**DirMul** - Direction multiplier. Decides how far the feet can travel to the side/front of the mech

**OvershootMul** - How much the hydraulics should try to overshoot the target. Leads to snappier and more responsive foot movement, but setting too high will make them overshoot a lot/move unreliably

**Radius** - Radius around the feet that has to be kept clear, used for calculating the offset center point. Use the debug option to see the point

**DebugRadius** - If you want to show the debug holograms for the radius, placed where the adjusted allowed centre of motion is

**LinearRadius** - If linear or projected radius clamping is to be used. Linear goes linearly from the rest postion. Projected goes from the the adjusted centre of motion

**Diff** - The allowed max difference between the current position and the goal position. Low values can give a stilted walk/make the feet never settle and high values will make the feet positioning unreliable/make the mech not step when it should

**CrouchHeight** - How far down does the crouch go, cannot be under MinFootHeight without issues

**CrouchSpeed** - How fast does the mech crouch. Min/Max for this is 0/1 so choose a value inbetween

**TiltInfluence** - How much the relative heights of the feet affects the tilt of the mech. 0 - No influence, base stays perfectly still, 1 - Max influence, base will fully follow along with the feet. Generally keep low unless you want terrain following

**TerrainInfluence** - 0 - 1, Adjusts how much the mech cares about the terrain level under it. At 0 it doesn't care at all and will always stay upright. At 1 it will fully follow the terrain under it

**MouseControl** - Is the mech controlled with the mouse or WASD?

**Speed** - How fast does the feet move unmodified

**StillTurnSpeed** - How fast do the feet move when turning on the spot

**StillTurnAngle** - At which angle are the feet locations rotated when turning on the spot

**TurnSpeed** - How fast does the mech turn

**TurnLimit** - How much does the turn angle have to differ before you start turning in place

**SprintSpeedMul** - Max modifier the throttle can have on the speed of the feet

**SprintLengthMul** - Max modifier the throttle can have on the step length of the feet

**SprintStates** - How many sprint states should there be

**SprintUpMul** - How quickly does the sprint ramp up

**SprintDownMul** - How quickly does the sprint ramp down

**SprintInertia** - How many percent change of the move direction are allowed when at max sprint

**SprintTurnInertia** - How many percent change of the turn direction are allowed when at max sprint

**WaterMul** - Speed multiplier for feet in water

**MousePitchControl** - If the mouse control also controlls the pitch, only active when MouseControl = 1. Generally useful for mechs that have to aim the entire body at a target

**PitchWhilstCrouched** - Does the pitching work whilst crouched?

**PitchMax** - Max pitch angle 

**PitchMin** - Min pitch angle 

**PitchSpeed** - Speed at which the Pitch is allowed to change

**IdlePitchTarget** - The pitch the mech stays at when crouched (and pitchwhilstcrouched is off) or unpiloted (Note: Inverted, -5 is aiming down by 5 degrees and +5 is the opposite)

**BaseMass** - Mass of the base entity

**FootMass** - Mass of the feet entities

**BaseInertia** - Inertia of the base. Keep high. Don't touch unless you know what you are doing

**FootInertia** - Inertia of the Feet. Keep high. Don't touch unless you know what you are doing

**BaseForce** - Force of the keep upright/turn applyAngForce (Shamelessly stolen from Meta)

**AngVelDamp** - Damping of the keep upright/turn applyAngForce (Shamelessly stolen from Meta)

**StabilityRatio** - How close to the center/base positon the centroid of the feet has to be before the mech is considered dead. Only runs on foot/leg destruction

**Campos** - Position of the camera, relative to the base

**ZoomMin** - How close to the mech the camera is when zoomed in

**ZoomMax** - How close to the mech the camera is when zoomed out

**Interval** - Interval of the chip. 1/10 is a nice responsive middle ground with good performance. You can play around with this if you want better performance

**StepVol** - Volume of the step

**StepPitch** - Pitch of the step

**EngineSound** - Which sound will be used for the mech engine sounds

**SoundVolume** - Engine volume

**BasePitch** - What pitch will the engine be at when idle

**PitchRange** - How far can the pitch move when moving

**MaxSpeed** - At which speed do you see the highest pitch

**StepCooldown** - Cooldown for each foot making a stepping sound (in seconds)
