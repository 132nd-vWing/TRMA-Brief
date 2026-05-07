# Range Drones
ver 2.3

The new range drone system is released for the following Ranges: 

Range 21
Range 22
Range 23
Range 31
Range 32
Range 33

NOTE: A2A drones are not smart, and do better with an AWACS close by. 

## Air 2 Air Advesary Script Function

The controlling script is singular and modular in that it is reused by each range. Therefore any range could have an A2A Averasy option. 

## Drone units
The system currently includes: 
- MIG23MLD (*APU602M*, R24R)
- MIG29A (*R60M*, R73, R27R)
- SU30 (*R73*, R77, R27ER)
- JF17 (*PL-5EII*, SD10-A)
- MIG25PD (*R40TD*, R40RD)
- MIG31 (*R73*, R77, R29ER)
- SU27 (*R73*, R27ET, R27ER)
- J11A (*R73*, R27ER, R77)

\* *italics* shows the BFM load  

## Control
Select mode **BVR** or BFM  
This defines the load and max detection range of the drone groups.  
BVR max detection range ~120nm.  
BFM max detection range ~30nm. 

Groups 1 & 2 allow the configuration of your required engagement airframes that can be configured through the Group Config Menu even before you leave the ground. 

## Enemy ROE
- Drones groups execute a CAP mission in the vacinity of their spawn zone when they are first spawned. 
- Drones will only engage targets inside their range.
- Red AWACS greatly improves the drone detection capability. 
- Max detection range is the possible maximum range that targets are detected.
- Engagement range is not configurable. (see note)
- Drone skill is set to "good", "avergae was too easy".

*Note: the engagement range is defined as maximum range in the drone templates, but their skill is set to "good" else they are impossible to beat, the side effect is that lower skilled drones engage closer. There is no way around this.*

## Zone Violation
- Drones will disengage only when **they** leave the range. 
- When drones disengage they will return to their spawn zone. 
- Drones will remain disengaged until re-entering their spawn zone, where they will reactivate their target search. 


![Locations](../GRAPHICS/TRMA_A2A_Zones.PNG)

[Back to frontpage](https://132nd-vwing.github.io/TRMA-Brief/)
