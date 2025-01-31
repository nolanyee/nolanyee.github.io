# Final Exam Scheduler
*Skills: Python, Algorithms, Monte-Carlo Simulation*

### Overview
This program uses graph coloring theory to generate a final exam schedule from students' enrollment data. Each course is a node of a graph. For each student, the courses that the student is enrolled in are all connected to each other. Once all the student enrollment data is entered, the graph is complete. For example

<img src="images/FinalExamFigure.png" width="400">

In the final exam schedule, no course can be in the same time block as any of the courses it is connected to in the graph (in the example above, English must be in a separate block since it is connected to all other courses). Since the graph is not necessarily planar, determining the minimum number of colors (time slots) for the nodes analytically is difficult. However, a workable (but perhaps not completely optimal) schedule can still be calculated using a simple algorithm that iterates through all courses and through all time slots. If a course is not connected to any courses in a time slot, it is added to that slot (it is assumed that there is no limit on number of exams that can take place at one time). Otherwise, the next slot is evaluated. If the course cannot be placed into any existing slot, a new slot is created.

*Prerequisite Libraries: matplotlib*

### Time Complexity
The program also includes a feature to generate random student enrollment data with sequentially numbered courses. This is useful for analyzing the average time complexity of the algorithm. 

At worst case the time complexity with respect to the course load is expected to be O(n<sup>2</sup>) because a fully connected graph with n nodes has n(n-1)/2 connections. The worst case time complexity with respect to the total number of courses is also O(n<sup>2</sup>) because the algorithm has to cycle through all courses and all slots (which at worst case is equal to the number of courses if the entire graph is fully connected), and that would be n(n+1)/2 evaluations. The time complexity with respect to number of students is expected to be at worst O(n) because the graph connection process has to take place once for each student.

By comparison, the results of the Monte Carlo simulation are shown below.

<img src="images/Exams1.png" width="700">
<img src="images/Exams2.png" width="700">
<img src="images/Exams3.png" width="700">

The average time complexity appears to be O(n) for students and course load, and O(log(n)) for total number of courses.
The results also show that for students and course load the number of time slots increases roughly linearly. However, with total number of courses, it appears to decrease as k+1/n (or some power thereof). This is because the more courses there are, the more sparse the graph will be. If the number of courses is large enough, the timeslots approaches the course load, as each student's enrollment is less likely to overlap with that of other students.
