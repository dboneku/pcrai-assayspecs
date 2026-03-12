# pcrai-assayspecs

## Project Overview
This repository contains an "Assay Specification Worksheet" application, currently implemented as a single-page HTML file (`index.html`) using Tailwind CSS and SheetJS. The goal is to allow laboratory personnel to configure assays, targets, controls, and performance specifications for PCR analysis.

## Core Logic & Relationships
- **Definitions**: **Assay = Mix**. 1:1 mapping between the chemical mix and the assay definition.
- **Assays & Targets**: Hierarchy is Assay -> Targets (multiple) -> Controls (multiple).
- **Quantitative Calculation**:
    - Option for **Stored Formula**: Current active Slope, Intercept, R².
    - Option for **Per-Plate Calculation**: Standard curve run every time.
    - **Rounding & Units**: Configured at the **Assay level**.
- **Validity & Performance**:
    - **Inhibition Check**: Hard-coded logic (IC Ct < 35 trigger). Enabled by default via toggle.
    - **Plate Geometry**: Defaults to **96-well plate** support only.
- **Quality Controls (QC)**:
    - SD and Mean are uniquely paired with **Lot Numbers**.
    - **Westgard Rules**: 1-2s (Warning), 2-2s (Error), 1-3s (Error).
- **Rules & Expressions**:
    - Build a dedicated **Expression Builder** for Boolean outcome rules (e.g., `Target1=POS & Target2=NEG`).
- **Data Export**:
    - Primary export: **JSON** for system config.
    - Secondary export: **Excel** for human review.

## Memory & Persistence
> [!IMPORTANT]
> **This file (CLAUDE.md) serves as the primary memory for this repository.** 
> Always update this file with any new requirements, architectural decisions, or technical specifications provided by the user to ensure continuity across sessions.

## Development Tasks
- [ ] Rework the UI/Schema to sync with the "Assay Specification Sheet (1).xlsx" structure.
- [ ] Split specifications into Assay-level and Target-level configurations.
- [ ] Implement toggle for Stored Formula vs. Per-Plate calculation in Quantitative assays.
- [ ] Implement Westgard rule toggles/configuration (1-2s, 2-2s, 1-3s).
- [ ] Add JSON export functionality.

## Technical Details
- **Styling**: Tailwind CSS
- **Data Export**: SheetJS (XLSX)
- **State Management**: LocalStorage (`pcrai_worksheet`)
