# CGPA-Calculator-using-C-

# 🎓 CGPA & SGPA Calculator

> A simple yet powerful console-based GPA calculator written in C++. Calculate your semester GPA (SGPA) or cumulative GPA (CGPA) across multiple semesters with instant academic standing feedback.

---

## ✨ Features

| Feature | Description |
|---|---|
| 📘 SGPA Calculator | Calculate GPA for a single semester |
| 📚 CGPA Calculator | Calculate cumulative GPA across multiple semesters |
| 🏅 Academic Standing | Automatic result classification (First Class, Pass, Fail, etc.) |
| 📊 Grade Scale Viewer | Built-in reference for grade-to-point mapping |
| ✅ Input Validation | Handles invalid grades, negative credits, and bad input gracefully |

---

## 🛠️ Tech Stack

- **Language:** C++
- **Standard:** C++98 or later
- **Libraries:** `iostream`, `iomanip`, `string`

---

## 🚀 Getting Started

### Compilation

```bash
g++ -o gpa_calculator gpa_calculator.cpp
```

### Run

```bash
./gpa_calculator
```

> On Windows:
> ```cmd
> gpa_calculator.exe
> ```

---

## 📋 Menu Options

```
========================================
      CGPA & SGPA CALCULATOR
========================================
  [1] Calculate SGPA (Single Semester)
  [2] Calculate CGPA (Multiple Semesters)
  [3] View Grade Scale
  [4] Exit
========================================
```

---

## 📊 Grade Scale

| Grade | Points | Standing |
|---|---|---|
| A | 4.0 | Outstanding |
| B | 3.0 | Good |
| C | 2.0 | Average |
| D | 1.0 | Below Average |
| F | 0.0 | Fail |

---

## 🏅 Academic Standing Scale

| GPA Range | Classification |
|---|---|
| 3.7 – 4.0 | Outstanding (First Class with Distinction) |
| 3.5 – 3.69 | Excellent (First Class) |
| 3.3 – 3.49 | Very Good (Second Class Upper) |
| 3.0 – 3.29 | Good (Second Class Lower) |
| 2.5 – 2.99 | Above Average (Third Class) |
| 2.0 – 2.49 | Average (Pass) |
| 1.0 – 1.99 | Below Average (Conditional Pass) |
| 0.0 – 0.99 | Poor (Fail) |

---

## 💡 How It Works

**SGPA Formula:**
```
SGPA = Σ(Grade Points × Credit Hours) / Σ(Credit Hours)
```

**CGPA Formula:**
```
CGPA = Σ(Semester GPA × Semester Credits) / Σ(All Credits)
```

---


```
