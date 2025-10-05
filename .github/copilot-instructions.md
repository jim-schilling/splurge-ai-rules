# GitHub Copilot Instructions

This document contains coding standards and guidelines for the splurge-ai-rules project. These instructions help maintain consistency and quality across the codebase.

## Software Development Lifecycle Standards
- Follow Research, Plan, and Implement lifecycle.
- Document research in docs/research/research-[description]-[yyyy-MM-dd]-[sequence].md.
- Document action plans in docs/plans/plan-[description]-[yyyy-MM-dd]-[sequence].md.
- Document requirements and specifications in docs/specs/spec-[description]-[yyyy-MM-dd]-[sequence].md.
- Document issues/bugs in docs/issues/issue-[description]-[yyyy-MM-dd]-[sequence].md.
- Document apis in docs/apis/api-[description]-[yyyy-MM-dd]-[sequence].md.
- Document notes in docs/notes/note-[description]-[yyyy-MM-dd]-[sequence].md.
- Document configuration in docs/configuration/configuration-[description]-[yyyy-MM-dd]-[sequence].md.
- Research shall include exploration of existing solutions, libraries, and tools.
- Plans shall detail requirements, acceptance criteria, testing strategy (e.g. TDD and BDD), and a step-by-step implementation guide.
- Each action plan shall be sub-divided into stages (e.g. Stage-1, Stage-2), while stages are subdivided into tasks (e.g. Task-[Stage].1, Task-[Stage].2).
- Implementation lifecycle shall always: code failing tests, then implement code, then run tests, then iteratively refactor and run tests until all tests pass.
- Every feature must start as a standalone library before integration:
  - Develop features as independent, reusable library components first
  - Only integrate into larger applications after proving standalone functionality
- Software tools, primary libraries, data tools, and development tools must expose their functionality through a CLI. Other software functionality may omit a CLI if appropriate.
- If in doubt, prompt user for clarification and mark as [NEEDS CLARIFICATION].
- Always ask for user confirmation before making significant changes.
- Always ask for user confirmation before deleting files or data.
- Always ask for user confirmation before overwriting existing files.
- Use git for version control with feature branches and pull requests.
- Write clear, concise commit messages in the imperative mood (e.g., "Add feature", "Fix bug").

## Project Organization Standards
- Create top-level folder: docs/.
- Create project README.md which summarizes the project.
- Create project CHANGELOG.md which details changes for each version/feature-branch.
- Create docs/README-DETAILS.md which details project features, usage, errors, dependencies, etc.
- Create sub-folders under docs/: research/, plans/, specs/, issues/, apis/, notes/, configuration/.
- For code projects, create top-level folders: tests/, examples/, scripts/, and tools/.
- For code projects, create sub-folders under tests/: unit/, integration/, e2e/.
- For Python projects, create modern, standardized pyproject.toml.
- For Python projects, use CalVer versioning.
- License shall be MIT.
- Author and Maintainer shall be Jim Schilling.
- Project base url shall be http://github.com/jim-schilling/[REPOSITORY].

