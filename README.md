Background 

In this project I have implemented a simple simulator of an epidemic. In this model a person can have five states: 
Susceptible individuals can be infected with the disease. 
Exposed Individuals who have been exposed to the disease but are not yet infectious.  
Infected individuals can spread the disease to susceptible individuals they are in contact with. They will either recover from the infection or die as a result of the infection. 
Recovered individuals are free of the disease and cannot pass it on to others. We assume that recovered individuals are not susceptible to the disease any more. We can also class individuals who are not susceptible to the disease (for example because they have built up immunity as a result of an infection with a related pathogen) as recovered, as they cannot be infected with the disease either.  
After individuals have died from the infection their state will not change. Assume that the individuals live on a regular m × n grid, the first individual lives at (0, 0), the second at (0, 1), etc. with the (mn)-th individual living at (m − 1, n − 1). The speed at which the epidemic spreads depends on how much contact there is between infected individuals and susceptible individuals.

For this project we will assume that infected individuals do not reduce their contact with others. This can be the case if symptoms are only mild for the majority of cases and/or if individuals become infectious before they develop symptoms (though the latter would alter the dynamic a little).

Details 
Initial Conditions
For our initial conditions we will consider two cases: 
The location of the infectious individuals is known and given at the start of the simulation. 
Each individual is infected with a given probability. 

Known Locations 
For this case we will assume that all individuals are susceptible except for a number of individuals which are set to be infectious at the start of the simulation. 
The list of infectious individuals should be given as a list of locations.

Randomly Infectious For our random case, mathematically speaking, we will assume that at the begin of the simulation each individual is, independently of each other, either . . . 

infected with a probability of α_infected, 
exposed with a probability of α_exposed, 
has already recovered or is immune with a probability of α_recovered, or 
is susceptible to the disease with probability 1 − α_infected − α_recovered − α_exposed.


Contacts 

An important factor controlling how fast the disease spreads is the number of other persons each person is in contact with and also where these contacts are. In this simulation we will simulate who is in contact with whom using the following two parameters: 
Individuals can only be in contact with each other another if their distance on the grid is at most r. 
On average, each individual is in contact with k other individuals. Note: “Distance on the Grid” refers to the distance if we would need to walk to get from one location to another if we followed the grid. For example: 
the distance between (0, 0) and (1, 0) is 1 (i.e. one row), 
the distance between (0, 0) and (1, 1) is 2 (i.e. one row and one column), 
finally the distance between (0, 0) and (10, 15) is 25 (i.e. ten rows and fifteen columns).

Dynamics 

We assume that every day the probability that an infected person passes the disease to a susceptible person it is in contact with on that day is γ. Once they have the disease they become “exposed”. 

Each day an exposed person becomes infectious with probability ϕ. 

Each day an infected person will recover with a probability of βrecover or die from the infection with a probability of βdeath. The person will be infected for at least another day with a probability of 1 − βrecover − βdeath. 

One can show that the probability of dying of the infection is βdeath βrecover+βdeath and that, on average, individuals are infectious for 1 βrecover+βdeath days after being infected. A susceptible person who is in contact with an infectious person has thus a probability of γ βrecover+βdeath of being infected by that person.
