**SENG 637 - Dependability and Reliability of Software Systems**

**Lab. Report \#4 – Mutation Testing and Web app testing**

| Group: 10       | 
|-----------------|
| Amey Brahme     |   
| Tejpreet Bal    |   
| Dhananjay Roy   |   
| Harshil Patel   |   
| Munal Akhtar    |  

# Introduction
During this lab assignment, our primary focus centered around mutation testing and the utilization of the Selenium tool. These concepts were introduced in our lectures. Our group chose to employ the PIT testing tool for mutation testing, specifically to assess mutation coverage within Eclipse. In the latter part of the lab, we utilized the Selenium IDE extension on our individual browsers. The integration of mutation testing aimed to enhance error detection in the original source code. Our test cases were designed to identify vulnerabilities that might have been overlooked during initial testing. Additionally, the lab emphasized GUI testing, providing an introduction to automating test cases. We particularly focused on user interface interactions, allowing users to record and execute their scripts

# Analysis of 10 Mutants of the Range class 

1. Mutation 3, line #144 for contains(double value),
    Applied on the following line:
    ```
    return (value >= this.lower && value <= this.upper);
    ```
    **Mutation**: Changed conditional boundary\
**Result**: SURVIVED\
**Analysis**: This mutation was a boundary change mutation since it likely replaced the boundary conditions >= and <= with > and < respectively. This change affected the behavior of the contains(double value) method, causing it to exclude the lower and upper bounds of the range. However, the mutation survived because the test cases in the testContains() method did not check for values equal to the lower or upper bounds of the range. Therefore, the altered behavior of the contains(double value) method was not detected by the test cases, allowing the mutation to survive. To kill this mutation, additional test cases that check for values equal to the lower and upper bounds of the range should be added. For instance, the testContains() method could include test cases where it checks if the range contains its lower and upper bounds. As a result, when the mutation alters the boundary conditions, the calculated results would deviate from the expected results, leading to failed assertions in the test cases and consequently killing the mutation.

2.  Mutation 1, line #123 for getLength(),
    Applied on the following line:
    ```
    return this.upper - this.lower;
    ```

    **Mutation**: Replaced double subtraction with addition\
    **Result**: KILLED \
    **Analysis**: This mutation was an arithmetic operator replacement since it replaced the subtraction "-" with addition "+". This change affected the calculation of the range lengths, causing incorrect results. However, the mutation was successfully detected and killed by the test cases. For instance, the testLength() method included test cases where specific range objects were instantiated with defined lower and upper bounds. The test then compared the expected lengths of these ranges with the actual lengths. As a result, when the mutation altered the subtraction operation to addition, the calculated lengths became incorrect, leading to failed assertions in the test cases and consequently killing the mutation.

3. Mutation 6, line #193 for constrain(double value),
    Applied on the following line:
    ```
        else if (value < this.lower) 
    ```
     **Mutation**: Negated double field lower \
   **Result**: SURVIVED\
   **Analysis**: The test method testContrain() has a test with value equal to -2, and range of -1 to 1. In this case, where this.lower is -1, and is negated, the mutated condition becomes -2 < 1. Therefore, the result is set to this.lower, which is -1, and the method returns -1. This is the expected result for this test case, so the test case passes and the mutation survives. This is a good example of an equivalent mutant, where the mutation changes the code but does not change the observable behavior of the program    
 
 4. Mutation 3, line #123 for getLength(),
    Applied on the following line:
    ```
    return this.upper - this.lower;
    ```
     **Mutation**: Replaced return of double value with -(x + 1) \
   **Result**: KILLED\
   **Analysis**: This mutation replaced the return value with -(x + 1), introducing a negative increment in the calculation of range lengths. Despite this modification, the mutation was killed by the test cases. The test cases, such as those in the testLength() method, compared the expected lengths of ranges with the actual lengths using assertions. When the mutation altered the return value, the calculated lengths deviated from the expected values. Consequently, the test cases detected the inconsistency and resulted in failed assertions, effectively killing the mutation.

5. Mutation 2, line #123 for getLength(),
    Applied on the following line:

        ```
        return this.upper - this.lower;
        ```

     **Mutation**: Replaced double return with 0.0d\
   **Result**: KILLED\
   **Analysis**: This mutation replaced the return value with 0.0d, affecting the calculation of range lengths. Despite this alteration, the mutation was successfully killed by the test cases. For example, in the testLength() method, the test cases compared the expected lengths of ranges with the actual lengths using assertions. When the mutation replaced the return value with 0.0d, the calculated lengths became incorrect. Consequently, the test cases detected the discrepancy between the expected and actual lengths, leading to failed assertions and ultimately killing the mutation.

