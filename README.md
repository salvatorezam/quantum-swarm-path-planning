# quantum-swarm-path-planning



We implement the pseudocode:

 \begin{algorithm}
 \caption{joint approach pseudocode}
 \begin{algorithmic}[1]
\State initialize robots' positions as state superpositions
\State evaluate individual rewards
\If {all rewards are below a certain threshold}:
  \State randomly reshuffle positions
  \For {each robot}:
  \State reach each new position through the path planning
  \EndFor
  \EndIf
 \State find the robot with the highest reward and let it enter the circuit
 \State find the new suggested position through the circuit
 \For {all robots}:
 \State reach the new positions through the path planning
  \State evaluate the new rewards
 \EndFor
 \end{algorithmic}
 \end{algorithm}
 
...these steps allow a swarm of about N = 10 robots to reach the target. With less robots, we might need more steps:
the passages can be repeated in a loop, and an additional command `Reach the robot with the highest target' can be used, to force convergence.
In this algorithm, the only non-quantum passage is the reshuffling step.
 
This code is working in a 2D scenario. The same ideas can be extended to a 3D scenario.
The path planning step requires a division of the arena into a 2x2 matrix, where each element is a macro-cell.
Each macro-cell can be divided into a 2x2 matrix, where each element is a micro-cell.
The more the subdivisions, the smoother the path.
 
Obstacles can be easily added considering one or more cells unaccessible, and thus excluding their portions of space from any possible path.
 
