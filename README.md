# Analytical-Algorithm-for-Arrow-Direction-Recognition
An analytical algorithm for arrow direction searching (angle) in polar coordinate system

## Introduction
Nowadays, Autonomous vehicles have become a important topic in either industry or our society, and a reliable navigation system is always required for the automobiles. There are a lot of things that need to happen to make a working navigation system, but one of them is that there needs to be an algorithm that can read road signs. [1]

Figure 1. Example of the signs
![image](https://user-images.githubusercontent.com/112973740/212385492-6add6b51-ab74-42f9-b7a3-47286b0799a1.png)

Each sign is associated with one direction in polar coordinate system, and our navigation system should be able to convert these signs to the direction the arrows have pointed to. An algorithm that based on 'Moment of Inertia' is designed to achieve this.

## Algorithm
The algorithm is based on the 'Moment of Inertia' concept in Solid Mechanics, where the moment of inertia would be either maximum or minimum along and perpendicular to the axis of symmetry.

Figure 2. Proof of Extremum
![image](https://user-images.githubusercontent.com/112973740/212507735-222a3422-190e-48af-a881-fa7f674a8a1c.png)

With this special property, our algorithm could be splitted as 4 parts: 
1. Preprocess: Standardize input images by converting them to be matrices with 1 on the arrow and 0 at the rest, find the centroid of this converted arrow.

2. Searching for Axis: Using Gradient Descent to search for the direction that maximize/minimize moment of inertia.

3. Component Evaluation: Further analysis is required as the result direction would be either along or perpendicular to the axis of symmetry. A tricky way is to split our arrow with two axis (the axis along the result direction, and the axis that is perpendicular to it) and calculate their moment of inertia separately.

4. Make Decision: Using the property of symmetry to identify the target axis, then decide the arrow direction.

Figure 3. Illustration of Procedure
![image](https://user-images.githubusercontent.com/112973740/212503250-9bca3114-efcd-46a6-8cfa-ac3721a76e97.png)

## Test
An random drive test with 20 arrows as a sequence is performed with this algorithm, the navigation error for each route is defined as the distance between the given destination and the navigation destination. The result for one individual test is shown below.

Figure 4. Random Drive Test
![image](https://user-images.githubusercontent.com/112973740/212501312-243c76c5-6531-47e8-9182-96f73d83bea1.png)

The mean error of 10 individual test is 0.561.

## Error Analysis
This algorithm provides the analytical solution, the error depends on the resolution of given images.

## Reference
[1] CEE492 Data Science Final Exam
