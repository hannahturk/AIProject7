# PROJECT 7: PACMAN CAPTURE THE FLAG

In Harvey Mudd's Artificial Intelligence course (CS 151), our projects are licensed from [UC Berkeley's CS 188](http://ai.berkeley.edu). Each of the seven projects has involved a game scenario using Pacman and ghosts as AI agents as we program Pacman to perform according to the concept we're learning at the moment.

# The premise: capturing the flag
This project is a Capture the Flag contest between two teams in a Pacman maze. The red team defends the left half of the maze, and the blue team defends the right half of the maze. There are two agents on each team; when an agent is in its home territory it is a ghost, and when it is in enemy territory it becomes Pacman. One team wins if its agents eat all the pellets in enemy territory within the given time limit of the game. If neither team reaches this goal within the time limit, the match is deemed a tie.

![test](https://s3-us-west-2.amazonaws.com/cs188websitecontent/projects/sp15/contest2/capture_the_flag2.png)

# Modeling the problems in the game
There are a number of ways to construct the two agents on one's team; I chose to assign one reflex agent to offense and one to defense. Thus, the offensive reflex agent's goal as Pacman is to cross over to enemy territory and eat pellets, and the defensive reflex agent's goal as a ghost is to stay on its home side and prevent the other team's agent(s) from eating pellets.

The offensive reflex agent's primary concerns are locating food pellets and avoiding ghosts looking for it. Meanwhile, the defensive reflex agent's single concern is eliminating pacman agents that cross over into its territory. Therefore, I deemed these three problems the most important to address.

# Search algorithms
The three problems discussed above can be solved by utilizing distance computations and a variety of search algorithms. 
