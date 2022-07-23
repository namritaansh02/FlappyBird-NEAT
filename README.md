# FlappyBird-NEAT
Basic flappy bird game developed using Pygame. Integrated NEAT algorithm using python library NEAT to find optimal topology neural network for playing the game.

## NEAT
Use *import neat* to import neat library
*config-feedforward.txt* contains the configurations which I found best for the game. You can experiment by changing values in the file. However since flappy bird is a
quite simple game with one output of jump or no jump, usually it will end up generating optimal neural network in firsts 3 generations regardless of hyperparameters. 

The fitness functions here chosen is such that it is directlt proportional to distance moved by the bird with a finite score increase when bird crosses a pipe. When a bird crashes into a pipe, it gets a decreased fitness score
to prefer birds which have moved the same distance but not crashed. The current configuration generally generates optimal NN within 3 generations.

## NEAT Algorithm
NeuroEvolution of Augmenting Topologies is based on paper published in 2001 which suggests a method by which we can get the optimal neural network topology with optimal
weights. The initial neural network is a very basic one and it specializes for our problems by:

(1) Speciation

(2) Cross Over

(3) Mutation

## Speciation
Each generation has a set of neural networks. There is similary function between neural networks which has 3 hyperparameters. This similarity function is not at all related
to the score of that NN. We sort members of each species by scoring metric. We set a threshold of similarity such that if a NN has similarity values less than threshold it turns into a new species. This way we speciate all the members
of the generation. Now we remove a fixed percentage of members of each generation. This makes sure that species remain hence making sure new innovations despite low score will make it through next generation. 

## Cross Over
Cross over happens among randomly selected members of different species. Cross over is done by aligning the parents by their connection innovation number and for the offspring
the connection config of the parent with high score is considered. Disjoint connects are passed on to offspring. Excess connections are not passed on when other parent has higher score.
This makes the offspring.

## Mutation
Mutation happens to introduce new features or innovation which may turn out to be fruitful. There are 4 types of mutations possible:

(1) Adding of new node along a connection line

(2) Creation of completely new connection between existing nodes 

(3) Random enabling or disabling of a connection line 

(4) Shifting of weights of a connection line

## Resources 
NEAT Paper : https://nn.cs.utexas.edu/downloads/papers/stanley.cec02.pdf 

NEAT Python Library : https://neat-python.readthedocs.io/en/latest/neat_overview.html

https://www.youtube.com/watch?v=VMQOa4-rVxE

https://www.youtube.com/watch?v=b3D8jPmcw-g
