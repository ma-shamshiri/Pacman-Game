<h1 align="center"> COMP 6721 - Artificial Intelligence </h1>
<h3 align="center"> Project Assignment 1: Pacman Agent </h3>
<h5 align="center"> Concordia University (Winter 2020) </h5>

<!-- TABLE OF CONTENTS -->
<h2 id="table-of-contents"> :book: Table of Contents</h2>

<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#about-the-project"> ➤ About The Project</a></li>
    <li><a href="#prerequisites"> ➤ Prerequisites</a></li>
    <li><a href="#folder-structure"> ➤ Folder Structure</a></li>
    <li><a href="#dataset"> ➤ Dataset</a></li>
    <li><a href="#roadmap"> ➤ Roadmap</a></li>
    <li>
      <a href="#preprocessing"> ➤ Preprocessing</a>
      <ul>
        <li><a href="#preprocessed-data">Pre-processed data</a></li>
        <li><a href="#statistical-feature">Statistical feature</a></li>
        <li><a href="#topological-feature">Topological feature</a></li>
      </ul>
    </li>
    <!--<li><a href="#experiments">Experiments</a></li>-->
    <li><a href="#results-and-discussion"> ➤ Results and Discussion</a></li>
    <li><a href="#references"> ➤ References</a></li>
    <li><a href="#contributors"> ➤ Contributors</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
<h2 id="about-the-project"> :pencil: About The Project</h2>

<p align="justify"> 
  For those of you not familiar with Pacman, it's a game where Pacman (the yellow circle with a mouth in the below figure) moves around in a maze and tries to eat as many food pellets (the small white dots) as possible, while avoiding the ghosts (the other two agents with eyes in the above figure). If Pacman eats all the food in a maze, it wins.
</p>

<p align="center"> 
<img src="gif/pacman_game.gif" alt="Animated gif pacman game" style="max-width:50%;">
</p>

<h2> :cloud: Overview</h2>
In this project, the Pacman agent will find paths through his maze world, both to reach a particular location and to collect food efficiently. I implemented general search algorithms such as depth-first, breadth-first, uniform cost, and A* search algorithms which are used to solve navigation problems in the Pacman world.

<h2> :floppy_disk: Project Files Description</h2>
<ul>
  <li><b>search.py</b> - Where all of the search algorithms reside.</li>
  <li><b>searchAgents.py</b> - Where all of the search-based agents reside.</li>
  <li><b>pacman.py</b> - The main file that runs Pacman games. This file also describes a Pacman GameState types.</li>
  <li><b>game.py</b> - The logic behind how the Pacman world works.</li>
  <li><b>util.py</b> - Useful data structures for implementing search algorithms.</li>
</ul>

<h3>Some other supporting files</h3>
<ul>
  <li><b>graphicsDisplay.py</b> - Graphics for Pacman.</li>
  <li><b>graphicsUtils.py</b> - Support for Pacman graphics.</li>
  <li><b>textDisplay.py</b> - ASCII graphics for Pacman.</li>
  <li><b>ghostAgents.py</b> - Agents to control ghosts.</li>
  <li><b>keyboardAgents.py</b> - Keyboard interfaces to control Pacman.</li>
  <li><b>layout.py</b> - Code for reading layout files and storing their contents.</li>
  <li><b>autograder.py</b> - Project autograder.</li>
  <li><b>testParser.py</b> - Parses autograder test and solution files.</li>
  <li><b>testClasses.py</b> - General autograding test classes.</li>
  <li><b>test_cases/</b> - Directory containing the test cases for each scenario.</li>
  <li><b>searchTestClasses.py</b> - Project specific autograding test classes.</li>
</ul>

<h2> :book: Introduction</h2>
<p>You are able to start the game by typing the following at the command line:</p>
<pre><code>$ python pacman.py</code></pre>

<p>You can see the list of all options and their default values via:</p>
<pre><code>$ python pacman.py -h</code></pre>
<i>Note that all of the commands that appear in this project also appear in <code>commands.txt</code>, for easy copying and pasting.</i>

<h2> :small_orange_diamond: Scenario 1: Finding a Fixed Food Dot using Depth First Search</h2>
<p>I have implemented the depth-first search (DFS) algorithm in the depthFirstSearch function in <code>search.py</code>.</p>
<p>The Pacman will quickly find a solution via running the following commands:</p>

<pre><code>$ python pacman.py -l tinyMaze -p SearchAgent</code></pre>
<pre><code>$ python pacman.py -l mediumMaze -p SearchAgent</code></pre>
<pre><code>$ python pacman.py -l bigMaze -z .5 -p SearchAgent</code></pre>

<p align="center"> 
<img src="gif/DFS.gif" alt="Animated gif DFS Algorithm" height="382px" width="737px">
</p>

<h2> :small_orange_diamond: Scenario 2: Finding a Fixed Food Dot using Breadth First Search</h2>
<p>I have implemented the breadth-first search (BFS) algorithm in the breadthFirstSearch function in <code>search.py</code>.</p>
<p>I wrote a graph search algorithm that avoids expanding any already visited states.</p>
<p>The Pacman will quickly find a solution via running the following commands:</p>

