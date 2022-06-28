# Particul-Swarm-Optimisation-PSO
<h3>aplying PSO in finance filed to manage investissements</h3>

![1_JQlQbx7gQOj2yWggID0xPg](https://user-images.githubusercontent.com/54851310/175163522-a73b7231-92aa-4f54-86d7-f54dbfc65692.gif)


# Introduction


Particle swarm optimization (PSO) has been successfully applied in many research and application areas. For my part, I really enjoyed the application of this algorithm in the article by G. Sermpinis [1] on foreign exchange rate forecasting.

It is demonstrated that PSO can have better results in a faster, cheaper way compared with other methods. It can also be parallelized. Moreover, it does not use the gradient of the problem being optimized. In other words, unlike traditional optimization methods, PSO does not require the problem to be differentiable.

Last but not least, there are very few hyperparameters. These parameters are very simple to understand and do not require advanced notions. For the same hyperparameters, PSO will work on a very wide variety of tasks, which makes it a very powerful and flexible algorithm.

Throughout this article, I will detail the mechanisms behind the Particle Swarm Optimization algorithm assuming as a metaphor a group of birds.

# Objectives


Function to minimize Particle Swarm Optimization Visually Explained (PSO) running
Function to minimize 
![image](https://user-images.githubusercontent.com/54851310/175163144-aa0e98cd-0c01-43f2-8b50-9a3b8f4093d5.png)

The objective of this article will be to minimize the function you see above. The function in question is clearly defined, includes only 2 variables, and is differentiable. But keep in mind that this function could be a non-differentiable step function, or a function defined by the weights of a neural network for which we do not know the global minimum [1].

For pedagogical purposes, we will consider the function f(x, y) = x² + (y + 1)² - 5cos(1.5x + 1.5) - 3cos(2x - 1.5) which allows us a 2D and 3D visualization. Thus the objective of this article will be to optimize the function f its global minimum given x and y.

2D-3D view function to minimize Particle Swarm Optimization Visually Explained (PSO)
Function to minimize — 2D and 3D view 
![image](https://user-images.githubusercontent.com/54851310/175163185-a08b1450-6417-41dd-bd9d-845266921046.png)

# Particle


Before we dive into our simple application case, let’s jump into the past. Particle Swarm Optimization is a population based stochastic optimization technique developed by Dr. Eberhart and Dr. Kennedy in 1995 [2] inspired by the social behavior of birds or schools of fish.

Bedtime story: a group of birds is looking for food in a vast valley. There is food in only one place in this valley. None of the birds know where the food is, but all the birds have an idea of how far away they are from the food.

PSO traduction: a group of particles (potential solutions) of the global minimum in a research space. There is only a global minimum in this search space. None of the particles knows where the global minimum is located, but all particles have fitness values evaluated by the fitness function to be optimized.


![image](https://user-images.githubusercontent.com/54851310/175163269-7478a8fd-7692-4b69-b8c3-d0f4e972fbda.png)


Particle defined by its coordinates Particle Swarm Optimization (PSO)
Particle defined by its coordinates


![image](https://user-images.githubusercontent.com/54851310/175163303-28925589-a3fb-4d8e-8fee-ce90251eb51d.png)

Before going further in the explanation of the PSO algorithm, let’s focus a moment on our particles. As you will have understood, each of these particles is a potential solution of the function to be minimized. They are defined by their coordinates in the search space.

Random Initialization of particles position Particle Swarm Optimization (PSO)
Random Initialization of particles position [Original Image]
We can then randomly define particles in the search space as in the image above. But these particles must be in movement to find the optimal function.

Bedtime story: each of these birds moves with a certain speed of flight through the valley to find food.

PSO traduction: each of these particles is in movement with a velocity allowing them to update their position over the iterations to find the global minimum.

![image](https://user-images.githubusercontent.com/54851310/175790223-d880dba6-b259-41fe-9499-d61820f61619.png)


Particle velocity defined by the velocity in each direction Particle Swarm Optimization (PSO)


The particles have already been randomly distributed in the search space. Their velocity must then be initialized. Defined by its speed in each direction the velocity vector will once again be randomized. For this reason, we speak of stochastic algorithms.

Random Initialization of particles position and velocity Particle Swarm Optimization (PSO)
Random Initialization of particles position and velocity 

![image](https://user-images.githubusercontent.com/54851310/175790294-1f2f4eda-b6c0-4cf0-93f2-bf3a5c02fa72.png)

Swarm
PSO shares many similarities with evolutionary computation techniques such as Genetic Algorithms (GA). The system is initialized with a population of random solutions and searches for optima by updating generations. However, unlike GA, PSO has no evolution operators such as crossover and mutation. The difference is in the way the generations are updated.

![image](https://user-images.githubusercontent.com/54851310/176122937-dbf346d8-090c-405b-bfbf-a7de22ec9ec2.png)


Particle update 2D view Particle Swarm Optimization (PSO)
Particle update 2D view [Original Image]
Bedtime story: while flying through the valley, the birds keep their speed (inertia) but also change their direction. Each bird aims to prove he is better than the others. He tries to find food based on his intuition (cognitive). But because he tends to imitate the others (social), he is also influenced by the experience and knowledge of his group.

PSO traduction: over the iterations in the search space, the speed of each particle is stochastically accelerated towards its previous best position (personal best) and towards the best solution of the group (global best).

Particle update Particle Swarm Optimization (PSO)
Particle update [Original Image]
Concretely, at each iteration, each particle is updated according to its velocity. This velocity is subject to inertia and is governed by the two best values found so far.

The first value is the best personal solution the particle has found so far. The second one is the best global solution that the swarm of particles has found so far. So each particle has in memory its best personal solution and the best global solution.



