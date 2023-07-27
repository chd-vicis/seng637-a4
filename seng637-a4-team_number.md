**SENG 637 - Dependability and Reliability of Software Systems**

**Lab. Report \#4 – Mutation Testing and Web app testing**

| Group: SENG637- 2   |
|-----------------|
| Jash Dubal                |   
| Steven Duong              |   
| Nikhil Naikar               |   
| Jason Xu                |
| Christopher DiMattia                |

# Introduction


# Analysis of 10 Mutants of the Range class 
1. Mutation #1 (on line #123, mutation #5)<br>
Mutation applied by Pitest tool - Replaced double subtraction with addition on method Range.getLength(). This mutant was applied on the following line:
> return this.upper - this.lower;
This mutation replaced the "-" with 

# Report all the statistics and the mutation score for each test class
- Mutation Score of Range Class - Before<br>
  <img width="600" alt="Screenshot 2023-07-26 at 5 24 32 PM" src="https://github.com/chd-vicis/seng637-a4/assets/61436662/88955810-62c9-4fc0-ab4a-37eea388738f"><br>
- Mutation Statistics of Range Class - Before<br>
  <img width="300" alt="Screenshot 2023-07-26 at 5 25 34 PM" src="https://github.com/chd-vicis/seng637-a4/assets/61436662/c591613f-c6f5-47a4-bf51-5d1d9dcf99cb"><br>
  Since only 5 methods out of the 15 total methods in the Range class were tested, the Mutation Score mentioned above is not accurate. The following table shows the mutation score for each of the 5 tested methods and the total mutation score from these 5 tested methods in Range Class.
  |Tested Method| # of Survived Mutants| # of Killed Mutants | Total | Mutation Score |
  |-------------|----------------------|---------------------|-------|----------------|
  |Range.combine(Range range1, Range range2)| 6 | 27 | 33 | 82 %|
  |Range.toString()| 4 | 18 | 22 | 82% |
  |Range.getLength()| 4 | 15 | 19 | 79% |
  |Range.getLowerBound()| 1 | 6 | 7 | 86% |
  |Range.getUpperBound()| 1 | 6 | 7 | 86% |
  |Total| 16 | 72 | 88 | 82% |
  



# Analysis drawn on the effectiveness of each of the test classes

# A discussion on the effect of equivalent mutants on mutation score accuracy

# A discussion of what could have been done to improve the mutation score of the test suites

# Why do we need mutation testing? Advantages and disadvantages of mutation testing

# Explain your SELENUIM test case design process

# Explain the use of assertions and checkpoints

# how did you test each functionaity with different test data

# Discuss advantages and disadvantages of Selenium vs. Sikulix

# How the team work/effort was divided and managed


# Difficulties encountered, challenges overcome, and lessons learned

# Comments/feedback on the lab itself
