# splurge-ai-rules

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![CalVer](https://img.shields.io/badge/versioning-CalVer-22c55e)](https://calver.org/)

A comprehensive collection of AI rules for consistent, high-quality code development across multiple domains.

## Overview

This repository contains a set of AI rules / instructions for Cursor and GitHub Copilot that enforce best practices for software development, with a focus on Python development. The rules are organized into 11 main categories covering various aspects of code quality, design, security, and development processes. All rules have been recently reviewed and updated for maximum clarity and actionable guidance.

## Rule Categories

### 🏗️ Design Standards
- Follow SOLID (Single Responsibility, Open-Closed, Liskov Substitution, Interface Segregation, Dependency Inversion) principles
- Follow DRY (Don't Repeat Yourself) principle
- Follow BDD/TDD (Behavior/Test Driven Development) practices
- Follow MVP (Minimum Viable Product) approach
- Follow KISS (Keep It Simple, Stupid) principle
- Follow PoLA (Principle of Least Authority)
- Follow YAGNI (You Aren't Gonna Need It) principle
- Prefer composition over inheritance
- Prefer encapsulation
- Prefer separation of concerns
- Prefer to fail fast
- Follow the Law of Demeter - objects should only interact with their immediate dependencies
- Prioritize error handling using appropriate mechanisms (exceptions, return values, Result types, or callbacks)
- Use guard clauses to handle preconditions and invalid state early
- Avoid side effects in module-level code
- Place the happy path (main successful execution flow) last in the function
- Use guard clauses and early returns instead of complex if-else chains
- Prefer iteration and modularization over code duplication
- Prefer simple, straightforward design over over-engineering
- Private methods should accept necessary data as parameters rather than directly accessing instance variables
- Use domain-specific custom exceptions for public APIs
- Use native/built-in exceptions for low-level APIs, where appropriate
- Prioritize code clarity while maintaining reasonable efficiency

### 🎨 Style Standards
- Prefer line length max of 120 characters, except when to do so would require temporary variables
- Except clauses shall be prefixed with a blank line
- Prefer separating logical blocks of code with a blank line for visual clarity
- For Python, use parentheses only for line continuations
- For Python, use ruff for code style, linting, and formatting
- Avoid magic strings and magic numbers, prefer class-level constants, otherwise use module/function level constants

### 🔄 SDLC Standards
- Follow Research, Plan, and Implement development lifecycle
- Document research in `docs/research-[yyyy-MM-dd]-[sequence].md`
- Document action plans in `docs/plan-[yyyy-MM-dd]-[sequence].md`
- Document requirements and specifications in `specs/spec-[yyyy-MM-dd]-[sequence].md`
- TDD implementation: write failing tests → implement code → run tests → refactor iteratively
- Plans include requirements, acceptance criteria, testing strategy (TDD/BDD), and step-by-step guides
- Every feature must start as a standalone library before integration:
  - Develop features as independent, reusable library components first
  - Only integrate into larger applications after proving standalone functionality
- Software tools, primary libraries, and development tools must expose functionality through a CLI
- If in doubt, prompt user for clarification and mark as [NEEDS CLARIFICATION]

### 📚 Documentation Standards
- Add comments before complex logic blocks to explain the "why" and "what"
- Use inline comments sparingly, only for complex or non-obvious code sections
- Remove outdated comments during refactoring instead of accumulating them
- Use Google-style docstrings for all public functions, classes, and modules in Python

### 🔧 Method Standards
- Prefer parameters in method signatures and calls to be listed on separate lines
- Prefer named keyword arguments for default parameters
- Require keywords for methods with more than 1 parameter
- Format method signatures with >2 parameters with each parameter on a separate line
- Format method calls with >2 parameters with each parameter on a separate line
- Include practical code examples for multi-parameter formatting
- Do not maintain backwards compatibility unless specifically requested

### 🏷️ Naming Standards
- Use descriptive variable names with auxiliary verbs (e.g., `is_active`, `has_permission`)
- Use PascalCase for class, enum, and dataclass names (e.g., `DsvReader`, `CsvWriter`, `TransformXmlToJson`)
- Prefer lowercase column names for SQL
- Use UPPER_SNAKE_CASE for constant names
- Environment variables must use project prefix `[A-Z][A-Z0-9_]*_` (e.g., `SPLURGE_DSV_`)

### 🐍 Python Standards
- Always add type annotations to function and method signatures
- Add type annotations to variables when it improves code clarity
- Prefer `|` instead of `Optional` or `Union` (Python 3.10+ union syntax)
- Write concise, technical Python that adheres to PEP 8 and PEP 585
- Target modern Python standards (version 3.10 or later)
- Use absolute import paths
- Place imports at module top when possible
- Group and sort imports: standard libraries, then third-party libraries, then local libraries (alphabetically within each group)
- Use separate statements for multiple context managers instead of nesting them

### 🧪 Testing Standards
- Validate behavior of public APIs only
- Prefer validation using actual data, interfaces, and objects
- Avoid use of mocks, except where appropriate
- Target 85% code coverage for all public interfaces and methods
- Prefer shared helpers for common logic
- Avoid validation of implementation details and private APIs
- Prefer validation of patterns of text, avoid exact matching of content and formatting
- pytest ecosystem: pytest, pytest-cov, pytest-xdist
- Default pytest parameters: `-x -v -n auto`
- Test organization: unit/ in `tests/unit/`, integration/ in `tests/integration/`, e2e/ in `tests/e2e/`, performance/ in `tests/performance/`
- Prefer pure pytest function style tests
- Use `tmp_path` and `tmp_path_factory` fixtures for temporary files and directories
- Name test methods as `test_[condition]_[expectedResult]`
- Each test method should ideally test a single condition and expected result
- Use fixtures for common setup and teardown logic
- Use parameterized tests for testing multiple input scenarios
- Use assertions to validate expected outcomes
- Performance guidelines: unit tests (<60s), integration tests (<60s), e2e tests (<60s), full suite (<120s)

### 📁 Project Standards
- Create top-level folder: `docs/`
- Create `docs/README-details.md` which details project features, usage, etc.
- For code projects: create top-level folders: `tests/`, `examples/`, `specs/`
- Under `tests/`: create `unit/`, `integration/`, `e2e/` sub-folders
- For Python projects: use modern `pyproject.toml` configuration
- For Python projects: implement CalVer versioning
- Create project `README.md` which summarizes project
- Create project `CHANGELOG.md` which details changes for each version/feature-branch
- Standard license: MIT
- Standard author/maintainer: Jim Schilling
- Standard base URL: `http://github.com/jim-schilling/[REPOSITORY]`

### 🖥️ CLI Standards
- MUST accept text input via stdin, arguments, or files
- MUST accept environment variables for configuration, unless user opts out
- Sensitive data must use environment variables
- Environment variable names MUST use project prefix `[A-Z][A-Z0-9_]*_` (e.g., `SPLURGE_DSV_`)
- Provide `--output-format {table,json,ndjson}` options (default: table)
- When reading from stdin, a file path of `-` MUST mean "read from stdin"
- Stdout and stderr MUST be UTF-8 encoded without BOM
- Standard exit codes: 0 (success), 1 (error), 2 (invalid arguments), 130 (interrupted)
- Flags map by prefix + uppercasing + hyphens→underscores (e.g., `--api-token` → `SPLURGE_DSV_API_TOKEN`)
- JSON output formats:
  - `--output-format json`: Output complete JSON arrays, one per line
  - `--output-format ndjson`: Output one JSON object per line (newline-delimited)
  - Never mix JSON with other text on stdout
- If an env var is referenced but missing, fail fast: "Missing required environment variable: <NAME>"
- Redact sensitive data in output, logging, and errors
- Document defaults in --help output
- CLI arguments override environment variables
- Environment variables override built-in defaults

### 🔒 Security Standards
- Follow secure coding best practices and OWASP guidelines
- Validate and sanitize all user inputs to prevent injection attacks (SQL, Shell, XSS, command injection)
- Use parameterized queries and prepared statements for database operations
- Implement proper authentication and authorization mechanisms
- Never store sensitive data (passwords, API keys, tokens) in plain text
- Follow the principle of least privilege for user permissions and API access
- Implement comprehensive error handling without exposing sensitive information
- Restrict allowed file types and sizes for uploads
- Use secure random number generators for cryptographic operations
- Implement proper logging without logging sensitive information
- Use environment variables or secure vaults for configuration secrets
- Implement proper password policies and secure password hashing
- Follow secure API design principles (proper HTTP methods, versioning, etc.)

## Usage

These rules are designed to be used with GitHub Copilot and Cursor AI to maintain consistent code quality and development practices. The rules are organized as GitHub Copilot instructions that can be referenced in your project's `.github/copilot-instructions.md` file.

## Installation

Clone this repository and copy the relevant sections from `.github/copilot-instructions.md` to your project's copilot instructions file. The rules can be selectively applied based on your project needs.

## Project Structure

```
splurge-ai-rules/
├── .cursor/
│   └── rules/                      # Cursor AI rule files (.mdc format)
│       ├── design-standards.mdc   # SOLID, DRY, TDD, and design principles
│       ├── style-standards.mdc    # Code formatting and style guidelines
│       ├── sdlc-standards.mdc     # Development lifecycle and planning
│       ├── naming-standards.mdc   # Naming conventions and standards
│       ├── python-standards.mdc   # Python-specific coding standards
│       ├── method-standards.mdc   # Method signatures and parameters
│       ├── documentation-standards.mdc  # Comments and documentation
│       ├── testing-standards.mdc  # Testing best practices and coverage
│       ├── project-standards.mdc  # Project organization standards
│       ├── cli-standards.mdc      # Command-line interface guidelines
│       └── security-standards.mdc # Security and OWASP compliance
├── .github/
│   └── copilot-instructions.md     # GitHub Copilot coding standards
├── docs/                           # Documentation and planning
│   ├── research-[yyyy-MM-dd]-[sequence].md  # Research documentation
│   ├── plan-[yyyy-MM-dd]-[sequence].md      # Action plans and specifications
│   └── README-details.md           # Detailed project documentation
├── LICENSE                         # MIT License
└── README.md                       # This comprehensive overview
```

### Rule Files Overview

**Cursor AI Rules (.mdc files):**
- Individual rule files for each standard category
- Designed for Cursor AI integration
- Can be enabled/disabled per project needs

**GitHub Copilot Instructions:**
- Comprehensive coding standards in markdown format
- Optimized for GitHub Copilot integration
- Single file with all standards consolidated

## Recent Changes

### v2025.09.08 Update
- **README Enhancement**: Added comprehensive badges and updated project structure
- **Project Structure Documentation**: Enhanced with detailed `.cursor/rules` directory structure
- **Rule Files Overview**: Added clear distinction between Cursor AI and GitHub Copilot formats

### v2025.09.05 Update - Clarity Improvements
- **Comprehensive Clarity Review**: Conducted thorough review and improvements across all 11 rule files
- **Header Standardization**: Fixed inconsistent header formats in SDLC and testing standards
- **Content Consolidation**: Removed duplicate content in project standards
- **Simplified Language**: Rewrote complex sentences for better readability
  - Simplified PascalCase naming conventions explanation
  - Clarified JSON streaming semantics with structured format options
  - Broke up run-on sentences in CLI configuration guidance
- **Added Code Examples**: Included practical Python examples for:
  - Multi-parameter method signatures and calls
  - Google-style docstrings with Args/Returns/Raises sections
- **Enhanced Documentation**: Made documentation standards more specific with clear guidelines
- **Improved Technical Writing**: Enhanced type annotation guidance and import organization
- **Better Structure**: Organized content with consistent bullet points and clearer hierarchies

### v2025.09.04 Update - Major Expansion
- **New Rule Categories**: Added two new rule categories to expand coverage
  - CLI Standards: Command-line interface best practices for text input/output and JSON support
  - Security Standards: Comprehensive secure coding guidelines covering OWASP principles, input validation, authentication, encryption, and secure API design
- **Rule Count Update**: Expanded from 9 to 11 rule categories total
- **Standards Refinement**: Enhanced documentation and clarified guidelines across multiple rule files
- **README Enhancement**: Updated overview and added comprehensive documentation for new rule categories
- **Documentation Accuracy**: Corrected project standards to include missing folders (specs/, e2e/) and files (README-details.md, CHANGELOG.md)
- **Standards Alignment**: Updated SDLC date format and added missing library development requirements
- **Style Standards Enhancement**: Expanded magic constants guidance to include module/function level fallbacks

### v2025.09.03 Update - Design Standards Enhancement
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

### v2025.09.02 Update - Standardization
- **Rule File Renaming**: Standardized rule file naming convention for consistency
  - `code-design.mdc` → `design-standards.mdc`
  - `code-style.mdc` → `style-standards.mdc`
  - `development-approach.mdc` → `sdlc-standards.mdc`
  - `naming-conventions.mdc` → `naming-standards.mdc`
- **Python Standards Enhancement**: Added import sorting guidelines
  - Sort imports grouped by: standard libraries → third-party libraries → local libraries
  - Within each group, sort alphabetically
- **README Updates**: Updated section headers to match new naming convention

### Roadmap
- **Future Enhancements**: Planning additional rule categories for specialized domains
- **Tool Integration**: Expanding support for additional AI coding assistants
- **Community Contributions**: Welcome contributions and feedback on standards evolution