<pre><code>$ python pacman.py -l mediumMaze -p SearchAgent -a fn=bfs</code></pre>
<pre><code>$ python pacman.py -l bigMaze -p SearchAgent -a fn=bfs -z .5</code></pre>

<p align="center"> 
<img src="gif/BFS.gif" alt="Animated gif DFS Algorithm" height="382px" width="737px">
</p>

<h2> :small_orange_diamond: Scenario 3: Finding the best path using Uniform Cost Search</h2>
<p>I have implemented the uniform-cost graph search (UCS) algorithm in the uniformCostSearch function in <code>search.py</code>.</p>
<p>While BFS will find a fewest-actions path to the goal, UCS will find paths that are “best” in other senses.</p>
<p>UCS agents differ only in the cost function they use.</p>
<p>The Pacman will quickly find a solution via running the following commands:</p>

<pre><code>$ python pacman.py -l mediumMaze -p SearchAgent -a fn=ucs</code></pre>
<pre><code>$ python pacman.py -l mediumDottedMaze -p StayEastSearchAgent</code></pre>
<pre><code>$ python pacman.py -l mediumScaryMaze -p StayWestSearchAgent</code></pre>

<p align="center"> 
<img src="gif/UCS.gif" alt="Animated gif DFS Algorithm" height="382px" width="737px">
</p>

<h2> :small_orange_diamond: Scenario 4: Finding the best path using A* search algorithm</h2>
<p>I have implemented the A* graph search algorithm in the aStarSearch function in <code>search.py</code>.</p>
<p>I used Manhattan distance as the heuristic function.</p>
<p>A* finds the optimal solution slightly faster than Uniform Cost Search.</p>
<p>The Pacman will quickly find a solution via running the following command:</p>

<pre><code>$ python pacman.py -l bigMaze -z .5 -p SearchAgent -a fn=astar,heuristic=manhattanHeuristic</code></pre>

<p align="center"> 
<img src="gif/A.gif" alt="Animated gif DFS Algorithm" height="500px" width="500px">
</p>

<h2> :small_orange_diamond: Scenario 5: Finding All the Corners</h2>
<p>I have implemented a search algorithm in <code>searchAgents.py</code> that helps Pacman agent to find the shortest path through the maze that touches all four corners.</p>

<p>The Pacman will quickly find a solution via running the following commands:</p>

<pre><code>$ python pacman.py -l tinyCorners -p SearchAgent -a fn=bfs,prob=CornersProblem</code></pre>
<pre><code>$ python pacman.py -l mediumCorners -p SearchAgent -a fn=bfs,prob=CornersProblem</code></pre>

<p align="center"> 
<img src="gif/All Corners.gif" alt="Animated gif DFS Algorithm" height="420px" width="420px">
</p>

<h2> :small_orange_diamond: Scenario 6: Corners Problem - Admissible and Consistent Heuristic</h2>
<p>I have implemented a non-trivial non-negative consistent heuristic function that returns 0 at every goal state and never returns a negative value.</p>
<p>This function is both <b><i>Admissible</b></i> and <b><i>Consistent</b></i> and has been written in <code>searchAgents.py.</code></p>

<p>The Pacman will quickly find a solution via running the following command:</p>

<pre><code>$ python pacman.py -l mediumCorners -p AStarCornersAgent -z 0.5</code></pre>

<p align="center"> 
<img src="gif/Corner Heuristic.gif" alt="Animated gif DFS Algorithm" height="382px" width="737px">
</p>

<h2> :small_orange_diamond: Scenario 7: Eating All The Dots</h2>
<p>I have implemented a heuristic function that helps Pacman agent to eat all the food in as few steps as possible.</p>
<p>The Pacman will quickly find a solution via running the following command:</p>

<pre><code>$ python pacman.py -l trickySearch -p AStarFoodSearchAgent</code></pre>

<p align="center"> 
<img src="gif/All Dots.gif" alt="Animated gif DFS Algorithm" height="382px" width="737px">
</p>

<h2> :small_orange_diamond: Scenario 8: Suboptimal Search</h2>
<p>In this scenario, I have implemented a function that helps Pacman agent to find a path to the closest dot.</p>
<p>This function has been written in <code>searchAgents.py</code></p>
<p>The Pacman will quickly find a solution via running the following command:</p>

<pre><code>$ python pacman.py -l bigSearch -p ClosestDotSearchAgent -z .5</code></pre>

<p align="center"> 
<img src="gif/Suboptimal Search.gif" alt="Animated gif DFS Algorithm" height="382px" width="737px">
</p>

<h2> :scroll: Credits</h2>
<ul>
  <li>This is the homework project for the course COMP 6721 - Artificial Intelligence (Winter 2020), at Concordia University</li>
  <li>Author: Mohammad Amin Shamshiri</li>
</ul>
