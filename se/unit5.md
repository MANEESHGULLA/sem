# Introduction

Software Testing is a dynamic activity in software engineering used to detect defects and ensure that the Software Under Test (SUT) behaves as expected. Testing increases confidence in software quality by executing the software with selected test cases.

---

## 1. Static and Dynamic Testing Approaches

### **Static Testing:**
Code is not executed. Includes:
- Code inspections  
- Reviews  
- Static analysis tools  

### **Dynamic Testing:**
Code is executed. Includes:
- Running test cases  
- Observing outputs  
- Identifying failures

---

# ERROR, FAULT, FAILURE — Clear Explanation

---

## ✅ ERROR (Human Mistake or Wrong Output)

### ✔ Meaning 1: Human mistake  
This is the mistake made by the developer while designing, coding, or understanding requirements.

**Examples:**
- Developer misunderstands formula  
- Writes wrong condition in code  
- Misinterprets requirement  

**Also called:** *Human error*

### ✔ Meaning 2: Difference between actual and expected output

**Example:**  
- Correct output must be: **10**  
- Program prints: **7**  
This difference is an **error in the output**.

### 🧠 Key idea:
❗ *Error occurs in the developer’s mind or in the observed output.*

---

## 2️⃣ FAULT (Bug / Defect in Code)

A fault is the actual defect inserted into the code or design because of the earlier error.  
It is the **root cause** of failures.

**Examples:**
- Using `>=` instead of `>`  
- Incorrect loop condition  
- Wrong variable used  
- Missing null check  
- Incorrect SQL query  

### 🧠 Key idea:
❗ *A fault is present in the code but may or may NOT cause a failure immediately.*  
Some faults remain hidden until a specific condition occurs.

---

## 3️⃣ FAILURE (System shows incorrect behavior during execution)

A failure happens when the software **executes a fault** and produces wrong behavior.

**Examples:**
- App crashes  
- Wrong output  
- Incorrect calculation  
- UI freezes  
- System stops responding  

Failures are visible.

### 🧠 Key idea:
❗ *A failure is observable at runtime.*  
❗ *Failure happens only when the fault is executed.*

---

## 🔗 Relationship: How They Lead to Each Other

**Human ERROR → causes a FAULT in the code → which may produce FAILURE during execution.**

### Important notes:
- A fault may exist and still not cause a failure (e.g., dead code).  
- A failure cannot occur unless there is a fault.  
- Observing no failures doesn’t mean no faults are present.

---

| Feature                          | **Error**                                                        | **Fault (Bug/Defect)**                 | **Failure**                                  |
| -------------------------------- | ---------------------------------------------------------------- | -------------------------------------- | -------------------------------------------- |
| **Where it occurs**              | Human activity (thinking, designing, coding) OR incorrect output | In the code or design                  | During execution of the software             |
| **Visibility**                   | Not always visible                                               | Not visible to user                    | Always visible                               |
| **Cause/Effect**                 | Cause of fault                                                   | Cause of failure                       | Effect of a fault                            |
| **When it happens**              | During development or observation                                | When writing code                      | When program runs                            |
| **Example**                      | Developer misunderstands formula                                 | Wrong logic in code                    | Program crashes or outputs wrong value       |
| **Detectable by**                | Reviews, inspections                                             | Testing, static analysis               | Runtime behavior                             |
| **Does it always lead to next?** | Error → always causes a fault                                    | Fault → *may or may not* cause failure | Failure → always indicates presence of fault |

---

## Test Case 

A test case is a set of inputs, execution conditions, and expected outputs.  
It checks whether the software under test behaves correctly for that scenario.  
Each test case targets a specific condition or functionality.

---

## ✅ Test Suite 

A test suite is a collection of related test cases grouped together.  
It is used to test a particular module, feature, or behavior of the system.  
Executing a test suite ensures complete coverage of that area.

---

## ✅ Test Harness / Test Framework 

A test harness provides the environment and tools to run test cases automatically.  
It supplies inputs, executes the software, compares outputs, and reports pass/fail.  
It simplifies repeat testing and supports automation.
----

# TESTING PROCESS

The Testing Process in software engineering is a systematic set of activities carried out to detect defects, ensure quality, and verify that the software meets its requirements. Testing is not just running test cases; it involves careful planning, designing high-quality test cases, executing them, and analyzing results. According to the slides, the testing process consists of three major phases:

---

## **1. Test Planning**

Test planning is the first and most important stage of the testing process.  
It starts before coding is complete, often parallel to design.

### **A Test Plan is a formal document that defines:**
- Scope of testing – what will be tested and what will not be tested  
- Approach for testing – strategies, tools, techniques  
- Testing schedule – timelines and effort  
- Test items (SUTs) – modules to be tested  
- Roles and responsibilities – who will test which components  

### **Inputs used to create the test plan:**
- Project Plan  
- Requirements Document  
- Architecture / Design Document  

