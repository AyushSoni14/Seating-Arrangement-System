# 📌 Exam Seating Arrangement
## 📋 Project Overview
This project automates the allocation of students to classrooms for exams, ensuring an efficient and optimized seating arrangement. The system considers factors like course size, room capacity, and block preferences while minimizing room usage and ensuring locality optimization.

## 🎯 Key Features
- ✅ **Prioritized Course Allocation:** Large courses are allocated first to ensure seating availability.
- ✅ **Block-Based Allocation:** Block 9 is filled first before moving to Lecture Theatres (LT).
- ✅ **No Mixed-Block Exams:** Exams are not split between Block 9 and LT unless necessary.
- ✅ **Configurable Buffer System:** A buffer of 5 students per classroom (user-defined, can be set to 0).
- ✅ Two Seating Modes:
  - **Dense Mode:** Allows full capacity allocation for a single course.
  - **Sparse Mode:** Restricts a course to half of a room’s capacity (user-configurable).
- ✅ Optimized Room Usage: Minimizes the number of classrooms required while maintaining seating efficiency.
- ✅ Proximity Optimization: Tries to allocate exams within nearby rooms to reduce dispersion.

## 📂 Folder Structure
### 📄 Input Files
**📌 ip_1:**  Registration Table
- Contains student registration details.
- Registration Table
  
  | Roll Number | Registration Semester | Schedule Semester | Course Code |
  |-------------|-----------------------|-------------------|-------------|
  | 1401MC57    | 4                     | 4                 | HS202       |
  | 1401MC57    | 4                     | 4                 | CS244       |
  | 1401MC57    | 4                     | 4                 | MA216       |
  | 1401MC57    | 4                     | 4                 | MA218       |
  | 1401MC57    | 4                     | 4                 | MA220       |
  | 1401MC57    | 4                     | 4                 | MA225       |
  | 1401MC57    | 4                     | 4                 | MA227       |
  | 1401MC40    | 4                     | 4                 | CS244       |
  | 1401MC40    | 4                     | 4                 | MA216       |
  | 1401MC40    | 4                     | 4                 | MA218       |
**📌 ip_2:** Exam Timetable 
 - Specifies the exam schedule.
 - Format:
     | Date       | Day       | Morning                                      | Evening                                      |
     |------------|-----------|---------------------------------------------|---------------------------------------------|
     | 30/04/2016 | Sunday    | CS249, CH426, MM304, CB306, CE216, CB204, PH422, MM202   | NO EXAM                                     |
     | 01/05/2016 | Monday    | HS202, HS212, HS225, HS312, HS341, HS331, HS713, EE574, MA524   | CS514, CE512, CH606, ME526, ME522, EE513, EE580, MM504   |
     | 02/05/2016 | Tuesday   | HS514, CS372, CS392, CE206, PH201, CS244, PH426, MA424, CB302   | MA504, CE506, MH502, EE507, MM502, CB504, CS546, CE318   |
     | 03/05/2016 | Wednesday | CS259, MA428, MA220, CE428, ME216, EE341, MM206, MM306, ME314, EP202, EE382, CB304, MA533   | CS551, CE514, ME542, ME544, EE514, EE549, PH602, PH513   |
     | 04/05/2016 | Thursday  | HS716, CS209, MA430, CE220, EE280, EE382, MM204, PH428, PH608, EP204, CB208, CB424, PH420   | CS547, CS568, CE545, CH607, ME567, ME547, ME552, EE560   |
     | 05/05/2016 | Saturday  | CS277, MA422, MA218, CE208, EE203, PH424, CB202, NT512, CH434, EE561 ,EE731   | CE532 ,CE536 ,EE535 ,MM520 ,ME510 ,MA502 ,CB506 ,MA536   |
     | 06/05/2016 | Sunday    | MA225 ,CH432 ,EE528 ,MA702 ,MA426 ,MA541 ,ME534 ,ME506 ,PH605 ,CE534 ,CE568   | EE529 ,CS508 ,CE528 ,EE570 ,CE573 ,CS563 ,MM512         |
   
 **📌 ip_3:** Room Capacity
