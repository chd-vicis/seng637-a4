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
  ```
  return this.upper - this.lower;
  ```
  This mutation was an arithmetic operator replacement since it replaced the "-" with "+", adding the two variables instead of subtracting them, affecting the returned value. This mutant was successfully killed by some of the test cases. For example, one test case that killed this mutant was testGetLengthValidRange(), fed in a range with the lower bound being -1 and the upper bound being 1 and expected this function getLength() to return 2 (1 - (-1) = 2). Therefore, since this mutant was introduced the result ended up being 0 (1 + (-1) = 0) and thus resulted in this test case failing, which means the mutant was killed.<br>
  
2. Mutation #2 (on line #123, mutation #1)<br>
  Mutation applied by Pitest tool - Incremented (a++) double field upper on method Range.getLength(). This mutant was applied on the following line:
  ```
  return this.upper - this.lower;
  ```
  This mutation was including a post-increment operation to the variable upper. However, since the above statement will still use the original value of the upper for the subtraction and the upper value is only used once in the above statement, this post-increment operation has no effect on the returned value. Therefore, this mutation introduces an equivalent mutant that can not be killed and thus survived.<br>

3. Mutation #3 (on line #105, mutation #1)<br>
  Mutation applied by Pitest tool - Incremented (a++) double field lower on method Range.getLowerBound(). This mutant was applied on the following line:
  ```
  return this.lower;
  ```
  This mutation was including a post-increment operation to the variable lower. However, since the above statement will still return the original value of the lower variable and the lower variable value is only used once in the above statement, this post-increment operation has no effect on the returned value. Therefore, this mutation introduces an equivalent mutant that can not be killed and thus survived.<br>

4. Mutation #4 (on line #114, mutation #6)<br>
  Mutation applied by Pitest tool - Incremented (++a) double field upper on method Range.getUpperBound(). This mutant was applied on the following line:
  ```
  return this.upper;
  ```
  This mutation was including a pre-increment operation to the variable upper. The above statement will now return the original value incremented by 1, affecting the return value. This mutant was successfully killed by some of the test cases. For example, one test case that killed this mutant was getUpperBoundWithSameValue(), fed in a range with the upper bound of 0.5 and expected this function getUpperBound() to return 0.5. But, since this mutant was introduced the returned value ended up being 1.5 (++0.5 => 0.5 + 1 = 1.5) and thus resulted in this test case failing, which means the mutant was killed.<br>

5. Mutation #5 (on line #217, mutation #4)<br>
  Mutation applied by Pitest tool - removed conditional, replaced equality check with true on method Range.combine(Range range1, Range range2). This mutant was applied on the following line:
  ```
  if (range1 == null)
  ```
  This mutation removed the conditional check and always made the condition output true. The above statement will now result in the range2 always being returned, affecting the return value. This mutant was successfully killed by some of the test cases. For example, one test case that killed this mutant was combineWithAUB(), fed in a range1(0.0, 1.1) and a range2(-1.0, 1.0), expected this function combine(Range range1, Range range2) to return a range(-1.0, 1.1). But, since this mutant was introduced the returned value ended up being a range(-1.0, 1.0) (which is just range2) and thus resulted in this test case failing, which means the mutant was killed.<br>

  
# Report all the statistics and the mutation score for each test class
- Mutation Score of Range Class - Before<br>
  <img width="600" alt="Screenshot 2023-07-26 at 5 24 32 PM" src="https://github.com/chd-vicis/seng637-a4/assets/61436662/88955810-62c9-4fc0-ab4a-37eea388738f"><br>
