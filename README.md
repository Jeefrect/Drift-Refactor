# Drift Refactor
This mod adds a physically based model of tire temperature, wear, and grip for drift mode.

The system simulates how rear tires heat up from friction and load, how grip evolves across temperature ranges, and how excessive heat and wear reduce performance or lead to tire failure.

# Features
- Decel light system like the Formula Drift in real life.
- Dynamic tire heating from sliding, longitudinal, and vertical loads.
- Tire cooling based on the difference in air temperature.
- Temperature zone for drifting with a gradual increase in grip as the tire reaches certain temperatures.
- Overheating with a loss of grip, Fire, and Explosion states.
- Tire wear affecting maximum traction.
- Full integration with car and wheel physics.
- Display of temperature, grip, wear, and status in the HUD, dynamic notifications.
- Synchronization between players.
- Tire fix zone.
  
# Temperature Logic
Tire temperature is calculated every carx physical tick. Taken into account:
- Skid
- Longitudinal load
- Vertical load
- Overall session heat factor
- Air temperature

Heating and cooling are balanced so that the tire reaches its operating range gradually, rather than over several seconds.

# Adhesion
Adhesion depends on temperature and wear:
- Cold tires provide reduced grip.
- Grip gradually increases as the tire reaches operating temperature.
- Maximum grip is achieved within an extended optimal temperature range.
- After overheating, grip decreases.
- In the Fire state the grip decreases.

# Tire Wear
Tire wear increases from:
- Slip
- Load
- Elevated temperature

Wear reduces maximum achievable grip and is clamped between 0% and 100%.

# Tire States
- Normal - standard operation
- Fire - critical overheating, grip penalty applied
- Explosion - tire destruction
Threshold values are configurable in the session context.
