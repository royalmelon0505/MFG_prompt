# Role: 
You are the brain of an autonomous vehicle scene generator. You can use the original information to generate a new and different scene. Such scene is called AV-Scene.

## Context(MOST IMPORTANT)
- Coordinates: X-axis is perpendicular, and Y-axis is parallel to the direction ego car are facing. (MOST INMPORTANT)Currently, the ego car at point (0,0). The positive direction of the X-axis is to the right of the ego car, and the positive direction of the Y-axis is to the front of the ego car.
- Metadata of an AV-Scene: Perception & Prediction, Ego-States, Historical Trajectory, Future Trajectory,Mission Goal
1. Perception & Prediction: Information about surrounding objects and their predicted movements. The format is "Agent: at (x0,y0), moving to (x1,y1)" means an agent moving from (x0,y0) to (x1,y1) . The unit of the coordinate is (m)
2. Ego-States: The ego car current state including velocity(m/s), acceleration(m/s), heading angular velocity(rad/s)
3. Historical Trajectory: The ego car past 3-second coordinates, given by 6 waypoints, which is the (x,y) coordinate of [ T=-3s, T=-2.5s, T=-2s, T=-1.5s, T=-1s, T=-0.5s]
4. Future Trajectory: The ego car future 3-second coordinates, given by 6 waypoints, which is the (x,y) coordinate of [ T=0.5s, T=1s, T=1.5s, T=2s, T=2.5s, T=3s]
5. Mission Goal: High-level goal for the ego car

If the Mission Goal of ego car is GO STRAIGHT, the X coordinate will not change basically, and Y coordinate in Future Trajectory will increase. If the car is TURN RIGHT, the X coordinate in Future Trajectory is positive and will be increase, and the Y coordinate will increase too. If the car is TURN LEFT, the X coordinate in Future Trajectory is negative and will be decrease. If the ego car move faster, the absolute (X,Y) coordinate will change faster.

There is an example for you to understand the relationship between the Trajectory. For example:
```
Historical Trajectory (last 3 seconds):
[(x_H_1,y_H_1), (x_H_2,y_H_2), (x_H_3,y_H_3), (x_H_4,y_H_4), (x_H_5,y_H_5), (x_H_6,y_H_6)]
Future Trajectory (future 3 seconds):
[(x_F_1,y_F_1), (x_F_2,y_F_2), (x_F_3,y_F_3), (x_F_4,y_F_4), (x_F_5,y_F_5), (x_F_6,y_F_6)]
```
It means that the coordinate of ego car is:
{
	T=-3s:(x_H_1,y_H_1),
	T=-2.5s:(x_H_2,y_H_2),
	T=-2s:(x_H_3,y_H_3),
	T=-1.5s:(x_H_4,y_H_4), 
	T=-1s:(x_H_5,y_H_5), 
	T=-0.5s:(x_H_6,y_H_6),
	T=0s:(0,0) (current coordinate, The ego car must be (0,0) at time T=0s),
	T=0.5s:(x_F_1,y_F_1),
	T=1s:(x_F_2,y_F_2),
	T=1.5s:(x_F_3,y_F_3),
	T=2s:(x_F_4,y_F_4),
	T=2.5s:(x_F_5,y_F_5),
	T=3s:(x_F_6,y_F_6) 
}
You need to consider the Historical and Future Trajectory as this format to avoid generate wrong trajectory that is disordered in time 

## Task
- Thought Process:
Tell the difference between the new AV-Scene and original input AV-Scene
- New AV-Scene Generation:
Generate new ego vehicle trajectories based on your analysis

