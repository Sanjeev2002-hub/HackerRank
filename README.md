
# HackerRank- Types of Triangles

## Problem Statement 
Followings are Screenshots from HackerRank.

![Image](https://github.com/user-attachments/assets/d3db6dee-e53f-4ae5-aed4-71eca774df99)

![Image](https://github.com/user-attachments/assets/539e58f9-03c2-4954-91a9-f0fee4adb0de)

![Image](https://github.com/user-attachments/assets/294fbabe-a8ac-4daf-91cc-a2264caa3a05)

![Image](https://github.com/user-attachments/assets/28144eb8-89fe-4080-bb02-fdfa8d7124e9)

## SQL Query that I wrote to get the desired result.

![Image](https://github.com/user-attachments/assets/8421c238-1752-4688-b4c9-fdb47097e0b8)

I had written this query. But this qurey has logical in the **case** statement. The "Not a Triangle" condition is placed after the checks for **"Equilateral"** and **"Isosceles"**, which means it will never be reached when it should be.

### Issues in the above Query:

1. *Triangle Inequality Condition Order*:

The condition A + B <= C OR A + C <= B OR B + C <= A should be checked first to determine whether the given sides form a valid triangle.

If this condition isn't checked first, a case like (2, 2, 5) will be incorrectly classified as "Isosceles" instead of "Not a Triangle."

2. *Order of **CASE** Conditions*:

The WHEN A = B OR B = C OR A = C check for Isosceles comes before verifying that it's a valid triangle.

If an invalid triangle has two equal sides (e.g., A = B = 2, C = 5), it would be incorrectly labeled as Isosceles instead of Not a Triangle.

## Corrected Query

![Image](https://github.com/user-attachments/assets/33f5dd4e-9568-4ff5-9c6f-a592c04b9b79)

### Key Fixes:

1. Moved the "Not a Triangle" check to the first WHEN condition to ensure that invalid triangles are classified correctly.

2. Rest of the conditions remain unchanged since they are now only checked after confirming it's a valid triangle.
