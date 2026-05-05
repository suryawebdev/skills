Generate comprehensive tests for the file or function specified in $ARGUMENTS.

If $ARGUMENTS is empty, ask which file or function to test.

Steps:
1. Read the target file thoroughly
2. Identify the testing framework already used in this project (Jest, JUnit, Jasmine, pytest, etc.) by checking package.json, pom.xml, or existing test files
3. Find existing test files for this module (if any) to match the style and structure

Then generate tests covering:

**Happy path**
- The primary use case with valid inputs
- All significant branches that return success

**Edge cases**
- Empty inputs, null/undefined, zero values
- Boundary values (min/max, first/last element)
- Large inputs if relevant

**Error cases**
- Invalid inputs that should throw or return errors
- External dependency failures (mock them)
- Authorization/permission failures if applicable

**Rules:**
- Use the exact testing framework and assertion style already in this project — do not introduce a new one
- Mock external dependencies (DB, HTTP calls, file system) — do not hit real services
- Each test has a single, clear assertion focus
- Test names read as plain English: `should return 404 when user not found`
- No redundant tests — if two tests cover the same path, keep only the cleaner one
- Add a comment only when the scenario being tested is non-obvious

Place the generated tests in the correct location for this project's test structure.
