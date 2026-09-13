# Product Roadmap: D&D Player Character Companion

## Vision Statement
To provide D&D 5e players and Dungeon Masters with a lightning-fast, intuitive, and visually captivating digital character sheet and campaign companion.

---

## Phase 1: Codebase Refactoring & Design System Integration (Sprint 1 - 2)
* **Goal**: Modernize existing Django codebase, resolve routing bugs, and implement standard Design System styles.

### Deliverables:
1. **Frontend Modernization**:
   * Migrate inline/Bootstrap default styling to Design System (`DESIGN_SYSTEM.md`).
   * Implement responsive navbar, active state indicators, and dark fantasy theme tokens.
2. **Backend & Architecture Cleanup**:
   * Standardize views in `dnd/views.py` (replace string responses with templates).
   * Refactor URL routes and namespace resolution in `dnd/urls.py`.
   * Add test coverage for `Character` model modifier calculations.

---

## Phase 2: Dynamic Character Creation & Dice Engine (Sprint 3 - 4)
* **Goal**: Automate stat generation and enable standard D&D 5e rules for races, classes, and dice rolling.

### Deliverables:
1. **Interactive Dice Rolling Engine**:
   * Integrate 4d6-drop-lowest stat generator (`dnd/dice.py`) directly into character creation wizard.
   * Provide d4, d6, d8, d10, d12, d20 interactive roller widget on character dashboard.
2. **Race & Class Subsystem**:
   * Implement concrete implementations for base D&D 5e races (Elf, Dwarf, Human, Dragonborn, Halfling, etc.) with automatic stat modifiers.
   * Add class features and proficiency selection (Skill checks, saving throws).

---

## Phase 3: Spellbook & Inventory Management (Sprint 5 - 6)
* **Goal**: Expand character capabilities with full spell management and inventory tracking.

### Deliverables:
1. **Spellbook Module**:
   * Searchable spell database filterable by class, level, and school of magic.
   * Dynamic spell slot tracking (Current vs Max slots, Long Rest reset button).
2. **Inventory & Equipment**:
   * Item manager (Weapons, Armor, Consumables, Magical items).
   * Automatic Armor Class (AC) calculation based on equipped armor and DEX modifier.
   * Carrying capacity and encumbrance calculator.

---

## Phase 4: Live Campaign Dashboard & Exporting (Sprint 7 - 8)
* **Goal**: Enable real-time party collaboration and offline export options.

### Deliverables:
1. **Live Campaign Dashboard**:
   * Dungeon Master view for monitoring party HP, Passive Perception, and initiative order.
   * Session notes sharing between party members.
2. **PDF Export Engine**:
   * One-click export of character sheets to official standard D&D 5e PDF format.
