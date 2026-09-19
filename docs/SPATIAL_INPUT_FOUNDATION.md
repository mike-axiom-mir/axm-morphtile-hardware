# MorphTile Spatial Input Foundation

Status: idea/foundation note — not implemented unless separately evidenced.

## Goal
Create a cheap, modular spatial input path for MorphTile using ordinary cameras and low-cost sensors rather than requiring proprietary VR hardware.

Hardware emits small inspectable state packets. MorphTile owns interpretation, interaction rules and world state.

## Initial tracking options
- Webcam hand tracking: existing camera, hand landmarks/pose.
- Camera + printed markers: cheap pose/identity assistance.
- Camera + LEDs: distinguishable LED patterns for camera-assisted tracking.
- IMU + Bluetooth LE: orientation/fast motion plus simple buttons/pinch/grab.
- UWB: optional later room-scale positioning; not required for v1.

## Device-neutral input
A first packet may resemble:

HandState {
  hand_id,
  position: { x, y, z },
  rotation,
  grab,
  pinch,
  buttons,
  confidence,
  timestamp
}

Illustrative only; not a frozen schema.

Tracking providers translate device-specific data into the common protocol. MorphTile consumes that protocol.

## Interaction examples
- move hand -> point/move
- pinch -> grab/select
- rotate hand -> rotate matter
- move hands together -> connect/assemble
- release -> place/confirm

Bindings are world/interface policy, not hardware truths.

## Interface-as-matter connection
Physical hardware is another compatible interface surface:
- button -> explicitly exposed action
- dial -> bounded parameter
- LED/display -> state presentation
- sensor -> input state
- actuator -> explicit output capability

Do not duplicate canonical state in the adapter. Do not grant arbitrary authority because a device is connected.

## Architecture
tracking providers / device adapters
-> common input/capability protocol
-> MorphTile interface/action boundary
-> canonical MorphTile matter/state

AI may be another caller/collaborator but is not required.

## Open-door requirement
Prefer inspectable adapters and simple hardware. Avoid mandatory proprietary headsets, cloud accounts, locked MorphTile hardware or hidden protocols. Third parties should eventually be able to build compatible adapters.

## Physical safety boundary
Actuators, motors, power systems and physical machines require explicit permissions, limits, fail-safe behavior and device-specific safety rules. A screen-safe action is not automatically safe as physical output.

## First prototype
camera OR IMU/BLE input
-> normalized HandState
-> MorphTile adapter
-> select/grab/move/release a harmless virtual tile
-> deterministic event/receipt
-> replay
-> clean disconnect

Combine tracking sources only when measurement shows value.

## Principle
Cheap sensors. Small packets. Open adapters. Canonical state stays in MorphTile. Build capability into the world, not complexity into the glove.
