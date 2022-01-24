# Pewlett-Hackard-Analysis

# Employee Database with SQL

## Overview of Project

### Purpose

The purpose of this project is to learn how to work with databases. I am working for Pewlett Hackard and they will soon have what they call the "Silver Tsunami". This is were a lot of their older employees with soon retire. My job is to use PostgreSQL to import large amounts of employee data. Then use SQL queries to reference multiple tables and find out how many employees and at what positions are going to retire. Then figureout if they have enough employees to mentor people to cover those positions.

## Results

- The first point from to get the deliverables was to create a database table that gathered all the information that we where looking for from employees. The tables that I needed to grab information from were 'employees' and 'titles'. I needed to all employee information for the people that were born between January 1, 1952 and December 31, 1955. I then joined information from the 2 tables on employee number and stored it in a new table called 'retirement_titles'.

![image](https://user-images.githubusercontent.com/92827264/150707319-cc8b85d7-7e16-457c-b3d8-62a989e6d7ea.png)

- Next I had to clean up the table because over time some employees have had title changes due to promotions. This causes their name and employee number to show up multiple times in the table. To fix the table I had to use the DISTINCT ON function on 'emp_no' when selecting the data, and sorting it by currently employeed. This will make the table only keep the first time the employee number shows up and with the to_date being the currently employeed (e.g. '9999-01-01') this will cause the most recent title to be stored. This was done with the code below.

![image](https://user-images.githubusercontent.com/92827264/150708033-af6c0ec2-6165-4f52-a9e3-5341999c9139.png)

- After that I needed to get a count for what titles are going to be retiring. I used the count function to count the employee number of the titles and group it by titles. I then stored the information into another table so I could export the data. The code is shown below.

![image](https://user-images.githubusercontent.com/92827264/150708228-61883d4a-8732-4010-8fb0-e31f55f8b29d.png)

- The last part was to create a table of all the employees that are qualified to mentor people to cover the positions that are retiring. I had to use the same techniques that I used previously. I used DISTINCT ON function to gather unique employee numbers to join data from 'employee', 'dept_emp', and 'titles' tables. It was conditioned on current employees that are 10 years away from retirement. The code to do this is shown below.

![image](https://user-images.githubusercontent.com/92827264/150708874-3030ca45-375f-4c87-b57d-d0c0eaee6dc9.png)

## Summary

- How many roles will need to be filled as the "silver tsunami" begins to make an impact?

  The amount of roles that will need to be filled is 72,458.

- Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?

  The amount of employees that are qualified to mentor are 1,549. There is not enough employees to mentor the next generation unless some take on multiple at one time.
