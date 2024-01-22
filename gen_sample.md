## Input:

**Description of new AV-Scene:**

<font color=Red>I hope the ego car can move faster</font>


**Metadata about original AV-Scene:**

'''

Perception and Prediction:
- car: at <font color=Blue>(0.74,10.89)</font>, moving to <font color=Blue>(0.84,22.13)</font>
- truck: at <font color=Blue>(0.56,37.25)</font>, moving to <font color=Blue>(-0.39,60.77)</font>
- car: at <font color=Blue>(0.73,23.43)</font>, moving to <font color=Blue>(1.03,39.96)</font>

Ego-States:
- Velocity(vy):<font color=Blue>(6.79)</font>
- Acceleration(ay):<font color=Blue>(-1.30)</font>
- Heading Angular Velocity(v\_yaw):<font color=Blue>(0.14)</font>

Historical Trajectory (last 3 seconds):

[<font color=Blue>(-4.36,-26.15), (-3.17,-20.79), (-2.05,-15.75), (-0.99,-11.04), (-0.11,-7.11), (0.03,-3.39)</font>]

Future Trajectory (future 3 seconds):

[<font color=Blue>(-0.35,3.05), (-0.44,5.81), (-0.59,8.59), (-0.67,10.69), (-0.41,12.99), (-0.20,14.96)</font>]

Mission Goal: <font color=Blue>GO STRAIGHT</font>

'''

## Output:

### Chain of Thoughts:
- The objects in the scenario are cars and a truck around the ego car.
- The Mission Goal of the ego car is to GO STRAIGHT.
- There could be interactive behavior in the scenario as there are multiple other vehicles present.
- The vehicles in the scenario should not collide with each other.
- The major difference in the Historical Trajectory and Future Trajectory in the generated AV-Scene from the original input Metadata is the increased speed of the ego car, resulting in adjusted waypoints for both trajectories.

### Generated New AV-Scene:

''' 

Perception and Prediction:
- car: at <font color=Blue>(0.77,12.09)</font>, moving to <font color=Blue>(0.95,24.49)</font>
- truck: at <font color=Blue>(0.62,36.79)</font>, moving to <font color=Blue>(-0.37,60.33)</font>
- car: at <font color=Blue>(0.78,23.76)</font>, moving to <font color=Blue>(1.32,40.57)</font>

Ego-States:
- Velocity(vy):<font color=Blue>(8.00)</font>
- Acceleration(ay):<font color=Blue>(-1.30)</font>
- Heading Angular Velocity(v\_yaw):<font color=Blue>(0.14)</font>

Historical Trajectory (last 3 seconds):

[<font color=Blue>(-4.97,-29.78), (-3.61,-23.54), (-2.33,-17.91), (-1.11,-12.48), (-0.16,-8.00), (0.22,-4.80)</font>]

Future Trajectory (future 3 seconds):

[<font color=Blue>(-0.68,6.05), (-0.85,9.23), (-1.14,12.99), (-1.29,16.11), (-0.78,19.40), (-0.41,22.34)</font>]

Mission Goal: <font color=Blue>GO STRAIGHT</font>

'''
