# 🗳️ Digital Logic Voting System with Stopwatch Timer

![Proteus](https://img.shields.io/badge/Simulation-Proteus-blue)
![Digital Logic](https://img.shields.io/badge/Domain-Digital%20Logic-green)
![Course](https://img.shields.io/badge/Course-EEE283L-orange)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📌 Project Overview

This project presents the design and simulation of a **Digital Majority Voting System integrated with a Stopwatch Timer** using fundamental digital logic components. The system was developed as part of the **EEE283L: Digital Logic Design Laboratory** course.

The voting system is designed for a **student club election scenario** where **9 voters** can vote for **3 candidates (A, B, and C)**. The candidate receiving the highest number of votes is declared the winner using **comparator-based majority logic**. Alongside vote counting, a **stopwatch timer** tracks the election duration using digital counters and a **555 Timer-based clock generator**.

The complete system was implemented and verified through **Proteus simulation**, emphasizing digital logic design principles rather than physical hardware realization.

---

## 🎯 Objectives

The main objectives of this project are:

* Design a **digital majority voting system** using logic circuits.
* Count votes for **three individual candidates**.
* Display **individual and total vote counts**.
* Determine the **winner using majority logic**.
* Indicate the winner using **LED indicators**.
* Integrate a **stopwatch timer** for monitoring election duration.
* Simulate and validate the system using **Proteus Design Suite**.

---

## ✨ Features

✅ Majority-based voting system
✅ 3 Candidate support (A, B, C)
✅ Real-time vote counting
✅ Individual vote display using 7-segment displays
✅ Total vote counting system
✅ Comparator-based winner detection
✅ LED winner indication
✅ Stopwatch timer integration
✅ Start / Stop / Reset functionality
✅ Fully simulated in Proteus

---

## 🛠️ Components Used

| No. | Component                        | Quantity |
| --- | -------------------------------- | -------- |
| 1   | 555 Timer IC                     | 1        |
| 2   | CD4026 Decade Counter            | 2        |
| 3   | 74161 Synchronous Binary Counter | 4        |
| 4   | 7447 BCD to 7-Segment Decoder    | 4        |
| 5   | 7485 Magnitude Comparator        | 3        |
| 6   | AND Gate IC                      | 6        |
| 7   | OR Gate IC                       | 1        |
| 8   | NAND Gate IC                     | 1        |
| 9   | NOT Gate IC                      | 1        |
| 10  | 7-Segment Display                | 6        |
| 11  | LED                              | 3        |
| 12  | Resistor (10kΩ)                  | 2        |
| 13  | Capacitor (47µF)                 | 1        |
| 14  | Push Button                      | 1        |
| 15  | Switches (SPST-MOM)              | 2        |
| 16  | Logic Toggle                     | 3        |
| 17  | DC Power Supply (12V)            | 1        |
| 18  | Proteus Design Suite             | 1        |

---

## ⚙️ System Specifications

| Specification        | Details              |
| -------------------- | -------------------- |
| Number of Voters     | 9                    |
| Number of Candidates | 3 (A, B, C)          |
| Voting Method        | Majority Voting      |
| Counting Technique   | Synchronous Counters |
| Winner Indication    | LED Based            |
| Stopwatch Resolution | 1 Second             |
| Display Type         | 7-Segment Displays   |
| Simulation Platform  | Proteus Design Suite |

---

# 🏗️ System Architecture

The project consists of two major subsystems:

1. **Voting System**
2. **Stopwatch Timer System**

These are further divided into multiple functional modules for easier understanding and verification.

### Subsystems

* Stopwatch Subsystem
* Voting Input Subsystem
* Individual Vote Counting Subsystem
* Total Vote Counting Subsystem
* Comparator & Majority Decision Subsystem
* Final Result Display Subsystem

---

## ⏱️ Stopwatch Subsystem

The stopwatch subsystem tracks election duration.

### Working Principle

* A **555 Timer IC** operates in **Astable Mode**.
* It generates a **clock pulse (~100 Hz)**.
* Clock pulses are sent to **CD4026 decade counters**.
* The counters drive **7-segment displays**.
* A **Start/Stop switch** controls timing.
* A **Reset switch** resets the stopwatch.

### Functional Blocks

* 555 Timer (Clock Generator)
* CD4026 Decade Counter
* 7-Segment Display
* Start/Stop Switch
* Reset Switch

---

## 🗳️ Voting Input Subsystem

The voting subsystem receives vote signals for:

* Candidate A
* Candidate B
* Candidate C

### Working Principle

Each candidate input passes through an **AND gate** controlled by a **Vote Enable switch**.

This ensures:

* Votes are counted only during active sessions.
* Invalid or accidental voting is prevented.

---

## 🔢 Individual Vote Counting Subsystem

Each candidate has an independent vote counter.

### Working Principle

1. Vote input is received.
2. Valid vote signal enters **74161 synchronous counter**.
3. Counter output is decoded using **7447 Decoder**.
4. Vote count is displayed on **7-segment displays**.

### Why 74161?

The **74161 synchronous counter** was chosen because:

* Faster operation
* Reduced glitches
* Simultaneous bit transitions
* Reliable counting

---

## 📊 Total Vote Counting Subsystem

A separate subsystem calculates the **total number of votes cast**.

### Working Principle

* Votes from A, B, and C are combined using an **OR Gate**.
* Output is fed into a **74161 Counter**.
* Result is displayed using **7447 + 7-segment display**.

This provides a real-time count of total voter participation.

---

## 🧠 Comparator & Majority Decision Logic

Winner selection is performed using **7485 Magnitude Comparators**.

### Pairwise Comparisons

* A vs B
* B vs C
* C vs A

### Winner Conditions

#### Candidate A Wins

```text
(A > B) AND (A > C)
```

#### Candidate B Wins

```text
(B > A) AND (B > C)
```

#### Candidate C Wins

```text
(C > A) AND (C > B)
```

### Tie Condition

If no candidate has strict majority:

```text
All LEDs remain OFF
```

---

## 💡 Result Display System

The final election result is indicated using LEDs.

| LED   | Meaning          |
| ----- | ---------------- |
| LED A | Candidate A Wins |
| LED B | Candidate B Wins |
| LED C | Candidate C Wins |

Only **one LED glows at a time** to ensure clear winner indication.

---

## 🔄 Working Flow

```text
Start System
      ↓
Enable Voting
      ↓
Cast Votes (A/B/C)
      ↓
Count Individual Votes
      ↓
Count Total Votes
      ↓
Compare Vote Counts
      ↓
Determine Winner
      ↓
Activate Winner LED
      ↓
Display Election Time
```

---

## 🧪 Simulation & Test Cases

The system was tested in multiple scenarios to validate correctness.

### ✅ Test Case 1: Candidate A Wins

Condition:

```text
A > B and A > C
```

Result:

✔ LED A turned ON

---

### ✅ Test Case 2: Candidate B Wins

Condition:

```text
B > A and B > C
```

Result:

✔ LED B turned ON

---

### ✅ Test Case 3: Candidate C Wins

Condition:

```text
C > A and C > B
```

Result:

✔ LED C turned ON

---

### ⚠️ Test Case 4: Tie Situation (4,4,1)

Result:

❌ No LED glows

System correctly identifies no majority.

---

### ⚠️ Test Case 5: Equal Votes (3,3,3)

Result:

❌ No LED glows

Prevents false winner declaration.

---

## 📈 Results

The simulation verified:

* Accurate vote counting
* Correct majority decision logic
* Reliable stopwatch operation
* Correct total vote tracking
* Proper LED-based winner indication
* Successful subsystem integration

The overall system behaved correctly under all tested conditions.

---

## ⚠️ Limitations

Although functional, the project has several limitations.

### 1. Vote Counting Limit

The system continues counting beyond **9 votes** unless manually stopped.

### 2. 7-Segment Display Issue

Certain digits (**6 and 9**) do not display perfectly due to decoder compatibility limitations.

### 3. Stopwatch Range Limitation

The stopwatch can display only:

```text
00 → 99 seconds
```

After 99 seconds, the count resets.

---

## 🚀 Future Improvements

Possible improvements include:

* Automatic vote limit restriction
* Tie-handling mechanism
* Biometric authentication for voting
* Larger stopwatch range
* Better display driver compatibility
* Hardware implementation on PCB
* Database logging of votes
* Real-time monitoring system

---

## 📂 Repository Structure

```text
📦 Digital-Logic-Voting-System
 ┣ 📂 Proteus Files
 ┣ 📂 Report
 ┣ 📂 Circuit Images
 ┣ 📜 README.md
 ┗ 📜 LICENSE
```

---

## 🧰 Technologies Used

* Proteus Design Suite
* Digital Logic Design
* Combinational Logic
* Sequential Logic
* 555 Timer Circuit
* Synchronous Counters
* Magnitude Comparators

---

## 👨‍💻 Team Members

| Name               
| ------------------ |
| Mofakkharul Islam  |
| Md. Shafinur Islam |
| Mahdi Ahmed        |

---

## 🎓 Academic Information

**Course:** EEE283L – Digital Logic Design Laboratory
**Section:** 02
**Group:** 03
**Institution:** entity["organization","BRAC University","Private University in Bangladesh"]

---

## 📚 References

1. Roth, C. H., & Kinney, L. L. *Fundamentals of Logic Design (6th Edition)*
2. Wakerly, J. F. *Digital Logic Design Principles*
3. Quist, S. C., Amegatse, L. K., & Dickson, D. *Conceptual Design of E-Voting System for Academic Institution*

---

## ⭐ Project Summary

This project demonstrates a **fully functional digital majority voting system integrated with a stopwatch timer**, developed using **fundamental digital logic components** and validated through **Proteus simulation**. It successfully applies **combinational and sequential logic concepts** to solve a real-world inspired electronic voting problem.

If you found this project helpful, consider ⭐ starring the repository.
