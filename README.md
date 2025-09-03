# splurge-cursor-rules 
A comprehensive collection of Cursor AI rules for consistent, high-quality code development across multiple domains.

## Overview

This repository contains a set of Cursor AI rules that enforce best practices for software development, with a focus on Python development. The rules are organized into 9 main categories covering various aspects of code quality, design, and development processes.

## Rule Categories

### 🏗️ Design Standards
- Follow SOLID, DRY, BDD (TDD), MVP, KISS, PoLA, and YAGNI design principles
- Prefer composition over inheritance and encapsulation
- Emphasize separation of concerns and fail fast approach
- Follow law of demeter and guard clauses for preconditions
- Prioritize error handling with try blocks and guard clauses
- Use domain-specific custom exceptions for public APIs
- Prefer native/built-in exceptions for low-level APIs
- Avoid side effects in module-level code and place happy path logic last
- Prefer if blocks over if-else chains and iteration over code duplication
- Follow simple, straightforward design principles

### 🎨 Style Standards
- Maximum line length of 120 characters (with exceptions)
- Use blank lines to separate logical code blocks
- Parentheses-only line continuations in Python
- Ruff for Python code style, linting, and formatting
- Replace magic strings/numbers with class-level constants

### 🔄 SDLC Standards
- Research → Plan → Implement development lifecycle
- Document research in `docs/research-[yyyy-MM-ddTHHmm].md`
- Document action plans in `docs/plan-[yyyy-MM-ddTHHmm].md`
- TDD implementation: failing tests → code → refactor cycle
- Plans include requirements, testing strategy (e.g. TDD and BDD), and step-by-step guides

### 📚 Documentation Standards
- Comments for complex logic blocks only
- Avoid inline comments except for complex intent clarification
- Google-style docstrings for Python
- Minimize noisy comments for refactors/redesigns

### 🔧 Method Standards
- Parameters on separate lines for readability
- Named keyword arguments for defaults
- Keywords required for methods with multiple parameters
- Multi-line formatting for methods with >2 parameters
- No backwards compatibility maintenance unless specified

### 🏷️ Naming Standards
- Descriptive variable names with auxiliary verbs (e.g., `is_active`, `has_permission`)
- PascalCase for acronyms/abbreviations in object definitions
- Lowercase column names for SQL
- UPPER_SNAKE_CASE for constants

### 🐍 Python Standards
- Always type-annotate method signatures
- Type annotations where clarity is needed
- Use `|` instead of `Optional` or `Union`
- Adhere to PEP 8 and PEP 585 standards
- Target Python 3.10+ features
- Absolute import paths preferred
- Imports at module top when possible
- Sort imports grouped by standard libraries → third-party libraries → local libraries (alphabetically within each group)

### 🧪 Testing Standards
- Validate public API behavior only
- Use actual data, interfaces, and objects (avoid mocks)
- Target 85% code coverage for public interfaces
- Prefer shared test helpers for common logic
- Validate text patterns, not exact content/formatting
- pytest ecosystem: pytest, pytest-cov, pytest-xdist
- Default pytest parameters: `-x -v -n auto`

### 📁 Project Standards
- Create top-level folder: `docs/`
- For code projects: create `tests/` and `examples/` folders
- Under `tests/`: create `unit/` and `integration/` sub-folders
- For Python projects: use modern `pyproject.toml` configuration
- For Python projects: implement CalVer versioning
- Standard license: MIT
- Standard author/maintainer: Jim Schilling
- Standard base URL: `http://github.com/jim-schilling/[REPOSITORY]`

## Usage

These rules are designed to be used with Cursor AI to maintain consistent code quality and development practices. Each rule file (`.mdc` format) can be individually enabled/disabled based on project needs.

## Installation

Clone this repository and configure Cursor AI to use the rules in the `.cursor/rules/` directory.

## Recent Changes

### v2025.09.03 Update
- **Design Standards Enhancement**: Significantly expanded design principles and guidelines
  - Added SOLID, DRY, BDD (TDD), MVP, KISS, PoLA, and YAGNI principles
  - Added preferences for composition over inheritance, encapsulation, and separation of concerns
  - Enhanced with fail fast approach and law of demeter
  - Refined exception handling: domain-specific custom exceptions for public APIs
  - Native/built-in exceptions preferred for low-level APIs
- **SDLC Standards Refinement**: Improved documentation and formatting
  - Moved design principles to Design Standards for better organization
  - Updated date format from `[yyyyMMddTHHmm]` to `[yyyy-MM-ddTHHmm]` for better readability
  - Changed "i.e." to "e.g." for improved grammar

### v2025.09.02 Update
- **Rule File Renaming**: Standardized rule file naming convention for consistency
  - `code-design.mdc` → `design-standards.mdc`
  - `code-style.mdc` → `style-standards.mdc`
  - `development-approach.mdc` → `sdlc-standards.mdc`
  - `naming-conventions.mdc` → `naming-standards.mdc`
- **Python Standards Enhancement**: Added import sorting guidelines
  - Sort imports grouped by: standard libraries → third-party libraries → local libraries
  - Within each group, sort alphabetically
- **README Updates**: Updated section headers to match new naming convention
