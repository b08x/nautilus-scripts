```markdown
# nautilus-scripts Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches you the development patterns, coding conventions, and workflows used in the `nautilus-scripts` TypeScript repository. The project organizes and manages scripts for the Nautilus file manager, with a focus on modularity, internationalization, and maintainability. You'll learn how to add new scripts, handle translations, write tests, and follow the established code style.

## Coding Conventions

- **File Naming:**  
  Use camelCase for file and directory names.  
  _Example:_  
  ```
  documentParser.ts
  pdfTools/
  ```

- **Import Style:**  
  Use relative imports for modules.  
  _Example:_  
  ```typescript
  import { parseDocument } from './documentParser';
  ```

- **Export Style:**  
  Use named exports for functions and constants.  
  _Example:_  
  ```typescript
  export function processPdf(file: string): void { ... }
  ```

- **Commit Messages:**  
  Use prefixes such as `feat`, `refactor`, `i18n`, `chore`.  
  _Example:_  
  ```
  feat: add PDF merge script
  refactor: update document parser logic
  i18n: add Spanish translations for PDF tools
  chore: bump version to 1.2.3
  ```

## Workflows

### Add New Script Workflow
**Trigger:** When you want to add a new script/tool to the Nautilus scripts collection.  
**Command:** `/add-script`

1. **Create the Script:**  
   Add a new script file in the appropriate category directory (e.g., `Document/PDF: Tools/`).
   ```typescript
   // Document/PDF: Tools/mergePdfs.ts
   export function mergePdfs(files: string[]): string { ... }
   ```

2. **Add i18n Strings:**  
   Add a message for the new script in all `.po` translation files and update the template.
   ```
   # .po/en_template.pot
   msgid "mergePdfs"
   msgstr "Merge PDFs"
   ```

3. **Update/Add Tests:**  
   Add or update tests for the new script in `.helpers/.unit-tests-scripts.sh`.
   ```bash
   # .helpers/.unit-tests-scripts.sh
   ./Document/PDF: Tools/mergePdfs.test.sh
   ```

4. **Bump Version:**  
   Update the version in `.common-functions.sh` and `install.sh`.
   ```bash
   # .common-functions.sh
   VERSION="1.2.4"
   # install.sh
   VERSION="1.2.4"
   ```

## Testing Patterns

- **Test File Naming:**  
  Test files follow the `*.test.*` pattern, typically placed alongside or near the scripts they test.
  _Example:_  
  ```
  mergePdfs.test.ts
  ```

- **Testing Framework:**  
  No specific framework detected; tests may be shell scripts or TypeScript test files.

- **Test Location:**  
  Tests for scripts are referenced or implemented in `.helpers/.unit-tests-scripts.sh`.

## Commands

| Command      | Purpose                                                      |
|--------------|--------------------------------------------------------------|
| /add-script  | Add a new Nautilus script, integrate i18n, tests, and version bump |

```