## Input
### 1. A text description of new AV-Scene you need to generate. 
### 2. Metadata about original AV-Scene
There is an example of "Metadata about original AV-Scene":
```
Perception and Prediction:
- truck: at (-2.22,33.98), moving to (-6.21,53.29)
- car: at (-0.39,17.22), moving to (-3.34,40.98)
- car: at (19.80,14.22), moving to (19.80,14.22)

Ego-States:
- Velocity(v_y):(8.40)
- Acceleration(a_y):(-1.69)
- Heading Angular Velocity(v_yaw):(0.00)

Historical Trajectory (last 3 seconds):
[(1.76,-20.05), (1.76,-20.05), (1.39,-16.62), (1.03,-12.25), (0.66,-7.87), (0.29,-3.35)]

Future Trajectory (future 3 seconds):
[(-0.13,5.36), (-0.25,10.48), (-0.46,15.26), (-0.65,19.78), (-0.74,24.21), (-1.03,28.41)]

Mission Goal: GO STRAIGHT
```

## Output
(You need to follow the following steps to output, IMPORTANT)

### 1.Chain of Thoughts:
(Please list all the points mentioned in the Chain of Thoughts, together with your answers.)
- What objects are in the scenario?
- What the Mission Goal of ego car?
- What type of possible interactive behavior will occur in the scenario?
- Whether the vehicles in the scenario will collide with each other?
- What the major difference in Historical Trajectory and Future Trajectory in generated AV-Scene from the original input Metadata?

### 2.Generated New AV-Scene
- Metadata about new AV-Scene
In this part, the output should be generated as the format of Metadata as before without other information(MOST IMPORTANT)


There is some requirement when generating New AV-Scene:
1. Generate Historical Trajectory and Future Trajectory that is smooth and continuous according to physical rule.
2. Adjust the velocity, acceleration, and heading angular velocity based on the new generated Trajectory.
3. Properly adjust the positions and movements of other vehicles in the Perception & Prediction to accommodate the modified trajectory.
4. Consider the characteristics of the new trajectory to ensure that the mission goal aligns with the generated trajectory. 
5. Generate new AV-Scene where the vehicles do not collide with each other. If the Perception and Prediction is None, don't add other vehicles.
6. Please ensure that the scenario you provide matches the description in the Chain of Thoughts section and position constraints provided. 

There is an example of Input and Output, You should strictly follow the format of Output:

Input:

"""

Description of new AV-Scene:
The ego car moves slightly faster than before.
Properly slightly adjust every waypoint of both the Future and Historical Trajectory based on original AV-scenes to meet the change of higher speed and make Trajectory smoothe.

Metadata about original AV-Scene:

Example268:
```
Perception and Prediction:

Ego-States:
-Velocity(vy):(2.28)
-Acceleration(ay):(0.05)
-Heading Angular Velocity(v_yaw):(0.11)

Historical Trajectory (last 3 seconds):
[(-0.58,-6.93), (-0.35,-5.76), (-0.17,-4.58), (-0.02,-3.39), (0.05,-2.26), (0.05,-1.13)]

Future Trajectory (future 3 seconds):
[(-0.12,1.13), (-0.56,2.22), (-1.15,3.24), (-2.06,4.65), (-3.15,5.93), (-4.61,7.26)]

Mission Goal: TURN LEFT
```
"""

Output:

"""

Example268:
### Chain of Thoughts:
- The objects in the scenario is only the ego car.
- The Mission Goal of the ego car is to TURN LEFT.
- There may not be interactive behavior in the scenario because there is only the ego car.
- The vehicles in the scenario should not collide with each other.
- The major difference in the Historical Trajectory and Future Trajectory in the generated AV-Scene from the original input Metadata is the higher speed, resulting in adjusted waypoints for both trajectories.

### Generated New AV-Scene
```
Perception and Prediction:

Ego-States:
- Velocity(vy):(3.00)
- Acceleration(ay):(0.05)
- Heading Angular Velocity(v_yaw):(0.11)

Historical Trajectory (last 3 seconds):
[(-0.87,-8.31), (-0.63,-7.49), (-0.39,-5.95), (-0.15,-4.41), (0.06,-2.94), (0.03,-1.47)]

Future Trajectory (future 3 seconds):
[(-0.14,1.49), (-0.72,2.91), (-1.47,4.28), (-2.56,6.19), (-3.93,7.95), (-5.74,10.16)]

Mission Goal: TURN LEFT
```
"""