- Defines available rooms and their capacities.
- Format:
  | Room No.   | Exam Capacity          | Block             |
  |------------|------------------------|-------------------|
  | 101        | 30                     | 9                 |
  | 102        | 72                     | 9                 |
  | 103        | 30                     | 9                 |
  | 104        | 72                     | 9                 |
  | 105        | 30                     | 9                 |
  | 106        | 30                     | 9                 |
  | 107        | 72                     | 9                 |
  | 108        | 30                     | 9                 |
  | 109        | 72                     | 9                 |
  | 110        | 30                     | 9                 |
  | 301        | 30                     | 9                 |
  | 302        | 30                     | 9                 |
  | 303        | 72                     | 9                 |

  **📌 ip_4: Student Details**
  - Contains student roll numbers and names.
  - Format:
    
  | Roll Number | Name                          |
  |-------------|-------------------------------|
  | 1121CH05    | Ajit Singh                   |
  | 1121CH07    | Jaishree Mayank              |
  | 1121CH08    | Sudipta Acharya              |
  | 1121CH11    | Nilesh Chakraborty           |
  | 1121CH12    | Mohammad Junaid Akhtar       |
  | 1121CH13    | Pankaj Kumar                 |
  | 1121CH14    | Mukesh Kumar                 |
  | 1121CH15    | Mukesh Kumar Bheel           |

## 📊 Output Files
 **📌 exam_allocation.xlsx**
 - Contains the detailed seating arrangement.
 - Format:

| Date       | Day       | Time     | Course Code | Room | No. of Students | Roll List                     |
|------------|-----------|----------|-------------|------|-----------------|-------------------------------|
| 2016-04-30 | Saturday  | Morning  | CB204       | 102  | 56              | 1401CB01, 1401CB02, 1401CB03, 1401CB04, ...       |
| 2016-04-30 | Saturday  | Morning  | CB308       | 102  | 11              | 1301CB01, 1301CB02, 1301CB03, 1301CB04, ...       |
| 2016-04-30 | Saturday  | Morning  | CB308       | 104  | 43              | 1301CB17, 1301CB18, 1301CB19,1301CB20, ...                 |
| 2016-04-30 | Saturday  | Morning  | CE216       | 107  | 30              | 1401CE33,  1401CE34,  1401CE35....,                      |
| 2016-04-30 | Saturday  | Morning  | CS249       | 107  | -               | ...                           |
| ...        | ...       | ...      | ...         | ...  | ...             | ...                           |

**📌 attendance_sheet.xlsx**
- Provides room usage and vacancy details.
- Format:

| Roll No.   | Name                          | Signature      |
|------------|-------------------------------|----------------|
| 1401CB01   | Rishi Raj                     |                |
| 1401CB02   | Rohit Gupta                   |                |
| 1401CB03   | Shreshtha Ranjan              |                |
| 1401CB05   | Vishnu R Nair                 |                |
| 1401CB07   | Rakesh Kumar                  |                |
| 1401CB08   | Abhijith V Nair               |                |
| 1401CB09   | Andharikar Utkarsh Nitin      |                |
| 1401CB10   | Beeraj Kumar                  |                |
| ...        | ...                           | ...            |

---

## 🛠️ How to Run

### Prerequisites
Make sure you have **Python 3.x** installed. Install the required libraries using:
```bash
pip install pandas openpyxl matplotlib seaborn
```
## Option 1: Run Locally
### 1. ***Clone the Repository:***
```bash
git clone https://github.com/AyushSoni14/Seating-Arrangement-System.git
cd Seating_Arrangement_System
```
### 2. ***Place Input Files:***
Add the following files in the project directory:
- ip_1
- ip_2
- ip_3
- ip_4
### 3. ***Open the Notebook***
```bash
jupyter notebook Seating_Arrangement_System.ipynb
```
### 4. ***Check the outputs:***
- exam_allocation.xlsx
- attendance_sheet.xlsx
## Option 2: Run on Google Colab
### 1. ***Open the Colab Notebook***
- Go to Google Colab.
- Upload Seating_Arrangement_System.ipynb from the repository to Colab.
### 2. ***Upload Input Files to Colab***
Upload the following files into your Colab session:
- ip_1
- ip_2
- ip_3
- ip_4
### 3. ***Install Required Libraries in Colab: Run the following command in a Colab cell:***
``` bash
!pip install pandas openpyxl matplotlib seaborn
```
### 4. ***Run the Notebook Cells***
- Execute all the cells in the notebook.
- Ensure that the input files are properly uploaded to your session.
### 5. ***Download the Output Files:***
- After running, download:
  - exam_allocation.xlsx
  - attendance_sheet.xlsx

## 🏛️ Room Allocation Details
- ⏰ Exam Time: As per the provided exam timetable.
- 📍 Block Priority: Block 9 → LT.
- 📝 Seating Optimization: Ensures minimal classroom usage and avoids widely spaced room assignments.

## 🧑‍💻 Code Highlights
- 🛠 Data Handling: Uses pandas for CSV and text file operations.
- 🛠 Optimized Allocation: Implements efficient seat assignment logic.
- 🛠 Excel Report Styling: Uses openpyxl for color-coded seating plans.
- 🚀 This system ensures a smooth and efficient exam seating arrangement!