- Mutation Statistics of Range Class - Before<br>
  <img width="300" alt="Screenshot 2023-07-26 at 5 25 34 PM" src="https://github.com/chd-vicis/seng637-a4/assets/61436662/c591613f-c6f5-47a4-bf51-5d1d9dcf99cb"><br>
  Since only 5 methods out of the 15 total methods in the Range class were tested, the Mutation Score mentioned above is not accurate. The following table shows the mutation score for each of the 5 tested methods.
  |Tested Method| # of Survived Mutants| # of Killed Mutants | Total | Mutation Score |
  |-------------|----------------------|---------------------|-------|----------------|
  |Range.combine(Range range1, Range range2)| 6 | 27 | 33 | 82 %|
  |Range.toString()| 4 | 18 | 22 | 82% |
  |Range.getLength()| 4 | 15 | 19 | 79% |
  |Range.getLowerBound()| 1 | 6 | 7 | 86% |
  |Range.getUpperBound()| 1 | 6 | 7 | 86% |
  
- Mutation Score of Range Class - After<br>
  <img width="820" alt="Screenshot 2023-07-28 at 5 49 16 PM" src="https://github.com/chd-vicis/seng637-a4/assets/61436662/5d291748-4e99-4186-af31-c70c3f416e94"><br>
- Mutation Statistics of Range Class - After<br>
  <img width="202" alt="Screenshot 2023-07-28 at 5 49 28 PM" src="https://github.com/chd-vicis/seng637-a4/assets/61436662/08e929aa-47e2-41fe-acba-7e59abd8de26"><br>
  Since only 5 methods out of the 15 total methods in the Range class were tested, the Mutation Score mentioned above is not accurate. The following table shows the mutation score for each of the 5 tested methods.
  Note: The mutation score could not be improved by adding more test cases for the original 5 test methods. This is because the original test cases managed to kill every mutant but the equivalent mutants. Therefore, test cases for two more methods were added to improve the mutation score.
  |Tested Method| # of Survived Mutants| # of Killed Mutants | Total | Mutation Score |
  |-------------|----------------------|---------------------|-------|----------------|
  |Range.combine(Range range1, Range range2)| 6 | 27 | 33 | 82 %|
  |Range.toString()                         | 4 | 18 | 22 | 82% |
  |Range.getLength()                        | 4 | 15 | 19 | 79% |
  |Range.getLowerBound()                    | 1 | 6 | 7 | 86% |
  |Range.getUpperBound()                    | 1 | 6 | 7 | 86% |
  |Range.contains(double value)             | 8 | 45 | 53 | 85% |
  |Range.intersects(double b0, double b1)   | 22 | 84 | 106 | 79% |
  

# Analysis drawn on the effectiveness of each of the test classes

# A discussion on the effect of equivalent mutants on mutation score accuracy

# A discussion of what could have been done to improve the mutation score of the test suites

# Why do we need mutation testing? Advantages and disadvantages of mutation testing

# Explain your SELENUIM test case design process

# Explain the use of assertions and checkpoints

| Name of Test               | Command (Assert)                   | Verification Checkpoints                                                        |
|----------------------------|---------------------------|---------------------------------------------------------------------------------|
| `VerifyProductReviews` | `assert text` | verifies if the reviews displayed belong to the correct product (DEWALT 20V MAX XR Cordless Brushless 3" Cut-Off Tool (tool-only)). |
| `NavigateToProductReviews` | `assert element present` | verifies the presence of "Customer Reviews" |
| `SearchItem` | `assert text` | verifies the presence of an item after searching for it |
| `SearchInvalidItem` | `assert text` | verifies the presence of "computer monitor" in the text of the queried items |


# how did you test each functionality with different test data

| Functionality         | Test Cases                                                            |
|-----------------------|-----------------------------------------------------------------------|
| Reviews                 | Test if the reviews belong to the correct product          |
|                       | Test the presence of customer reviews for a patio item |
| Search bar    | Test search for an item that does not exist using "computer monitor"                                         |
|                       | Test "toolbox" for search                                              |

# Discuss advantages and disadvantages of Selenium vs. Sikulix

# How the team work/effort was divided and managed


# Difficulties encountered, challenges overcome, and lessons learned

# Comments/feedback on the lab itself
