## Description of Metrics
[comment]: <> (RH: Really cool idea for a project)

Nasa's Center for Near Earth Object Studies (CNEOS) continues to grow as Congress allocates more funding to this division of NASA. Included in this are two major projects. The NEO Surveillance Mission and the Asteroid Redirection Test program. The Surveillance Mission continues to actively detect these NEOs or near earth objects, which are asteroids 99.9% of the time, and gather data on parameters such as size, orbit, and distance. This surveillance is what enables NASA to determine which asteroids could be of any danger to Earth. The Asteroid Redirection Test program, which will be attempting it's first redirection this September of 2022, aims to launch a spacecraft into the trajectory of the asteroid to change it's orbit accordingly.

[comment]: <> (RH: Will you use any physical parameters such as mass, velocity, or rotational forces? It may be interesting to simualte a curve based using CF below to understand ranges not feasible for redirection / alternate strategy.)
For the sake of this project I'll assume the Asteroid Redirection program will be fully functional and ready to be deployed when a hazardous asteroid has been identified. I'm going to assume that the NEO Surveillance Mission, which is a satellite that is constantly monitoring asteroid activity near Earth, has been launched and is orbiting Earth for $10M and requires no maintenance for the forseeable future. I'm then going to assume that it costs $5M to deploy the Asteroid Redirection Spacecraft for each asteroid that is considered to be hazardous to Earth. When a hazardous asteroid isn't accurately predicted, I'll assume an emergency mechanism exists costing $100M per asteroid to quickly launch some sort of spacecraft for a last minute redirection. It would be next to impossible to calculate potential damages to Earth if an asteroid actually hit us.

### Confusion Matrix

Positive = Hazardous<br>
Negative = Non-hazardous

- True Positive
    - We predict an NEO is hazardous and it is hazardous
    - Initial $10M for surveillance plus $5M for each redirection.
- False Positive
    - We predict an NEO is hazardous but it is not hazardous
    - Initial $10M for surveillance plus $5M for each unnecessary redirection.
- False Negative
    - We predict an NEO is not hazardous but it is hazardous
    - Initial $10M for surveillance plus $100M emergency funding for each asteroid due to not detecting the hazardous asteroid early enough!
- True Negative
    - We predict an NEO is not hazardous and it is not hazardous
    - Initial $10M for surveillance.

### Example using 1000 datapoints

- True Positive where N = 50
    - $10M + $5M(50) = $260M
- False Positive where N = 50
    - $10M + $5M(50) = $260M
    - This wrong prediction has cost us $260M - $10M = $250M
- False Negative where N = 10
    - $10M + $100M(10) = $1.1B
    - This wrong prediction has cost us $1.1B - $260M - $10M = $830M
- True Negative where N = 890
    - $10M


### Summary

In summary, the worst case scenario is a false negative where we incorrectly predict an NEO to be safe and it becomes hazardous to Earth which would cost $100M per asteroid. As seen in the example, even if only 1% of our predictions are a false negative it can be extremely costly! We can assume the 10,000,000 + 5,000,000(N) formula, where N is the number of asteroids needed to be redirected, for instances where a hazardous asteroid is predicted (no matter True or False). We have no extra or unaccounted for costs when the true positive and true negative instances occur. Of course, the true positive costs more, but it is accounted for with our correct prediction.
