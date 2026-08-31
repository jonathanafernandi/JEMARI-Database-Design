# JEMARI-Database-Design

A database normalization case study for **JEMARI**, a fictional mental health consultation application, developed as a group project for the **COMP6799001 – Introduction to Database Technology** course (Bina Nusantara University).

## Table of Contents

- [Overview](#overview)
- [About JEMARI](#about-jemari)
- [Group Members](#group-members)
- [Project Structure](#project-structure)
- [Entity-Relationship Diagram](#entity-relationship-diagram)
- [Data Anomalies](#data-anomalies)
- [Normalization Process](#normalization-process)
- [Recommendation](#recommendation)
- [Notes](#notes)

## Overview

This repository documents a complete database normalization exercise applied to JEMARI, a mental health consultation platform. The project walks through the full normalization pipeline from Unnormalized Form (UNF) to Boyce-Codd Normal Form (BCNF) while identifying and resolving data anomalies present in the application's raw dataset.

## About JEMARI

JEMARI is an application designed to help people facing mental health challenges connect with professionals (psychiatrists) or peer listeners for consultation and emotional support. The project's background is grounded in WHO statistics: as of 2012 and 2019, 450 million people worldwide suffer from mental disorders, 8 out of 10 of whom receive no treatment, and 800,000 people die by suicide every year, highlighting the need for accessible mental health support platforms like JEMARI.

## Group Members

| Name | Student ID |
|---|---|
| Kevyn Aprilyanto | 2602089793 |
| Jonathan Alvindo Fernandi | 2602089143 |
| Andrew Alfonso Lie | 2602101653 |

**Class:** LB01  
**Academic Year:** 2023/2024

## Project Structure

```
JEMARI-Database-Design/
├── docs/
│   ├── JEMARI_AoL-GroupProject_Laporan.pdf
│   └── JEMARI_AoL-GroupProject-SlidesPresentasi.pdf
└── README.md
```

## Entity-Relationship Diagram

The core entities identified in the JEMARI system include:

- **User (Pengguna)** - attributes: name, gender, email address, phone number, date of birth
- **Counselor (Konselor)** - attributes: name, years of experience, phone number
- **Diagnosis** - created when a counselor evaluates a user's condition
- **Therapy (Terapi)** - attributes: therapy date, session duration

These entities interact through relationships formed when a user books a consultation, receives a diagnosis, and optionally undergoes therapy sessions.

## Data Anomalies

Three types of data anomalies were identified in the raw (unnormalized) JEMARI dataset:

- **Insert Anomalies**: occur when new information (e.g., a new user's data) is added while related information (e.g., an assigned counselor) does not yet exist.
- **Update Anomalies**: occur when updating one piece of information (e.g., a counselor's email) requires updates across multiple duplicated records, risking inconsistency if not all instances are updated.
- **Delete Anomalies**: occur when deleting a user's record unintentionally causes the loss of related counselor data associated with that user.

## Normalization Process

The dataset was progressively normalized through five stages:

| Stage | Description |
|---|---|
| **UNF** (Unnormalized Form) | Raw data as originally collected, containing redundancy and potentially incomplete or duplicated entries. |
| **1NF** (First Normal Form) | Removes repeating groups; every attribute holds a single atomic value, no duplicate rows, and a defined primary key. |
| **2NF** (Second Normal Form) | Requires 1NF plus full functional dependency, non-key attributes must depend on the *entire* primary key. |
| **3NF** (Third Normal Form) | Requires 2NF plus the elimination of transitive dependencies between non-key attributes. |
| **BCNF** (Boyce-Codd Normal Form) | Every non-trivial functional dependency (X → Y) must have X as a superkey, further reducing redundancy. |

## Recommendation

For optimal data analysis and management, it is recommended that JEMARI's database be hosted on a dedicated server using SQL, improving performance, security, and ease of data manipulation as the user base grows.

## Notes

- This is an academic case study. "JEMARI" and its associated data are fictional and created for coursework purposes.
