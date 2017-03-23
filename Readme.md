This is not an official Google product.

This README describes the dataset used in the following publication:
Hamrick, J. B., Ballard, A. J., Pascanu, R., Vinyals, O., Heess, N., &
Battaglia, P. W. (2017). Metacontrol for Adaptive Imagination-Based
Optimization. In Proceedings of the 5th International Conference on Learning
Representations (ICLR 2017), available on [openreview](https://openreview.net/pdf?id=Bk8BvDqex).

This repository contains the following CSV files, two for each of the five
datasets corresponding to different numbers of planets:

* one-planet_train.csv
* one-planet_test.csv
* two-planets_train.csv
* two-planets_test.csv
* three-planets_train.csv
* three-planets_test.csv
* four-planets_train.csv
* four-planets_test.csv
* five-planets_train.csv
* five-planets_test.csv

Each row in these files corresponds to one scene, and each of these files
contains the following columns:

* x_ship -- the x coordinate of the spaceship
* y_ship -- the y coordinate of the spaceship
* vx_ship -- the x velocity of the spaceship
* vy_ship -- the y velocity of the spaceship
* mass_ship -- the mass of the spaceship
* radius_ship -- the radius of the spaceship
* x_planetN -- the x coordinate of the Nth planet, where N is the identifier of the planet (e.g. 0, 1, 2, etc.)
* y_planetN -- the y coordinate of the Nth planet
* vx_planetN -- the x velocity of the Nth planet
* vy_planetN -- the y velocity of the Nth planet
* mass_planetN -- the mass of the Nth planet
* radius_planetN -- the radius of the Nth planet
* gravity -- the gravitational constant (G), which can be thought of as what is essentially a weight scale
* damping -- the damping coefficient

To simulate from these scenes, we computed the sum of forces acting on the
spaceship from all the planets as well as a damping term (see Equation 9 in the
paper) and the used Euler integration to simulate forward. When calculating
forces, we accounted for one special case: If the spaceship was within the
radius of a planet, the force exerted by the planet on the spaceship was set to
a value as if the spaceship was just above the planet surface. We used an
integrator step size of 0.05 and ran simulations forward for 12 steps.