### **Contents of a Test Plan (from your slides):**
- Test unit specification  
- Features to be tested  
- Testing approach  
- Test deliverables  
- Schedule & task allocation  

*(Diagram from your slide: SE _ UNIT - 5)*

A test plan ensures that testing is organized, systematic, and aligned with project goals.

---

## **2. Test Case Design**

Once planning is complete, the next step is designing test cases for each SUT.

### **A test case includes:**
- Test inputs  
- Execution conditions  
- Expected output  

A good test case reveals defects if they exist.

### **Why test case design is important?**
- Testing has limitations → only a finite set of test cases can be executed  
- Selecting the right test cases determines effectiveness  
- Reviewing documented test cases improves test quality  

### **What Test Case Specification Document Contains:**
- All test cases  
- Input values  
- Conditions being tested  
- Expected outputs  
- (Optional) columns for pass/fail results  

*(Diagram from Test Case Design slide: SE _ UNIT - 5)*

Documenting test cases ensures:  
- No important condition is missed  
- Redundant test cases are removed  
- Reviewers can evaluate completeness  

---

## **3. Test Execution**

After designing test cases, they must be executed on the Software Under Test (SUT).

### **Activities in Test Execution:**
- Set up required test environment  
- Create stubs/drivers if needed  
- Execute test cases in sequence  
- Compare actual and expected output  
- Record results (pass/fail)  
- Log defects for debugging  

Test execution may be manual or automated.

### **Automated Execution:**
- Uses scripts and test frameworks  
- Reduces effort  
- Allows quick retesting  
- Supports regression testing  
---

## 2.3 Psychology of Testing

Testing is not just a mechanical process; it requires a specific mindset.  
The goal of testing is **not to prove the software works**, but to **find errors**.

A tester should think destructively — they should try to **break the software**.

Human psychology naturally tries to confirm correctness rather than search for faults;  
therefore, **independent testers** are often employed.

**Independent testing** means testing is performed by a team separate from the developers.  
This ensures objectivity, unbiased analysis, and thorough evaluation.

---

## Levels of Testing

Software testing is performed in multiple levels, and each level focuses on detecting different categories of defects that enter the system during various phases of development.  
Because software is built incrementally, testing must also be carried out in increments.

---

### **Unit Testing**
- Performed by developers to test individual modules or components.  
- Ensures each function performs correctly.  
- **Example:** Testing a “Calculate Interest” function independently.

---

### **Integration Testing**
- Combines multiple tested modules and checks their interfaces.  
- Focuses on interaction between components.  
- Detects issues like mismatched data types or incorrect data flow.

---

### **System Testing**
- Entire system is tested as a whole.  
- Verifies that all modules work together correctly and satisfy requirements.  
- Usually done by independent test teams.

---

### **Acceptance Testing**
- Performed by end-users or clients to confirm the system meets business needs.  
- Includes **alpha** and **beta** testing.

---

### **Regression Testing**
- Conducted after modifications to ensure no new errors were introduced.  
- Important when maintaining large systems.

---

**Diagram (from PPT - Page 8):**  
Levels of Testing → **Unit → Integration → System → Acceptance**


---

## Unit Testing Strategy

Unit testing strategy focuses on testing the smallest components of the software.

### **Key Points:**
- Test individual functions, modules, or classes.  
- Conducted by developers, often using **drivers** and **stubs**.  
- Ensures internal logic works correctly.  
- Uses white-box techniques: path testing, branch testing, loop testing.  
- Prevents low-level errors from spreading to higher levels.  

👉 **Principle:** Test small units first to avoid costly errors later.

---

## 2️⃣ Integration Testing Strategy

Defines how modules will be combined and tested for interface defects.

### **Major Approaches:**

### **Top-Down Integration**
- Start with the main module; integrate downward.  
- Use **stubs** for missing lower modules.  
- Verifies control flow early.

### **Bottom-Up Integration**
- Start with lower-level modules; integrate upward.  
- Uses **drivers** instead of stubs.  
- Easier to test data flow.

### **Sandwich / Hybrid Integration**
- Combination of top-down and bottom-up approaches.

### **Big-Bang Integration**
- All modules integrated at once.  
- Not recommended — difficult to isolate defects.

### **Purpose:**
- Identify interface problems.  
- Detect data mismatches.  
- Ensure combined behavior is correct.

---

## System Testing

System testing verifies the entire integrated system.

### **Types:**
- **Recovery Testing** – tests ability to recover from crashes.  
- **Security Testing** – checks protection from unauthorized access.  
- **Stress Testing** – tests behavior under heavy load.  
- **Performance Testing** – checks speed, response time, resource usage.  
- **Usability Testing** – checks user interface quality.  
- **Compatibility Testing** – checks performance across environments.

---

## Verification & Validation (V&V) Strategy

Aligned with the V-Model.

### **Verification:**
**Are we building the product right?**  
Ensures software implements specified functions.

