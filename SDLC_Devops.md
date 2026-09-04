# DevOps — SDLC, Waterfall, Agile & Agile with DevOps

## 1. SDLC — Software Development Life Cycle

Before going into DevOps, understand **SDLC**.

**Life cycle** means the journey from **birth to death**.

**SDLC = Software Development Life Cycle**

In industry standards, SDLC means the complete process of developing and maintaining a software/application/product.

### A Typical SDLC

**Requirements → Planning & Analysis → Development → Testing → Deployment → Monitoring & Maintenance**

---

# 2. Waterfall vs Agile vs Agile with DevOps

Let's understand these concepts using a **School Management System** example.

## Stakeholders

**Stakeholders** are the people or organizations who are part of or have an interest in the system.

Examples:

- Students
- Parents
- Teachers
- Management
- Investors
- Non-teaching staff
- Government agencies

---

# 3. Waterfall Model — Traditional Year-End Examination Model

Imagine a school conducting examinations for students **only once a year**.

- Parents → Paying fees
- Students → Studying
- Teachers → Teaching students

### Year-End Result

- **40% → Pass**
- **60% → Fail**

### Disadvantages

- The problem is identified only at the end of the year.
- By the time results are available, there is very little time to analyse the problems and improve student performance.

### Flow

**Teaching → Entire Year → Final Exam → Results → Analyse Problems**

👉 **Feedback comes very late.**

---

# 4. Agile — Continuous Assessment & Examination Model

Instead of conducting only one exam at the end of the year, the school conducts **multiple exams throughout the year**.

### Examination Flow

**Unit-Test-I → Unit-Test-II → Unit-Test-III → Unit-Test-IV → Unit-Test-V → Quarterly → Half-Yearly → Pre-Final → Final Exam**

This allows teachers to check student performance regularly and get feedback earlier.

## Unit-Test-I

### Preparation

- **Teacher:** Completes the required syllabus before conducting the exam.
- **Student:** Starts preparing before the exam, for example, one week in advance.

### Result

- **60% → Pass**
- **40% → Fail**

### Analyse the Results

The school now has time to:

- Analyse failing students' problems
- Understand why students are failing
- Conduct parent-student meetings
- Identify areas where students need improvement

### Improvement Flow

**Unit-Test-I → Results → Analyse Problems → Take Corrective Action**

---

## Unit-Test-II

After analysing the students' problems and taking corrective actions:

**Passing Percentage → 65%**

The result improves:

**60% → 65%**

This shows the benefit of **frequent feedback and improvement**.

### Continuous Improvement Flow

**Test → Analyse → Improve → Test Again → Better Result**

---

## Final Exam

After continuous assessments and improvements:

- **80% → Pass**
- **20% → Fail**

The school has improved the passing percentage from **40% in the traditional model to 80%**.

However, **20% of students are still failing**.

---

# 5. Targeted Improvement for 20% Failing Students

Now the school focuses specifically on the **20% failing students**.

## Slip Tests

Conduct simple tests regularly:

- Multiple-choice questions
- Short-answer questions
- Around 10 questions per test
- Multiple tests throughout the process

### Flow

**Daily Slip Test → Analyse Results → Identify Problems → Take Corrective Action → Improve Performance**

Teachers analyse the results regularly and share the results with parents.

Additional study hours and better learning methods can be introduced to help students improve.

### Final Result

**99% → Correct / Improved Result**

---

# 6. Waterfall → Agile → Continuous Improvement

