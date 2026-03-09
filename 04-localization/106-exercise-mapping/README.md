# Exercise: Mapping

> Part of: **Utilizing Scan Matching**

## Additional Content

## Exercise Instructions

* Open the VM workspace to practice the current exercise. If you haven't already, review the overview and restrictions outlined in the **Ubuntu VM Workspace - Overview** page. 


* Once you log into the VM, open a Terminal window. 


* Clone the starter code

[Github repository](https://github.com/udacity/nd0013_cd2693_Exercise_Starter_Code)

using the commands below:
  ```bash
  git clone https://github.com/udacity/nd0013_cd2693_Exercise_Starter_Code.git
  cd nd0013_cd2693_Exercise_Starter_Code
  ```


* If you haven't already, review the starter files in the repo. The repo has the starter files for all exercises and the project for this course. 
  ```bash
    .
    ├── Lesson_2_C++_Checkpoint
    ├── Lesson_3_Markov_Localization
    ├── Lesson_5_Creating_Scan_Matching_Algorithms
    ├── Lesson_6_Utilizing_Scan_Matching
    ├── Lesson_7_Project_Scan_Matching_Localization
    ├── README.md
    └── assets
  ```

  You must start with reviewing the root-level

[README](https://github.com/udacity/nd0013_cd2693_Exercise_Starter_Code#readme)

file. 


* Navigate to the lesson directory.
  ```bash
    cd Lesson_6_Utilizing_Scan_Matching
  ```


* The **Lesson_5_Creating_Scan_Matching_Algorithms/** directory has the following exercises.
  ```bash
  .
  ├── Exercise-ICP-Alignment
  ├── Exercise-Mapping
  └── Exercise-NDT-Alignment
  ```


* Follow the instructions in the [specific README](https://github.com/udacity/nd0013_cd2693_Exercise_Starter_Code/blob/main/Lesson_6_Utilizing_Scan_Matching/Exercise-Mapping/README.md) in the **Exercise-Mapping/** sub-directory.

### Instructions for compile-time error

In case you face compile issues with provided solution code, please follow below steps:

* Step1: Remove existing libcarla-install directory.

* Step2: Create a make-libcarla-install.sh file under Lesson_6.../Exercise_Mapping directory with code from [this Github location](https://github.com/udacity/nd0013_cd2693_Exercise_Starter_Code/blob/main/Lesson_7_Project_Scan_Matching_Localization/c3-project/make-libcarla-install.sh) for code content of make-libcarla-install.sh.

* Step 3: Run below commands in order to generate new libcarla-install:

	`chmod +x make-libcarla-install.sh`

	`./make-libcarla-install.sh`

* Step 4: Now compile the solution code and it should work.
