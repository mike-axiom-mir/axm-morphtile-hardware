# AXM MorphTile Hardware

Experimental hardware/input bridge for MorphTile.

Goal: let inexpensive, replaceable hardware expose bounded input/output capabilities to MorphTile without making MorphTile depend on any particular device.

Initial direction:
- camera/webcam hand tracking
- printed markers
- LED-assisted tracking
- IMU + Bluetooth LE
- buttons / pinch / grab inputs
- optional future UWB positioning
- displays, lights, controls, sensors and actuators through explicit adapters

Core rule: **hardware measures; MorphTile interprets.**

This repository sits beside MorphTile. MorphTile core must remain usable without this repository.
