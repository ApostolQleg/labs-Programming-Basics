# Laboratory Work 2: Project Setup

This repository contains the documentation and references for the second laboratory work on the Fundamentals of Programming. The assignment focuses on proper project initialization, configuration, dependency management, and code modularity.

## Task Description

The objective of this laboratory work is to learn foundational project setup skills, including:
* Initializing a Git repository with a `.gitignore` file.
* Setting up a project configuration file (such as `package.json`).
* Adding authors and an appropriate open-source license.
* Splitting the code from Task 1 into a proper library format.
* Creating a separate demonstration project that links to and uses the library.
* Committing and pushing the structured project to GitHub.

## Implementation Details

The requirements for this laboratory work have been fully integrated into the **QuizTime** frontend application. By applying these project setup principles to a larger real-world application, the practical value of modularity and package management is thoroughly demonstrated.

### 1. Project Configuration
The project is initialized as a Node.js module utilizing a comprehensive `package.json` file. It leverages React 19 and Vite 7, with scripts explicitly defined for development (`npm run dev`), building (`npm run build`), and linting (`npm run lint`). All core dependencies and development dependencies are properly separated and tracked.

### 2. Code Structure and Modularity
To fulfill the requirement of splitting code into a library, the generator and timeout iterator developed in Laboratory Work 1 were modularized. They are separated into dedicated utility files within the project's `libs` directory. These files act as a local library that the React component tree imports and consumes to drive UI animations, satisfying the requirement to link an example project to the library code.

### 3. Version Control and Licensing
The repository is tracked using Git with a standard `.gitignore` tailored for Node and React environments. *The project is open-source and released under the MIT License. The copyright is established for the year 2026 by Oleg Bondarenko.*

## Code Usage and Demonstration

To view the complete project structure, the configuration files, and how the library modules are integrated into a functional user interface, please visit the main repository:

<a href="https://github.com/ApostolQleg/QuizTime"><img src="https://github.com/user-attachments/assets/91c45428-997b-41a3-862a-63a269c5f81b" height="64" align="absmiddle" alt="QuizTime"></a>

## Author

**Oleg Bondarenko** - *Lead Developer*
- **University:** Igor Sikorsky Kyiv Polytechnic Institute (KPI)
- **Faculty:** Faculty of Informatics and Computer Engineering (FICE)
- **Group:** IM-54
- **GitHub:** [@ApostolQleg](https://github.com/ApostolQleg)