## Design Standards
- Follow SOLID (Single Responsibility, Open-Closed, Liskov Substitution, Interface Segregation, Dependency Inversion) principles.
- Follow DRY (Don't Repeat Yourself) principle.
- Follow BDD/TDD (Behavior/Test Driven Development) practices.
- Follow MVP (Minimum Viable Product) approach.
- Follow KISS (Keep It Simple, Stupid) principle.
- Follow PoLA (Principle of Least Authority).
- Follow YAGNI (You Aren't Gonna Need It) principle.
- Prefer composition over inheritance.
- Prefer encapsulation.
- Prefer separation of concerns.
- Prefer to fail fast.
- Follow the Law of Demeter - objects should only interact with their immediate dependencies.
- Prioritize error handling using appropriate mechanisms (exceptions, return values, Result types, or callbacks).
- Use guard clauses to handle preconditions and invalid state early.
- Avoid side effects in module-level code.
- Place the happy path (main successful execution flow) last in the function.
- Use guard clauses and early returns instead of complex if-else chains.
- Prefer iteration and modularization over code duplication.
- Prefer simple, straightforward design over over-engineering.
- Private methods should accept necessary data as parameters rather than directly accessing instance variables.
- Use domain-specific custom exceptions for public APIs.
- Use native/built-in exceptions for low-level APIs, where appropriate.
- Prioritize code clarity while maintaining reasonable efficiency.

## Python Standards
- Always add type annotations to function and method signatures.
- Add type annotations to variables when it improves code clarity.
- Prefer | instead of Optional or Union.
- Code concise, technical, Python that adheres to PEP 8, PEP 604, and PEP 585.
- Code to modern Python standards targeting version 3.10 or later.
- Use absolute import paths, where appropriate.
- When possible, place imports at top of module.
- Group and sort imports: standard libraries, then third-party libraries, then local libraries. Sort alphabetically within each group.
- Use separate statements for multiple context managers instead of nesting them.
- Use mypy for type validation.
- Use ruff for style, formatting, and security validation.
- Place module-level constants in UPPER_SNAKE_CASE.
- Place a single space before and after operators (=, +, -, *, /, ==, !=, <, >, <=, >=, etc.).
- Place a single space after commas in lists, tuples, and function parameters.
- Use 4 spaces for indentation, no tabs.
- Use UTF-8 encoding without BOM for all text files.
- Use f-strings for string interpolation.
- Use triple double quotes for docstrings and comments.
- Use single quotes for string literals, except when the string contains single quotes.
- Add a DOMAINS list at the top of each module indicating associated domains (e.g., DOMAINS = ["generator", "helpers"]).
- Add a package level constant __domains__ listing all associated domains for the package in __init__.py.
- Use exceptions for error handling, not return codes.
- Use __all__ to define public API of modules.
- Use logging module for logging, not print statements.
- Use pathlib for file and path operations.
- Use context managers for file operations.
- Use list comprehensions and generator expressions for creating lists and iterators.
- Use enumerate() when needing both index and value in loops.
- Use zip() to iterate over multiple iterables in parallel.

## Naming Standards
- Use descriptive variable names with auxiliary verbs (e.g. is_active, has_permission).
- Use PascalCase for class, enum, and dataclass names (e.g., DsvReader, CsvWriter, TransformXmlToJson).
- For SQL, prefer lower case column names.
- Prefer upper snake case for constant names.
- Environment variable names MUST use a project prefix [A-Z][A-Z0-9_]*_ (e.g., SPLURGE_DSV_).
- Test module names should mirror the domains associated with the modules, where DOMAINS is a list of the module's domain names.
 - e.g., for a module that has DOMAINS = ['dsv', 'csv'], the test module should be named test_csv_dsv_[SEQUENCE].py, where [SEQUENCE] is a unique identifier for the test module.
- Test class names should mirror the class being tested, prefixed with Test.
 - e.g., for a class named CsvReader, the test class should be named TestCsvReader.
- Test method names should be descriptive and follow the pattern test_[condition]_[expectedResult].
 - e.g., test_read_valid_csv_returns_data, test_read_invalid_csv_raises_exception.
- Use verbs for function and method names (e.g., get_data, process_file).
- Use nouns for class and module names (e.g., DataProcessor, file_utils).
- Use singular nouns for class names (e.g., User, Product).
- Use plural nouns for collection names (e.g., Users, Products).
- Test module names should be prefixed with test_ (e.g., test_csv_reader.py).
- For every code module, there shall be at least one corresponding test module in named test_[module-path]_basic.py, where [module-path] is the module path with dots replaced by underscores, the path will not contain the package name.
 - e.g., for a module named splurge_unittest_to_pytest.converter.helpers, the test module should be named test_converter_helpers_basic.py.

## Method Standards
- Prefer parameters in method signatures and method calls to be listed on separate lines.
- For classmethods, property methods, and class instance method calls with 3 or more parameters, prefer named keywords for default parameters.
- For standard methods and staticmethods calls with 2 or more parameters, prefer named keywords for default parameters.
- For all other method signatures prefer use of keywords for more than 1 parameter.
- If a method signature use keywords, then all default parameters should be keywords.
- For method signatures with more than 2 parameters, place each parameter on a separate line:
  ```python
  def process_data(
      input_file: str,
      output_format: str,
      validate_schema: bool = True
  ) -> dict:
  ```
- For method calls with more than 2 parameters, place each parameter on a separate line:
  ```python
  result = process_data(
      input_file="data.json",
      output_format="ndjson",
      validate_schema=Trues
  )
  ```
- When updating a method or class signature, do not maintain backwards compatibility unless specifically told to do so.

## Style Standards
- Prefer line length max of 120 characters in code modules, except for tests or when to do so would require use of temporary variables.
- Except clauses shall be prefixed with a blank line.
- Prefer separating logical blocks of code with a blank line for visual clarity.
- For Python, for any line continuations, use parentheses only.
- For Python, use ruff for code style, linting, and formatting.
- Avoid magic strings and magic numbers, instead prefer class level constants, otherwise use module/function level constants.

## Documentation Standards
- Add comments before complex logic blocks to explain the "why" and "what".
- Use inline comments sparingly, only for complex or non-obvious code sections.
- Remove outdated comments during refactoring instead of accumulating them.
- Use Google-style docstrings for all public functions, classes, and modules in Python:
  ```python
  def process_data(input_file: str) -> dict:
      """Process input file and return structured data.

      Args:
          input_file: Path to the input file to process

      Returns:
          Dictionary containing processed data

      Raises:
          FileNotFoundError: If input file doesn't exist
      """
  ```

## Testing Standards
- Follow BDD/TDD (Behavior/Test Driven Development) practices.
- Validate behavior of public APIs only.
- Prefer validation using actual data, interfaces, and objects
- Minimize use of mocks, except where appropriate.
- Mock at architectural boundaries (external systems, I/O) but prefer real objects/data for internal logic.
- Ensure tests are isolated and do not depend on external systems or state.
- Each code module must have at least one corresponding test module.
- Unit test shall target 85% code coverage for all public interfaces and methods.
- Combination of unit tests and integration tests shall target 95% code coverage for all public interfaces and methods.
- Prefer tests that are independent, repeatable, and deterministic.
- Prefer shared helpers for common logic.
- Avoid validation of implementation details and private APIs.
- Prefer validation of patterns of text, and avoid exact matching of content and formatting.
- Prefer pytest; pytest-xdist may be used optionally for parallel runs (e.g., -n 4) when desired.
- Prefer pytest-cov for code coverage with parameters --cov=your_package --cov-report=term-missing.
- Prefer pytest-mock for mocking and patching, where appropriate.
- Run pytest with code coverage when asked by user, otherwise skip.
- Place unit tests in tests/unit/ and integration tests in tests/integration/, e2e tests in tests/e2e/, and performance tests in tests/performance/.
- Place test data in tests/data.
- For Python, prefer pure pytest function style tests.
- For Python, prefer use of tmp_path and tmp_path_factory fixtures for temporary files and directories.
- Name test methods as test_[condition]_[expectedResult].
- Each test method should ideally test a single condition and expected result.
- Use fixtures for common setup and teardown logic.
- Use parameterized tests for testing multiple input scenarios.
- Use assertions to validate expected outcomes.
- Prefer tests/unit/* to run to completion within 60 seconds.
- Prefer tests/integration/* to run to completion within 60 seconds.
- Prefer tests/e2e/* to run to run to completion within 60 seconds.
- Prefer tests/performance/* to run to completion within 60 seconds.
- Prefer entire test suite to run to completion within 120 seconds.

## CLI Standards
- MUST accept text input via stdin, arguments or files.
- May accept environment variables for configuration, unless user opts out.
- Sensitive data must use environment variables.
- Environment variable names MUST use a project prefix [A-Z][A-Z0-9_]*_ (e.g., SPLURGE_DSV_).
- Provide --output-format {table,json, and/or ndjson} (default: table).
- When reading from stdin, a file path of - MUST mean "read from stdin".
- Stdout and stderr MUST be UTF-8 encoded without BOM.
- Exit codes: 0 success; 1 generic error; 2 invalid arguments; 130 interrupted (Ctrl+C).
- Flags map by prefix + uppercasing + hyphens→underscores (e.g., --api-token → SPLURGE_DSV_API_TOKEN).
- JSON output formats:
  - `--output-format json`: Output complete JSON arrays, one per line
  - `--output-format ndjson`: Output one JSON object per line (newline-delimited)
  - Never mix JSON with other text on stdout
- If an env var is referenced but missing, fail fast: "Missing required environment variable: <NAME>".
- Redact sensitive data for output, logging, and errors.
- Document defaults in --help output.
- CLI arguments override environment variables.
- Environment variables override built-in defaults.

## Security Standards
- Follow secure coding best practices.
- Validate and sanitize all user inputs to prevent injection attacks (SQL, Shell, XSS, command injection).
- Use parameterized queries and prepared statements for database operations.
- Implement proper authentication and authorization mechanisms.
- Never store sensitive data (passwords, API keys, tokens) in plain text.
- Follow the principle of least privilege for user permissions and API access.
- Implement comprehensive error handling without exposing sensitive information.
- Restrict allowed file types and sizes.
- Use secure random number generators for cryptographic operations.
- Implement proper logging without logging sensitive information.
- Follow OWASP security guidelines and address common vulnerabilities.
- Use environment variables or secure vaults for configuration secrets.
- Implement proper password policies and secure password hashing.
- Follow secure API design principles (proper HTTP methods, versioning, etc.).