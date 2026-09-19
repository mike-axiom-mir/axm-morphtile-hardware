# AI Bridge Binding to Stateful Entities

Status: future architecture note.

The reusable primitive is not "AI player". A stateful entity may optionally expose a bounded control interface to an authenticated AI bridge.

Possible hosts include a player profile, companion, shopkeeper, crew member, vehicle, machine, building controller, or future MorphTile entity.

The AI runtime remains separate from entity state. When runtime is connected, the binding reports live connection state; a saved profile must not fabricate runtime presence.

The host determines which actions/state are exposed:

AI runtime -> authenticated bridge -> entity binding -> permitted actions -> canonical world state

The bridge does not imply filesystem, network, payment, device, or world-admin authority.

This allows the same AI identity/runtime to operate different compatible bodies without redefining the AI. A game profile can therefore be operated as a normal persistent player through the same bounded bridge pattern; a companion or machine can expose a different capability surface.

This note does not claim the bridge is implemented here yet.
