## 1. What part of your phenomenon would you like to build a model of?  Make sure that the phenomenon is appropriate for an agent-based model that could be completed in the next month.

I would like to build a model of certain slime moulds (*Physarum polycephalum*). In particular, I am interested in their ability to optimally solve mazes in search for food (you can see the mould in action and read about its behaviour [here](https://www.scientificamerican.com/article/brainless-slime-molds/)).

This phenomenon is particularly suited for ABM since the colony/organism has no central control system and the nuclei that compose it have no global information, but the colony as a whole does behave as if it did.

I would like to demonstrate that this kind of behaviour is possible with only one type of agent and (arguably) a proto-agent, following very simple rules. This demonstration would have no ambition towards literal biological realism, but I hope to produce a simulated behaviour which would look similar to that of the mould for a human observer.

## 2. What are the principal types of agents involved in this phenomenon?  Illustrate all of the agent types necessary for the model.

The only type of agent is a **particle** of slime mould.

A proto-agent representing **slime** will also be present. Tiles converted to **slime** will slowly expire and convert back to standard tiles.

## 3. What properties do these agents have (describe by agent type)?  Describe for all agent types.

The only property of a particle is **energy**. Energy allows the particle to move. Once the energy level reaches 0, the particle "dies".

**Slime** is created in the wake of **particles**, and expires after a given number of ticks.

## 4. What actions (or behaviors) can these agents take (describe by agent type)? Describe all appropriate behaviors for all agent types.

The particles will:

1. move randomly until they hit a **wall** and their energy level is more than 0;
2. replenish their energy level when they find **food**;
3. leave behind a streak of **slime**;
4. partially replenish their **energy** while they remain on **slime**;
5. lose energy whenever they are not on a **slime** tile.

## 5. In what kind of environment do these agents operate? Describe the basic environment type (e.g., spatial, network, featurespace, etc.) and fully describe the environment.

The environment will have three kinds of tiles:

1. **Floor**, on which (**particles**) will be able to walk and whose tiles will be converted to **slime** in their wake;
2. **Walls**, which particles cannot cross;
3. **Food**, in the origin and target tiles. The original **particles** will spawn in one of the tiles.

A **shortest path** will also be visible within the labyrinth, but it won't be used by any of the agents.

## 6. If you had to “discretize” the phenomenon into time steps, what events and in what order would occur during any one time step? Fully describe everything that happens during a time step.

From the point of view of a **particle**:

Move in the same direction you were moving before, spending a little **energy** and leaving behind a slime in proportion to your current energy level and:

- If you hit a **wall**, change direction, spending significant **energy**;
- If you hit **food**, replenish your energy completely and turn around.

From the point of view of **slime**:

- Set your level to a certain amount less than the previous turn.

## 7. What are the inputs to the model? Identify all relevant inputs.

1. Number of particles;
2. Type of labyrinth (some options provided);
3. Energy cost of a step / a change of direction;
4. Slime persistence (possibly in ticks).

## 8. What do you hope to observe from this model? Identify all relevant outputs.

1. Number / percentage of live particles;
2. Average energy;
3. Average distance of particles from the shortest path.

I think it would be interesting to see these graphs evolve, and  perhaps compare them with the results of standard pathfinding algorithms over time.
