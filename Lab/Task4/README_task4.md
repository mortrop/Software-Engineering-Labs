# Task 4: Behavioral Diagrams

This document provides a brief description of the behavioral diagrams included in the `task4.pdf` file.

## 1. System 1: ATM (Automated Teller Machine) - Sequence Diagram
This diagram models the step-by-step sequential flow of a cash withdrawal process at an ATM.
- **Actors/Objects:** Customer, ATM, BankServer, and CashDispenser.
- **Flow:** Shows the chronological messages passed back and forth, including card insertion, PIN request/entry, validation by the BankServer, amount selection, authorization, and conditional outcomes (dispensing cash if approved, showing an error if declined or PIN is invalid).

## 2. System 3: Car Insurance System - Activity Diagram
This diagram illustrates the step-by-step business workflow of processing an insurance claim.
- **Flow:** It starts with a customer reporting an accident and submitting a claim. The system then validates the policy. Based on decision nodes, the flow branches out: if active, it reviews documents; if incomplete, it requests missing ones. Finally, the damage is assessed, and the claim is either approved (leading to a settlement payment) or rejected.

## 3. System 2: Medical Clinic System - State Diagram
This diagram captures the various states a patient's visit or appointment can be in during their interaction with the clinic.
- **States:** PatientRegistered, AppointmentScheduled, CheckedIn, InConsultation, DiagnosticTesting, Billing, PaymentCompleted, and VisitClosed.
- **Transitions:** It maps the triggers that move the process from one state to another, such as "Check in" to transition from Scheduled to CheckedIn, or "Tests needed" to transition into DiagnosticTesting.
