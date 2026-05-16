# PhysicsElaSim

A lightweight, custom 2D rigid body physics engine written from scratch in C#. It focuses on numerical stability, efficient impulse-based dynamics, and accurate multi-point contact resolution for arbitrary shapes.

## Key Features

* **Arbitrary Shape Dynamics**: Full physical representation of custom rigid bodies. Each body manages its own mass, inverse inertia, friction, and restitution (elasticity) parameters to simulate realistic material behaviors.
* **Multi-Point Contact Resolution**: Advanced contact manifold generation supporting multiple simultaneous contact points per collision. This ensures proper distribution of linear impulses and angular torques across complex overlapping geometries.
* **High Elasticity & Chain Stability (Newton's Cradle)**: Features a multi-pass velocity solver utilizing alternating directional iterations (forward-backward sweeping). This optimization eliminates energy loss and jitter during sequential rigid impacts, making high-elasticity scenarios—such as a perfectly functioning Newton's Cradle—highly stable and numerically accurate.
* **Energy-Efficient Sleeping System**: Automatically monitors body velocities and linear/angular energy thresholds over time. Stationary or low-energy objects are put to sleep to bypass costly integration and collision checks, and are dynamically re-awakened when a sufficient impact normal velocity is detected.

## Code Structure

* `World.cs` – Houses the core `FixedUpdate` simulation loop, handles force integration (gravity), updates body sleep timers, and coordinates the sequential impulse velocity/position resolution passes.
* `RigidBody.cs` – Defines the rigid state (position, rotation, velocity, and forces). Implements dirty flags for lazy geometry evaluation and features precise local impulse application.
* `Collision.cs` – Immutable data structure containing contact points, penetration depths, and collision normal vectors for a given body pair.

##
*Developed as a two-person collaborative project, utilizing VS Code Live Share for efficient real-time pair programming and remote teamwork.*
