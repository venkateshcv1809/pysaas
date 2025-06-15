# PySaaS Code Style Guidelines

This document outlines the code style guidelines for the PySaaS project. Adhering to these guidelines ensures consistency, readability, and maintainability across the entire codebase, facilitating collaboration and reducing cognitive load for developers.

---

## 1. Python Specific Guidelines

### a. PEP 8 Compliance

The primary Python style guide is [PEP 8](https://www.python.org/dev/peps/pep-0008/). All Python code in this project MUST comply with PEP 8.

### b. Automatic Formatting (Black & isort)

We use automated tools to ensure PEP 8 compliance and consistent formatting:

- **Black:** An uncompromising Python code formatter. It formats code deterministically.
- **isort:** A Python utility to sort imports alphabetically and automatically separate them into sections.

**Configuration:**

- `pyproject.toml` contains the configurations for Black and isort.
- VS Code is configured to run Black and isort automatically on save.

**Manual execution (if needed):**
`bash
    poetry run black .
    poetry run isort .
    `

### c. Linting (Flake8)

**Flake8** is used for linting. It combines PyFlakes, pycodestyle, and McCabe complexity checker.

**Configuration:**

- Flake8 configuration is also in `pyproject.toml`.
- VS Code integrates Flake8 to show linting errors and warnings.

**Manual execution (if needed):**
`bash
    poetry run flake8 .
    `

### d. Docstrings

All modules, classes, methods, and complex functions MUST have docstrings. We follow the [Google Python Style Guide](https://google.github.io/styleguide/pyguide.html#38-comments-and-docstrings) for docstring format.

**Example:**
```python
def calculate_area(radius: float) -> float:
"""Calculates the area of a circle.

        Args:
            radius: The radius of the circle.

        Returns:
            The area of the circle.
        """
        return 3.14159 * radius * radius
    ```

### e. Type Hinting

All Python code SHOULD use [type hints](https://docs.python.org/3/library/typing.html) for function arguments and return values. This improves readability, enables static analysis, and helps prevent bugs.

### f. Naming Conventions

- **Variables, functions, methods:** `snake_case` (e.g., `user_name`, `get_user_by_id`)
- **Classes:** `CamelCase` (e.g., `UserService`, `User`)
- **Constants:** `UPPER_SNAKE_CASE` (e.g., `MAX_RETRIES`, `DEFAULT_TIMEOUT`)
- **Modules:** `snake_case` (e.g., `user_management.py`)
- **Private members:** Prefix with a single underscore `_private_method` (convention, not enforced)
- **Dunder methods:** Standard Python dunder methods `__init__`, `__str__` etc.

### g. Imports

- Imports should be grouped in the following order (handled by isort):
  1.  Standard library imports
  2.  Third-party imports
  3.  Local application imports
- Always use absolute imports (e.g., `from services.auth.models import User`)
- Avoid wildcard imports (`from module import *`)

### h. Error Handling

- Use exceptions for exceptional conditions.
- Prefer specific exceptions over broad ones.
- Do not suppress exceptions silently.
- Use `try...except...finally` blocks for resource management and cleanup.

## 2. General Code Guidelines (Applicable to all languages/files)

### a. Readability

- Write clear, concise, and self-documenting code.
- Avoid overly clever or complex solutions where a simpler alternative exists.
- Break down large functions/methods into smaller, single-responsibility units.

### b. Comments

- Use comments to explain _why_ certain decisions were made, not _what_ the code does (unless the "what" is non-obvious).
- Keep comments up-to-date with code changes.
- Remove commented-out code.

### c. Consistency

- Maintain consistent style, patterns, and naming conventions throughout the project.
- If a specific pattern is established in a module, follow it.

### d. No Magic Numbers/Strings

- Use named constants instead of hardcoding "magic" values or strings.

---

_This document is part of the foundational project setup for PySaaS._
