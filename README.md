# PROJECT 7: PACMAN CAPTURE THE FLAG

In Harvey Mudd's Artificial Intelligence course (CS 151), our projects are licensed from [UC Berkeley's CS 188](http://ai.berkeley.edu). Each of the seven projects has involved a game scenario using Pacman and ghosts as AI agents as we program Pacman to perform according to the concept we're learning at the moment.

# The premise: capturing the flag
This project is a Capture the Flag contest between two teams in a Pacman maze. The red team defends the left half of the maze, and the blue team defends the right half of the maze. There are two agents on each team; when an agent is in its home territory it is a ghost, and when it is in enemy territory it becomes Pacman. One team wins if its agents eat all the pellets in enemy territory within the given time limit of the game. If neither team reaches this goal within the time limit, the match is deemed a tie.

![test](https://s3-us-west-2.amazonaws.com/cs188websitecontent/projects/sp15/contest2/capture_the_flag2.png)

# Modeling the problems in the game
There are a number of ways to construct the two agents on one's team; I chose to assign one reflex agent to offense and one to defense. Thus, the offensive reflex agent's goal as Pacman is to cross over to enemy territory and eat pellets, and the defensive reflex agent's goal as a ghost is to stay on its home side and prevent the other team's agent(s) from eating pellets.

The offensive reflex agent's primary concerns are locating food pellets and avoiding ghosts looking for it. Meanwhile, the defensive reflex agent's single concern is eliminating pacman agents that cross over into its territory. Therefore, I deemed these three problems the most important to address.

The three problems discussed above can be solved by utilizing distance computations and a variety of search algorithms. First, the offensive reflex agent's task of locating the nearest food pellets is easily solved by looping through the list of pellets still in the maze, computing the Manhattan distance between the pellet and the agent, and returning the minimum Manhattan distance from the list. The other two tasks (the offensive reflex agent avoiding ghosts and the defensive reflex agent catching ghosts) is significantly more complex, because unlike pellets in the maze, the other team's agents are moving with each time step. 

# The A* search algorithm
Though I could have used any pathfinding algorithm in my implementation, I chose to use the A* algorithm because it fit the project requirement that we implement something we had not yet done in a previous project. But beyond this deciding factor, the A* algorithm is a good choice because it is quite flexible and performs significantly better than other commonly-used search algorithms like Depth First Search or Breadth First Search. 

As shown in the picture below, in most cases A* finds the shortest path between the start and goal node, even if there is an obstacle in the way. Obstacles are an important to consider, because the agents must navigate through the walled maze.

![test](http://theory.stanford.edu/~amitp/game-programming/a-star/a-star-trap.png)

Here, the heuristic I used in the A* computation was the Manhattan (cityblock) distance between the agent and the enemy agent I was tracking. However, the way I utilized the output from A* for each agent was different.

# The offensive reflex agent
On offense, Pacman's goal is to avoid ghosts while eating pellets. For the sake of simplifying the problem, I did not add any code to address how Pacman chooses to eat the pellets. Instead, I focused on a way to avoid ghosts. I first made the assumption that the enemy ghosts would be using pathfinding algorithms similar to A* to find my offensive agent. I implemented A* and took those results, and programmed my offensive agent to make a move in the opposite direction that the result of A* suggested at every time step. Thus, the offensive reflex agent's main functionality is to predict the ghost's behavior and avoid it.

# The defensive reflex agent
On defense, a ghost's goal is to find the Pacman agent and run into it as soon as possible. Thus, this called for the more obvious use of the A* algorithm: finding the shortest path to the enemy agent and taking the suggested step at each time step.  



# End Notes
I had trouble formatting the recorded audio with my slides (the pictures on this page), so I posted the narration script alongside the pictures instead.

[Link to the first image I used](https://s3-us-west-2.amazonaws.com/cs188websitecontent/projects/sp15/contest2/capture_the_flag2.png)

[Link to the second image I used](http://theory.stanford.edu/~amitp/game-programming/a-star/a-star-trap.png)
