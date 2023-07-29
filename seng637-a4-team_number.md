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

Assertions and checkpoints are vital components of our testing process, utilized to confirm if a software or website behaves as intended. They function as validation checks, validating whether particular conditions or outcomes are achieved during the testing procedure.

**Assertions:** These are the conditions that we are checking during our test execution. For instance, in the `VerifyProductReviews` test, we're asserting (using assert text) that the text of the reviews displayed matches the text we expect for the specific product ("DEWALT 20V MAX XR Cordless Brushless 3" Cut-Off Tool (tool-only)"). In the `NavigateToProductReviews` test, we're asserting (using assert element present) that the "Customer Reviews" element is present on the page. Basically, assertions help us to determine whether a test has passed or failed based on the boolean outcome (true or false) of the condition checked.

**Verification Checkpoints:** These are the anticipated outcomes that our assertions aim to verify. For example, in the `NavigateToShopByRoom` test, the verification checkpoint is that the page successfully navigates to the "Shop by Room" section. This is what we expect to happen when the test is executed correctly, and it's what we're confirming with our assert title command. Similarly, for the `SelectSpecificRoom` test, the verification checkpoint is the successful navigation to the "Kitchen" category under "Shop by Room". Each verification checkpoint aligns with a specific assertion in our test, serving as an indicator of the test's success.


| Name of Test               | Command (Assert)                   | Verification Checkpoints                                                        |
|----------------------------|---------------------------|---------------------------------------------------------------------------------|
| `VerifyProductReviews` | `assert text` | verifies if the reviews displayed belong to the correct product (DEWALT 20V MAX XR Cordless Brushless 3" Cut-Off Tool (tool-only)) |
| `NavigateToProductReviews` | `assert element present` | verifies the presence of "Customer Reviews" |
| `SearchItem` | `assert text` | verifies the presence of "Milwaukee Tool PACKOUT 22-inch Rolling Tool Box" after searching for it |
| `SearchInvalidItem` | `assert text` | verifies the presence of "computer monitor" in the text of the queried items |
| `NavigateToShopByRoom` | `assert title` | The page should successfully navigate to the "Shop by Room" section |
| `SelectSpecificRoom` | `assert title` | The page should successfully navigate to the "Kitchen" category under "Shop by Room" |
| `DepartmentMenu` | `assert presence` | The page should successfully display a dropdown menu with various departments |
| `SelectSpecificItem` | `assert title` | The page should successfully navigate to the "Air Purifiers & Filters" items category under the "Heating & Cooling" department|
| `ShopInWarehouseValueAndSpecials` | `assert text` | The items chosen products listed in this section should have an indicator of being on sale (such as a discounted price, "sale" or "discount" label)


# how did you test each functionality with different test data

We selected X key functionalities of the Home Depot website to test thoroughly. For each functionality, we developed test cases using Selenium IDE. The table below covers the test cases that we developed:

| Functionality         | Test Cases                                                            |
|-----------------------|-----------------------------------------------------------------------|
| Customer Reviews      | Test if the reviews belong to the correct product                            |
|              | Test the presence of customer reviews for a patio item                       |
| Search bar   | Test search for an item that does not exist using "computer monitor"         |
|              | Test for a specified toolbox to search                                       |
| Shop by Room | Test if the "Shop by Room" page appears after clicking on the nav link        |
|              | Test if kitchen furnishings and appliances appear when clicking on "Kitchen" |
| Shop by Department | Test if the "Shop by Department" dropdown appears after clicking on the nav link        |
|              | Test if "Air Purifiers & Filters" appear when routing to "Heating & Cooling" -> "Air Purifiers & Filters" |
| Warehouse Value & Specials | Test if items under "Savings Lighting & Ceiling Fans" are on sale |

# Discuss advantages and disadvantages of Selenium vs. Sikulix

## Selenium

### Advantages:

- Open Source and Popular: Selenium is an open-source tool, which means it enjoys significant support from a broad community of users. This popularity ensures a wealth of resources and peer support.
- Extendable: You can expand Selenium's functionality through the use of plugins. This allows for customization to meet unique testing needs.
- Language Support: Selenium supports a wide range of programming languages, providing flexibility in its usage.
- Ease of Installation: Installing Selenium is straightforward—it primarily involves adding a browser extension.
Extensive Documentation: Comprehensive documentation is available, simplifying understanding and usage of Selenium.

### Disadvantages:

- Limited to Web Applications: As Selenium is a browser plugin, it cannot test desktop applications.
- Additional Plugins Required: To identify GUI components, you often need to install additional browser plugins.
- Website Limitations: Selenium might not support automation on certain websites.
  
## Sikulix

### Advantages:

- Image Recognition: Sikulix uses image recognition powered by OpenCV to identify GUI components. This feature is beneficial when GUI internals or source code is inaccessible.
- Text Recognition: Thanks to Tesseract, Sikulix has basic text recognition capabilities, which enables it to search for text in images.
- Useful for Development Testing: Sikulix can test applications or web apps that are under development.
- Repetitive Task Automation: Sikulix can automate monotonous tasks.
  
### Disadvantages:

- Screen Resolution Dependency: Since Sikulix uses OpenCV for image recognition, test cases are dependent on the screen resolution at which they were recorded. As a result, they may not work on screens with different resolutions.
- Platform-Dependent Scripts: Scripts in Sikulix are platform-dependent, which can limit their portability.
- Error Handling: Handling runtime errors can be challenging, especially during long script runs.
- Less Community Support: Sikulix is less popular than Selenium, which results in reduced community support.
- Poor Documentation: Sikulix's documentation is not as comprehensive as Selenium's, which could hinder its usage and understanding.

# How the team work/effort was divided and managed


# Difficulties encountered, challenges overcome, and lessons learned

# Comments/feedback on the lab itself
