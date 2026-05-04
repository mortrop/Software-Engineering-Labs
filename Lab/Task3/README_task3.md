# Task 3: Class Diagrams

This document provides a brief description of the diagrams included in the `task3.pdf` file. All diagrams in this document are Class Diagrams showing the structural foundation of the systems.

## 1. System 1 - ATM (Automated Teller Machine) - Class Diagram
This diagram maps out the entities and relationships for an ATM system.
- **Key Classes:** Customer, ATM, Transaction, Bank, Withdrawal, and Account.
- **Key Details:** It displays inheritance (Withdrawal extending Transaction), associations (Customer uses ATM, Bank manages Account), and class attributes/methods like `startSession()` for the ATM and `authorizeWithdrawal()` for the Bank.

## 2. System 3 - Car Insurance System - Class Diagram
This diagram structures the data and relationships within a car insurance platform.
- **Key Classes:** Customer, Insurance Company, Vehicle, Policy, ComprehensivePolicy, and Claim.
- **Key Details:** It shows how an Insurance Company issues a Policy, which covers a Vehicle and processes a Claim.

## 3. System 2 - Medical Clinic System - Class Diagram
This diagram models the clinical and administrative entities of a medical center.
- **Key Classes:** Person, Staff, Doctor, Clinic, Patient, and MedicalRecord.
- **Key Details:** Demonstrates inheritance trees (Person -> Staff -> Doctor, and Person -> Patient). It also shows composition/aggregation relationships, such as a Patient possessing a MedicalRecord and Staff working at a Clinic.
