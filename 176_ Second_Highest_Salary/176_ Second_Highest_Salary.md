# Problem 176.Second Highest Salary

Problem Description:

Write a SQL query to get the second highest salary from the Employee table.

Id | Salary 
-|-:
1  | 100    
2  | 200    
3  | 300 

For example, given the above Employee table, the query should return 200 as the second highest salary. If there is no second highest salary, then the query should return __null__.

<br />+---------------------+
<br />| SecondHighestSalary |
<br />+---------------------+
<br />| 200 |
<br />+---------------------+



### My approach:
Find the highest salary, the find the second highest. however, I did not consider the NULL situation.<br>Then I find the other two solutions.