6. Mutation 5 on line #123 for getLength(),
    Applied on the following line:
    ```
    return this.upper - this.lower;
    ``` 
    **Mutation**: Negated double field lower\
   **Result**: KILLED\
   **Analysis**: This mutation negated the lower field value, impacting the code's behavior. However, the mutation was detected and killed by the test cases. Similar to the previous mutation, the testLength() method played a crucial role in detecting the mutation. By comparing the expected lengths of ranges with the actual lengths, the test cases identified discrepancies caused by the negation of the lower field value, resulting in failed assertions and ultimately killing the mutation.

7. Mutation 6 on line #123 for getLength(),
    Applied on the following line:
    ```
    return this.upper - this.lower;
    ```
    **Mutation**: Replaced double operation with first member\
   **Result**: KILLED\
   **Analysis**: This mutation replaced a double operation with the first member, which affected the code's behavior. However, the mutation was successfully detected and killed by the test cases. For example, in the testLength() method, specific range objects were created with defined upper and lower bounds, and their lengths were compared with expected values using assertions. When the mutation replaced the operation with the first member, it led to incorrect length calculations, causing the test cases to fail. Consequently, the mutation was effectively killed by the test cases.

8. Mutation 7 on line #123 for getLength(),
    Applied on the following line:
    ```
    return this.upper - this.lower;
    ``` 
    **Mutation**: Replaced double operation by second member\
   **Result**: KILLED\
   **Analysis**: This mutation replaced a double operation with the second member, impacting the code's behavior. However, the mutation was detected and killed by the test cases. Similar to the previous mutation, the testLength() method played a significant role in detecting the mutation. By comparing the expected lengths of ranges with the actual lengths, the test cases identified discrepancies caused by the replacement of the operation with the second member, resulting in failed assertions and ultimately killing the mutation.

9. Mutation 8 on line #123 for getLength(),
    Applied on the following line:
    ```
    return this.upper - this.lower;
    ```
    **Mutation**: Replaced double subtraction with addition\
   **Result**: KILLED\
   **Analysis**: This mutation was an arithmetic operator replacement, replacing subtraction "-" with addition "+". Despite this change affecting the code's behavior, the mutation was successfully killed by the test cases. For instance, in the testLength() method, specific range objects were instantiated with defined upper and lower bounds, and their lengths were compared with expected values using assertions. When the mutation replaced subtraction with addition, it led to incorrect length calculations, causing the test cases to fail. Consequently, the mutation was effectively killed by the test cases.

10. Mutation 10 on line #123 for getLength(),
    Applied on the following line:
    ```
    return this.upper - this.lower;
    ```
     **Mutation**: Replaced double subtraction with division\
    **Result**: KILLED\
    **Analysis**: This mutation replaced double subtraction with division, impacting the calculation of range lengths. However, the mutation was detected and killed by the test cases. Similar to previous mutations, the testLength() method played a crucial role in detecting the mutation. By comparing the expected lengths of ranges with the actual lengths, the test cases identified discrepancies caused by the replacement of subtraction with division, resulting in failed assertions and ultimately killing the mutation.

# Report all the statistics and the mutation score for each test class
## Initial Score and Statistics for Test classes
Range Class Initial Score
<img src="media/rangeInitialScore.png" alt="Range Class Initial Score" />
Range Class Initial Mutation Statistics
<img src="media/rangeInitialMutationStatistics.png" alt="Range Class Initial Mutation Statistics" />
Data Utilities Class Initial Score
<img src="media/DUInitialScore.png" alt="Data Utilities Class Initial Score" />
Data Utilities Class Initial Mutation Statistics
<img src="media/DUInitialStats.png" alt="Data Utilities Class Initial Mutation Statistics" />

## Final Score and Statistics for Test classes
Range Class Final Score
<img src="media/rangeFinalMutationScore.png" alt="Range Class Final Score" />
Range Class Final Mutation Statistics
<img src="media/rangeFinalStatistics.png" alt="Range Class Final Mutation Statistics" />
Data Utilities Class Final Score
<img src="media/DUFinalScore.png" alt="Data Utilities Class Final Score" />
Data Utilities Class Final Mutation Statistics
<img src="media/DUFinalStats.png" alt="Data Utilities Class Final Mutation Statistics" />

# Analysis drawn on the effectiveness of each of the test classes

# A discussion on the effect of equivalent mutants on mutation score accuracy

# A discussion of what could have been done to improve the mutation score of the test suites

# Why do we need mutation testing? Advantages and disadvantages of mutation testing

# Explain your SELENUIM test case design process

# Explain the use of assertions and checkpoints

# how did you test each functionaity with different test data

# How the team work/effort was divided and managed

# Difficulties encountered, challenges overcome, and lessons learned

# Comments/feedback on the assignment itself