Includes:
- Reviews  
- Inspections  
- Walkthroughs  

### **Validation:**
**Are we building the right product?**  
Ensures software meets customer requirements.

Includes:
- System testing  
- User testing  

The V&V strategy ensures quality of both the **process** and the **product**.

---

## Regression Testing Strategy

Ensures that changes do not break existing features.

### **Key Points:**
- Performed after modifications or bug fixes.  
- Uses previously executed test cases.  
- Often automated using a test harness.  
- Ensures stability of old functionalities.  

Essential for long-term system reliability.

---

## Black Box & White Box Testing Strategies

### **Black Box Testing**
Tests **functionality** without knowing internal code.

**Techniques:**
- Equivalence Partitioning (EP)  
- Boundary Value Analysis (BVA)  
- Cause-effect graphing  
- State transition testing  

### **White Box Testing**
Tests **internal code structure**.

**Techniques:**
- Statement coverage  
- Branch coverage  
- Condition coverage  
- Path coverage  

Both strategies complement each other.

---

## Equivalence Partitioning (EP)

### **Meaning:**
Input values are divided into partitions where each group behaves similarly.

### **Why use it?**
Reduces number of test cases while ensuring coverage.

### **Example:**
Age must be **18 to 60**.

- Valid partition: 18–60 → e.g., **30**  
- Invalid partitions: <18 (e.g., **10**) and >60 (e.g., **70**)

One test per partition is enough.

---

## 2️⃣ Boundary Value Analysis (BVA)

### **Meaning:**
Most defects occur at boundaries, so test values at, below, and above boundaries.

### **Example:**
Age must be 18–60.

Test:  
17, 18, 19, 59, 60, 61

BVA finds more edge-case errors.

---

## 3️⃣ Condition Coverage

### **Meaning:**
Every condition inside a decision must evaluate to **TRUE** and **FALSE** at least once.

### **Example:**
```c
if (A > 10 && B < 5)
```
Conditions:

A > 10

B < 5

Tests must cover TRUE/FALSE for each.

Ensures thorough Boolean testing.

4️⃣ Path Coverage
Meaning:

Tests all possible execution paths.

Example:
```
if (X > 0) { A }
else { B }
C
```

Paths:

X > 0 → A → C

X ≤ 0 → B → C

Used for loops, complex logic.

Statement Coverage
Meaning:

All statements in code must execute at least once.

Goal:

Ensure no line is untested.

Example:

```
if (x > 5) { y = 10; }
z = y + 1;

```
To cover all statements: test x = 6.

Limitation: Does NOT test all decision outcomes.

2️⃣ Branch Coverage (Decision Coverage)
Meaning:

Ensures both TRUE and FALSE branches of every decision execute.

Example:
if (x > 5) y = 10;
else y = 20;


Test:

x > 5 (TRUE)

x ≤ 5 (FALSE)

Branch coverage implies statement coverage.

Statement coverage does NOT imply branch coverage.

---

## Manual Testing

### **Meaning:**
Manual Testing is when testers execute test cases **by hand**, without using automation tools.

### **How it works:**
- Tester enters input manually  
- Observes the system behavior  
- Compares actual vs expected output  
- Records pass/fail  

### **Advantages:**
- Best for exploratory, usability, and ad-hoc testing  
- Human intuition catches unexpected issues  
- No programming skills needed  

### **Disadvantages:**
- Slow and time-consuming  
- Error-prone  
- Not suitable for repeated regression testing  
- Costly for large projects  

### **Use when:**
- Test cases change often  
- UI/UX must be evaluated  
- Early development stages  

---

## 2️⃣ Automatic Testing (Automated Testing)

### **Meaning:**
Automated testing uses software tools or scripts to run test cases automatically.

### **How it works:**
- Inputs given through scripts  
- SUT executed automatically  
- Actual vs expected output compared  
- Reports generated automatically  

### **Advantages:**
- Very fast  
- Ideal for regression testing  
- Reliable and accurate  
- Can run 24/7  
- Saves time on large projects  

### **Disadvantages:**
- Requires programming skills  
- High initial setup cost  
- Not suitable for UI/UX testing  
- Test scripts need maintenance  

### **Use when:**
- Tests are repetitive (regression)  
- Large volume of test cases  
- Performance/load/stress testing  
- CI/CD pipelines (DevOps)  

---

## 3️⃣ Clear Comparison Table

| **Feature**     | **Manual Testing**      | **Automated Testing**      |
|-----------------|--------------------------|-----------------------------|
| **Execution**   | By human                 | By tools/scripts            |
| **Speed**       | Slow                     | Fast                        |
| **Accuracy**    | Less (human error)       | High                        |
| **Cost**        | Low initially            | High initially              |
| **Best for**    | UI/UX, exploratory       | Regression, performance     |
| **Skills**      | No programming needed    | Programming required        |
| **Maintenance** | No scripts               | Scripts must be updated     |


