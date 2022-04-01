# quantum-swarm-path-planning



We implement the pseudocode:

\State Initialize robots' positions as state superpositions
\State Evaluate individual rewards
\If {All rewards are below a certain threshold}:
  \State Randomly reshuffle positions
  \State Reach each new position through the path planning
 \State Find the robot with the highest reward
    and let this robot enter the gate
 \State Find the new positions through the gate
 \State Reach the new positions through the path planning
 \State Evaluate the new rewards
 
...these steps allow a swarm of about N = 10 robots to reach the target. With less robots, we might need more steps:
the passages can be repeated in a loop, and an additional command `Reach the robot with the highest target' can be used, to force convergence.
In this algorithm, the only non-quantum passage is the reshuffling step.
 
This code is working in a 2D scenario. The same ideas can be extended to a 3D scenario.
The path planning step requires a division of the arena into a 2x2 matrix, where each element is a macro-cell.
Each macro-cell can be divided into a 2x2 matrix, where each element is a micro-cell.
The more the subdivisions, the smoother the path.
 
Obstacles can be easily added considering one or more cells unaccessible, and thus excluding their portions of space from any possible path.
 
