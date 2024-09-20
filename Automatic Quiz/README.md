# Quiz Automation System Design Proposal

## Project Motivation
This project was initiated after observing how time-consuming it was for our family, who works with children with developmental disabilities, to manually create simple quizzes. Even though the questions were straightforward, creating them manually consumed significant time. To streamline this process, we developed a system that **automatically generates quizzes and grades answers**.

## Project Overview: Quiz Auto-Generator and Grading System

### Key Objectives:

**Quiz Auto-Generation:**
- Users provide a specific topic as input.
- The system generates questions and answers based on that topic.

**Automatic Grading:**
- The system automatically grades the students' answers.

### Benefits:
- **Significant time savings** in quiz creation and grading.
- **Reduces the manual effort** required for evaluation.

---

## System Workflow

### 1. Prompt Design
- Utilize the **latest model** to generate quizzes.
- Provide clear instructions and examples to the model for **accurate output**.

### 2. API Integration
- Generate quizzes and answers via **API** based on the input topic.

### 3. Quiz and Answer Extraction
- Extract questions and answers from the model’s response for **further processing**.

### 4. Quiz Simulation
- Present questions to students and collect their **responses**.

### 5. Automated Grading
- Automatically compare **student answers** with the correct ones to generate a score.

---

## Code Explanation and Design

### 1. Quiz Parsing and Separation
A function parses the model’s response using regular expressions to **extract question numbers, options, and correct answers**. This allows for structured handling of questions and answers.

**Example pattern:**

```python
pattern = r"(Question \d+:) | (\\n\\n\\[Correct Answer\\]:)"
```

### 2. Data Storage
Two dictionaries are initialized:

- **student_view:** Stores questions and options for students.
- **correct_answers:** Stores the correct answers for grading.

### 3. Collecting Student Answers
The `collect_student_answers()` function iterates over the **student_view** dictionary, displays each question, and **collects student responses**, storing them in a dictionary for later grading.

### 4. Reviewing Student Answers
The `review_student_answers()` function compares **student answers** with the original questions and provides feedback, allowing students to **review their responses**.

### 5. Grading the Exam
The `grade_exam()` function calculates the score by comparing the student’s answers with the **correct_answers** dictionary and prints the final result.

**Key grading structure:**

```python
for q_num in correct_answers:
    if student_answers[q_num] == correct_answers[q_num]:
        score += 1
```

### 6. Modular Structure
The system is built with **modular components** to ensure scalability and maintainability:

- **Question parsing**, answer collection, review, and grading are handled by separate functions, making the code **easy to update and expand**.

---

## Implementation Steps

1. **Design System Prompts:** Create API prompts for quiz generation and correct answer identification.
2. **Extract Questions and Answers:** Parse the API response into structured data.
3. **Simulate the Quiz:** Present questions to students and collect their responses.
4. **Automated Grading:** Implement automated grading by comparing responses with correct answers.

---

## Features Breakdown

- **Question and Answer Storage:** Uses dictionaries to store quiz content and answers for easy access.
- **Review Functionality:** Allows students to review their submitted answers for accuracy.
- **Modularization:** Ensures easy maintenance, updates, and future scalability.
