```markdown
# xget Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches you the core development patterns and workflows used in the `xget` JavaScript repository. You'll learn about the project's coding conventions, commit message style, file organization, and how to run and write tests using Vitest. This guide is ideal for contributors or anyone looking to maintain consistency within the codebase.

## Coding Conventions

### File Naming
- Use **camelCase** for file names.
  - Example: `myUtility.js`, `getData.test.js`

### Import Style
- Use **relative imports** for modules within the project.
  - Example:
    ```js
    import { fetchData } from './fetchData.js';
    ```

### Export Style
- Use **named exports** exclusively.
  - Example:
    ```js
    // fetchData.js
    export function fetchData(url) {
      // ...
    }
    ```

### Commit Messages
- Follow the **Conventional Commits** specification.
- Use the `perf` prefix for performance-related changes.
- Keep commit messages concise (average: 44 characters).
  - Example:
    ```
    perf: optimize data fetching logic
    ```

## Workflows

### Running Tests
**Trigger:** When you want to verify code correctness or before submitting a pull request  
**Command:** `/run-tests`

1. Ensure you have all dependencies installed (`npm install`).
2. Run the test suite using Vitest:
    ```bash
    npx vitest
    ```
3. Review the output for passing and failing tests.

### Writing Tests
**Trigger:** When adding new features or fixing bugs  
**Command:** `/write-test`

1. Create a new test file alongside your module, using the pattern `*.test.js`.
2. Import the function(s) you want to test using a relative import.
3. Use Vitest's `test` and `expect` functions to define your tests.
    ```js
    // fetchData.test.js
    import { fetchData } from './fetchData.js';
    import { test, expect } from 'vitest';

    test('fetchData returns data', async () => {
      const data = await fetchData('https://api.example.com');
      expect(data).toBeDefined();
    });
    ```
4. Run the tests to ensure they pass.

## Testing Patterns

- All tests are written in files matching the pattern `*.test.js`.
- Tests use the **Vitest** framework.
- Each test imports the module under test via a relative path.
- Example test structure:
    ```js
    import { myFunction } from './myFunction.js';
    import { test, expect } from 'vitest';

    test('myFunction returns expected value', () => {
      expect(myFunction(2)).toBe(4);
    });
    ```

## Commands
| Command      | Purpose                                    |
|--------------|--------------------------------------------|
| /run-tests   | Run the full test suite using Vitest        |
| /write-test  | Create a new test file for a module         |
```