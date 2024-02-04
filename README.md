# search
Question 1: To implement a depth first search algorithm, I used a stack and initially pushed the starting state into the stack.
            While the stack is not empty, I popped the top and checked if the goal state is met. If not, for each successor to
            the element I just popped, I added it back to the stack.

Question 2: To implement a breadth first search algorithm, I used a queue and initally pushed the starting state into the queue.
            While the queue isnt empty, I popped the front element in the queue and checked if the goal state is met. If not,
            for each successor to the element I got from the front, I pushed the successors to the back of the queue.

Question 3: For the varying cost function, I used a priority queue data structure from util.py. The algorithm is very similar to
            breadth first search from question 2 but this time, the pop function always returns the element with the smallest
            cost. This allows me to always go towards the best path. I used a set for this problem, the next problem, and the
            previous problems to keep track of visited states so that I don't revist a state I have already been to.

Question 4: For A* search, I used the same algorithm as the uniform cost search but this time the cost was a manhattan heuristic
            + the path cost instead of just the path cost that was used in the varying cost function.

Question 5: The only thing I really added was a tuple of 4 boolean values that correspond to each corner on the board. Initally
            they were all False. I know I reached the goal state of pacman visiting all four corners if all the values in the 
            tuple are set to True. I checked if I visited a corner in the getSuccessors method, where I check if a succesor is
            equal to one of the corner values. If the succesor is a corner, then the boolean that is corresponding to that specific
            corner is set equal to true and a new state and updated tuple is returned as a successor.

Question 6: I am taking all unvisited corners, which I know because the state returns not only pacman's position but a tuple which
            shows whether or not I have visited all 4 corners, and adding them to a list. For each unvisited corner, I am getting
            the manhattan distance between pacman and the unvisited corner. After I found the distance, I take the smallest distance
            and add it to the heuristic and make my current corner the corner that was the least furthest from pacman. At the same
            time, I remove the corner that was the closest to pacman from my list of unvisited corners. I do this till I get the
            manhattan distance from each corner to the next closest corner and add it to the heuristic while also removing the most
            recent closest corner from the unvisited corners list. Once this list is empty, I return the heuristic.

Question 7: I have two lists, one that keep track of the manhattan distance between pacman and every single piece of food and another
            list that keeps track of the distance between a piece of food and all other pieces of food on the grid. Once I calculate
            all these distances, I return the smallest distance to a food that pacman has to go + the largest distance between two foods. If the list that contains the pacman to food distance is empty, I return the the largest distance between two foods.
            If food to food list is also empty, I return 0.

Question 8: To check if the goal state is met, I simply check if the given state is one of the food coordinates. If so, I return
            True, otherwise False. As for the algorithm for pacman to find all the dots, I used the uniform cost search algorithm
            from search.py because it gives me a less costly result than depth first search.