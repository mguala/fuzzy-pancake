# Product Requirements Document (PRD)

## Project Name: D&D Player Character Companion
**Repository**: `fuzzy-pancake`  
**Authors**: @NovaFugaz, @mguala  
**Framework**: Django 4.2  
**Document Version**: 1.0  

---

## 1. Executive Summary
The **D&D Player Character Companion** is a web-based management tool designed to streamline character sheet creation, attribute calculations, and session note-taking for Dungeons & Dragons (5th Edition) players. By replacing easily lost paper character sheets with a responsive digital hub, the platform simplifies stat tracking, skill modifier calculation, and session documentation.

---

## 2. Target Audience & Personas

### Persona A: The Casual Player ("Alex")
* **Needs**: Fast character creation without needing to memorize modifier formulas.
* **Pain Point**: Forgets paper character sheet between bi-weekly gaming sessions.
* **Goal**: Log into a web app on a phone or laptop and see updated stats immediately.

### Persona B: The Campaign Chronicler ("Sam")
* **Needs**: Organized session logging connected directly to their character profile.
* **Pain Point**: Scattered notes across physical notebooks and phone apps.
* **Goal**: Dedicated campaign notes tab linked to their player account.

---

## 3. Feature Specifications

### 3.1 User Authentication & Profiles
* **Registration & Login**: Secure user registration with custom field validation (`RegistrationForm`).
* **Profile Association**: One-to-one mapping between Django `User` and `UserProfile` to isolate user-specific characters and notes.

### 3.2 Character Creator & Sheet Manager
* **Stat Input & Auto-Calculation**:
  * Core attributes: Strength, Dexterity, Constitution, Intelligence, Wisdom, Charisma.
  * Automatic calculation of modifiers using rule: `(attribute_value - 10) // 2`.
  * Automatic updating of 18 standard D&D 5e skill checks (e.g., Athletics derived from STR modifier, Stealth derived from DEX modifier).
* **Character List**: Dashboard listing all created characters belonging to the active user profile.

### 3.3 Session Notes Manager
* **Note Creation**: Rich text or plain text session log entries containing titles and content blocks.
* **Authentication Safeguards**: Session notes are restricted to logged-in users and rendered per `user_profile`.

### 3.4 Dice Rolling Engine
* **4d6 Drop Lowest**: Utility backend method (`daditos()`) simulating 4d6 roll, dropping the lowest value, and summing the highest three for initial attribute generation.

---

## 4. System Architecture & Data Schema

### 4.1 Database Schema
```
+-------------------+        +-------------------+        +-------------------+
|    django.User    | 1    1 |    UserProfile    | 1    N |     Character     |
+-------------------+--------+-------------------+--------+-------------------+
| id (PK)           |        | id (PK)           |        | id (PK)           |
| username          |        | user_id (FK)      |        | user_profile (FK) |
| password          |        | name              |        | name              |
+-------------------+        +-------------------+        | level, exp        |
                                                          | strength..charisma|
                                                          | str_mod..cha_mod  |
                                                          | skills (18)       |
                                                          +-------------------+
                                                                    | 1
                                                                    | N
                                                          +-------------------+
                                                          |       Note        |
                                                          +-------------------+
                                                          | id (PK)           |
                                                          | user_profile (FK) |
                                                          | title, content    |
                                                          +-------------------+
```

---

## 5. Non-Functional Requirements
* **Performance**: Page loads must complete under 1.5 seconds on standard mobile connections.
* **Usability**: High contrast visual layout compliant with WCAG AA guidelines for dark mode gaming environments.
* **Data Integrity**: Enforce attribute boundary limits (minimum value 0, maximum value 30) via Model validators.
* **Security**: Enforce CSRF protection on all form submissions and restrict character/note access to authorized owners.

---

## 6. Success Metrics
* **Completion Rate**: > 90% of user sessions starting character creation successfully save a completed character.
* **Retention**: Users returning to log campaign notes across multiple sessions.
* **Calculation Accuracy**: Zero discrepancy between attribute score inputs and computed skill modifiers.
