# Academic Course Data Tracking and Reporting System

## Overview

A course data tracking system built as a graduate-level project at Northeastern University (Jan–Mar 2026). The system organizes course offerings, program requirement mappings, and student enrollment selections across three simulated M.S. programs, with validation rules to prevent data quality issues and summary reports to support academic planning decisions.

## Problem

Academic departments managing multiple graduate programs need to keep course offerings, program requirements, and enrollment data organized and consistent. Without a structured system, this data often lives in disconnected spreadsheets — leading to duplicate entries, mismatched course codes, outdated requirement mappings, and reactive planning instead of proactive decision-making.

This project simulates the kind of academic data tracking system that a real academic planning office would use to manage course data across programs.

## How It Works

The project follows a three-stage workflow:

```
AirTable (Data Modeling) → Excel (Validation & Storage) → Tableau (Reporting)
```

### Stage 1: AirTable — Relational Data Modeling

AirTable was used to design the relational structure of the data. Three main tables were created:

- **Course Offerings** — 22 courses across 3 departments (CS, DA, IE) with capacity, enrollment, delivery mode, prerequisites, and instructor fields
- **Program Requirements** — maps each course to its program (M.S. Computer Science, M.S. Data Analytics, M.S. Industrial Engineering) with required vs. elective designation and minimum grade requirements
- **Enrollment Selections** — ~150 enrollment records for 50 simulated students, tracking selection status (Confirmed / Pending / Waitlisted) and advisor approval

AirTable made it easy to see how courses, programs, and enrollment connect — for example, clicking a course code shows which programs require it and which students have selected it.

🔗 **AirTable Base:** https://airtable.com/appxW61SxaB0r3Twx/shruigNvfRFJ6fFSV

### Stage 2: Excel — Validation Rules & Formulas

The working data lives in an Excel workbook with five sheets:

| Sheet                 | Purpose                                                                    |
| --------------------- | -------------------------------------------------------------------------- |
| Course Offerings      | 22 courses with capacity, enrollment, utilization formula, and status      |
| Program Requirements  | Requirement mappings with required/elective designations                   |
| Enrollment Selections | Student enrollment records with selection status and approval tracking     |
| Summary Stats         | Aggregated metrics using Excel formulas (counts, averages, capacity flags) |
| Validation Log        | Records of data quality checks — duplicates, missing fields, format errors |

**Built-in validation rules include:**

- Dropdown menus for delivery mode (In-Person / Hybrid / Online), enrollment status, and approval status
- Credit hour range check (must be 1–4)
- Utilization percentage calculated automatically via formula
- Validation log documenting every quality check performed and its resolution

### Stage 3: Tableau — Summary Reports

CSV files were exported from Excel and imported into Tableau to build summary reports for academic staff. The reports include:

- **Enrollment Trends** — semester-over-semester enrollment by program, showing growth patterns
- **Capacity Utilization** — which courses are full, near capacity, or underutilized
- **Requirement Coverage** — whether all program requirements have corresponding course offerings, highlighting gaps

Reports were designed so academic staff could identify planning issues at a glance — without needing to cross-reference multiple spreadsheets manually.

🔗 **Tableau Dashboard:** https://public.tableau.com/app/profile/kapish.gupta/viz/AcademicCourseDataTracking/Dashboard1

## Data

The data was **simulated** to reflect realistic academic structures at Northeastern University:

- 22 courses across Computer Science (8), Data Analytics (8), and Industrial Engineering (6)
- 3 M.S. programs with distinct core and elective requirements
- 50 students with ~150 enrollment records
- Realistic distributions: varying utilization rates, prerequisite chains, mix of enrollment statuses

The data was scripted to ensure realistic patterns — not randomly generated. Course codes, credit structures, and prerequisite chains follow Northeastern's actual format.

## Key Findings

- Data Analytics program showed the steepest enrollment growth (+32% over 4 semesters)
- 4 courses at or above 90% capacity — flagged for potential section additions or waitlist management
- Industrial Engineering may benefit from 1 additional core course to strengthen program structure
- 3 prerequisite violations and 2 duplicate entries caught during validation checks

## Project Structure

```
academic-course-data-tracking/
├── data/
│   ├── Academic_Course_Data_Tracking.xlsx    # Main workbook with 5 sheets
│   └── csv_exports/                          # CSV files exported for Tableau
│       ├── Course_Offerings.csv
│       ├── Program_Requirements.csv
│       └── Enrollment_Selections.csv
└── README.md
```

## Tools Used

| Tool         | Role in Project                                                                                 |
| ------------ | ----------------------------------------------------------------------------------------------- |
| **AirTable** | Relational data modeling — linked tables between courses, programs, and enrollment              |
| **Excel**    | Data storage with validation rules, formulas (utilization %, summary stats), and quality checks |
| **Tableau**  | Summary reports — enrollment trends, capacity utilization, requirement coverage gaps            |
| **CSV**      | Export format connecting Excel data to Tableau reports                                          |

## Author

**Kapish Gupta**  
M.S. Data Analytics Engineering, Northeastern University  
January – March 2026