```text
WATERFALL
    ↓
Year-End Examination
    ↓
40% Pass / 60% Fail
    ↓
Feedback comes late
    ↓
AGILE
    ↓
Multiple Examinations
    ↓
Analyse Results
    ↓
Corrective Actions
    ↓
60% → 65% → 80% Pass
    ↓
20% Students Still Fail
    ↓
AGILE + DEVOPS THINKING
    ↓
Daily Slip Tests
    ↓
Continuous Feedback
    ↓
Continuous Improvement
    ↓
99% Result
````

> **Note:** Daily slip tests primarily demonstrate the idea of **continuous feedback and continuous improvement**, which is an important Agile principle. The DevOps connection comes when this idea is applied to software delivery using automation, faster testing, deployment, and feedback.

---

# 7. Waterfall Model — Application Development Example

## Project Example

* **Project Cost → $1 Million**
* **Delivery Time → 2 Years**

## Teams Required

The project may require multiple teams:

* Architects
* Developers
* Testers
* Build & Release
* Database
* Linux
* Networking
* Storage
* SharePoint
* etc.

## Project Timeline

### 1. Team Recruitment — 1–2 Months

Time is required to recruit and arrange the required teams.

### 2. Requirement Discussion & Documentation — 2–3 Months

Teams discuss the requirements and prepare the required documentation.

### 3. Software Development — 9 Months

Developers develop the complete software based on the requirements.

### 4. Testing & Deployment — 4 Months

After development is completed, the software goes through testing and deployment.

---

## Defects

Suppose testing identifies:

**100 Defects**

Out of these:

**20 → Invalid Defects**

The team may spend:

**2–3 Days**

analysing and discussing whether those defects are valid or invalid.

---

## Product Delivery Example

A product such as a **Maruti 800** can be thought of as following:

**Requirement → Design → Development → Testing → Final Product → Delivery**

The product is delivered as a **complete product at the end**.

---

## Operations After Delivery

After the product is delivered, other teams are involved in supporting it:

* Operations
* Monitoring
* Service Desk
* L1 Support
* etc.

## Waterfall Summary

In the Waterfall model:

* Development follows sequential phases.
* Feedback comes late.
* The complete product is delivered at once.
* Coordination between teams can be difficult.
* Stakeholders wait a long time for results.

---

# 8. Agile

In Agile, we divide the application into **small modules/features** and develop them in smaller cycles called **Sprints**.

## Divide into Small Modules

### School Management System

```text
School Management System
          ↓
   ┌──────┼────────┬─────────┐
   ↓      ↓        ↓         ↓
Account  Login     OTP   User Management
Creation
   ↓
Fee Management
   ↓
Exam Management
   ↓
Result Management
   ↓
Reports
```

### Application Examples

* Account Creation
* Login
* Forgot Password
* OTP
* Products Catalogue
* Order Management
* Delivery Management
* Reviews
* etc.

### Main Idea

Instead of developing the complete application at once:

**Divide it into smaller modules/features.**

---

# 9. Sprint

A **Sprint** is a fixed period in which the team works on a selected module or set of requirements.

## Sprint-1 → 1 Month

Suppose Sprint-1 is for:

**User Management**

### Sprint Flow

**User Management → Requirements → Development → Testing → Deployment**

---

## Sprint-1 Timeline

**1 Month**

```text
|------ 20 Days ------|------ 10 Days ------|
       Development          Testing &
                            Deployment
```

### First 20 Days

The development team develops the selected functionality.

**Requirements → Development → User Management**

### Next 10 Days

The completed functionality goes through:

**Testing → Deployment**

---

# 10. Stand-up / Sprint Meetings

During the Sprint, the team conducts **stand-up/sprint meetings**.

The team discusses:

* Progress of the work
* Issues
* Blockers
* Sprint-related activities

---

# 11. Defects in Agile

During testing, suppose testers identify:

**10 Defects**

The team analyses the defects:

```text
10 Defects
    ↓
8 Valid Defects
2 Invalid Defects
```

The valid defects need to be addressed, while the invalid defects are identified as not being actual defects.

---

# 12. Agile with DevOps

## Application Development

In Agile, the application is divided into small modules and developed through Sprints.

With **Agile + DevOps**, the focus is on delivering, testing, and getting feedback **continuously and quickly**.

## Developer Example

Suppose a developer develops **50 lines of code**.

Example:

**Enter your first name: ____________**

Now the team asks:

> What if we test and deploy this on the same day?

Instead of waiting until the complete application is developed, this small functionality can be tested and moved through the delivery process quickly.

---

# 13. Testing Example

The team performs different test cases.

## 1. Positive Test

**Enter 40 characters → PASS**

The expected input is provided and the functionality works correctly.

## 2. Negative Test

**Enter 1 character → NEGATIVE**

The application should identify this as invalid input.

## 3. Negative Test

**Enter special characters → NEGATIVE**

The application should reject invalid special characters.

## 4. Negative Test

**Enter numbers → NEGATIVE**

The application should reject numbers if the field is designed to accept only the expected input.

---

# 14. Better Coordination

With Agile + DevOps, development, testing, operations, and other teams need to work with **better coordination**.

### Key Idea

**Better Coordination + Faster Feedback + Automation + Continuous Improvement**

---

# 15. DevOps

A simple way to understand the DevOps idea:

**Whatever you develop, it should move through build, testing, and deployment quickly, with continuous feedback.**

The focus is on:

* Continuous improvement
* Continuous evaluation
* Automation
* Faster feedback
* Collaboration between teams

**DevOps** is the process of developing, building, scanning and testing the application continuously.

For example, if developers write even a single line of code, it should be built, scanned, tested, deployed immediately, and feedback should be given to developers. This is called DevOps.

### DevOps Flow

**Develop → Build → Test → Deploy → Monitor → Feedback**

---

# 16. DevSecOps

DevSecOps extends DevOps by integrating **security** into the software delivery process.

### DevSecOps Flow

**Develop → Build → Security Scan → Test → Deploy → Monitor → Feedback**

The goal is to identify security issues **earlier**, rather than waiting until the end.

### DevOps vs DevSecOps

**DevOps → Develop → Build → Test → Deploy → Monitor → Feedback**

**DevSecOps → Develop → Build → Security Scan → Test → Deploy → Monitor → Feedback**

---

# 17. Tools Used to Achieve DevOps

Different tools can be used to automate different stages:

* **Git → SCM (Source Code Management)**
* **Jenkins → CI/CD**
* **Scanning Tools → Security / Quality Checks**
* **Kubernetes → Container Orchestration**
* **Cloud → Scalability**
* etc.

---

# 18. Real-Time Example — Banking Application

Imagine a bank wants to develop a **Mobile Banking Application**.

## Customer Requirements

The customer wants these features:

* Login
* Account Balance
* Money Transfer
* Bill Payment
* Transaction History

The complete process of building and maintaining this application is called **SDLC**.

---

## 18.1 Requirements

The bank tells the IT team:

> "We need a mobile application where customers can log in and transfer money."

The team collects all requirements.

### Customer Requirements

```text
Customer Requirements
        ↓
      Login
        ↓
  Account Balance
        ↓
  Money Transfer
        ↓
   Bill Payment
        ↓
Transaction History
```

---

## 18.2 Planning & Analysis

The team analyses how to build the application.

They decide:

* **Frontend → Mobile application**
* **Backend → Java / Python / etc.**
* **Database → Store customer & transaction data**
* **Cloud → AWS**
* **Security → Authentication & Authorization**

They also estimate:

* Cost
* Resources
* Timeline
* Infrastructure
* Security requirements

---

## 18.3 Development

Developers start writing the application.

For example:

* One developer → Login
* Another developer → Money Transfer
* Another developer → Transaction History

Code is stored in Git.

### Flow

**Developer → Writes Code → Git Repository**

---

## 18.4 Testing

Testers verify whether the application works correctly.

### Login Test

* Correct username + password → Login successful
* Wrong password → Error
* Empty password → Validation error

### Money Transfer Test

* ₹1,000 transfer → Successful
* Insufficient balance → Error
* Invalid account → Error

Testing tries to find defects before users experience them.

---

## 18.5 Handover / Deployment

After the application passes the required testing, it is deployed.

### Deployment Flow

**Development → Testing → UAT → Production**

Now customers can use the banking application.

---

## 18.6 Maintenance & Monitoring

The work does not end after deployment.

Suppose customers report:

> "Money transfer is taking 30 seconds."

The team investigates and improves the application.

Or the bank wants a new feature:

**UPI Payment**

The development team adds it, tests it, and releases it.

---

# 19. Overall Understanding

## Waterfall

**Sequential phases → Big delivery → Late feedback**

## Agile

**Small modules → Sprints → Frequent feedback → Continuous improvement**

## Agile + DevOps

**Small changes → Automation → Faster testing & delivery → Continuous feedback**

## DevSecOps

**DevOps + Security integrated throughout the lifecycle**

### Simple Memory Flow

**SDLC → Waterfall → Agile → Agile + DevOps → DevSecOps**

And the overall improvement is:

**Big Delivery → Small Increments → Automation → Continuous Feedback → Continuous Improvement**

```
```
