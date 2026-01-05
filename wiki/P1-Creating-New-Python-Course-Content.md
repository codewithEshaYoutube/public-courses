# [P1] Creating New Content for the Python Course

## Overview

This guide is designed for **Public Course Administrators** who need to create new content for the Python course (`Curso-de-Python-FutureLabs`). This documentation covers the complete process from planning to deployment.

## Prerequisites

Before creating new content, ensure you have:

- Admin access to the omegaUp platform
- Write access to this GitHub repository
- Understanding of the course structure (see [DOCUMENTATION.md](../DOCUMENTATION.md))
- Python 3, Pip, Git, and Pipenv installed (see [Getting Started](../DOCUMENTATION.md#getting-started))

## Understanding the Course Structure

The Python course (`Curso-de-Python-FutureLabs`) is organized into assignments, each containing problems. The structure follows this pattern:

```
Courses/
└── Curso-de-Python-FutureLabs/
    ├── intro_y_variables/
    │   └── python_2/
    │       ├── settings.json
    │       ├── settings.distrib.json
    │       └── statements/
    │           └── es.markdown
    ├── colecciones_de_datos/
    ├── control_de_flujo/
    └── ...
```

Each problem folder contains:
- `settings.json` - Problem configuration (limits, validator, etc.)
- `settings.distrib.json` - Distribution settings
- `statements/` - Problem statements (markdown files, typically `es.markdown` for Spanish)

## Step-by-Step Guide

### Step 1: Plan Your Content

Before creating new content, consider:

1. **Learning Objectives**: What should students learn from this content?
2. **Assignment Placement**: Which assignment should this content belong to, or should you create a new assignment?
3. **Problem Type**: Is this a new problem, or are you adding content to an existing assignment?
4. **Content Format**: Will this be a problem with test cases, or educational content?

### Step 2: Create the Problem on omegaUp.com

1. Log in to [omegaUp.com](https://omegaup.com) with your admin account
2. Navigate to the problem creation page
3. Create a new problem with:
   - A descriptive alias (e.g., `python_10` for the 10th Python problem)
   - A clear title
   - Problem statement in Markdown format
   - Test cases (input/output pairs)
   - Time and memory limits appropriate for Python
   - Validator settings

**Recommended Settings for Python Problems:**
- Time Limit: 1-3 seconds (depending on complexity)
- Memory Limit: 64-128 MB
- Validator: Usually "token" for standard problems
- Language: Python 3

### Step 3: Add Problem to Course Assignment

1. Go to the course management page for `Curso-de-Python-FutureLabs`
2. Navigate to the target assignment (or create a new one)
3. Add the problem to the assignment with appropriate points

**Important**: Grant admin permissions to the `CourseBot` user for the problem. This is required for the problem content to be synced to the GitHub repository.

### Step 4: Sync Problem to GitHub Repository

After creating the problem on omegaUp and adding it to the course:

1. **Option A: Automatic Sync (Recommended)**
   - Checkout the `sync-course` branch:
     ```bash
     git checkout sync-course
     ```
   - Reset the branch with main:
     ```bash
     git reset --hard origin/main
     ```
   - Push to trigger sync:
     ```bash
     git push --force
     ```
   - The GitHub Action will automatically download and add the problem to the repository

2. **Option B: Manual Sync via Pull Request**
   - Create a pull request targeting the `sync-course` branch
   - Update `sync-course.json` to request synchronization
   - Once merged, the GitHub Action will sync the content

### Step 5: Verify Content in Repository

After the sync completes:

1. Verify the problem folder exists in the correct assignment directory
2. Check that all files are present:
   - `settings.json`
   - `settings.distrib.json`
   - `statements/es.markdown` (or other language files)
3. Review the problem statement for formatting and correctness

### Step 6: Edit Content Locally (Optional)

If you need to modify the problem content:

1. Make changes directly in the problem folder
2. For statement edits: Modify `statements/es.markdown`
3. For settings changes: Modify `settings.json` or `settings.distrib.json`
4. Commit and push to the `main` branch

**Note**: Changes pushed to `main` will be synced back to omegaUp.com automatically.

## Creating New Assignments

If you need to create a completely new assignment:

1. **On omegaUp.com:**
   - Create a new assignment in the course
   - Set the assignment alias (this will be the folder name)
   - Configure assignment settings (start date, end date, etc.)

2. **Sync to Repository:**
   - Follow the sync process described in Step 4
   - The new assignment folder will be created automatically

3. **Verify Structure:**
   - Ensure the assignment folder follows the naming convention
   - Check that `course_settings.json` is updated if needed

## Best Practices

### Content Quality

- **Clear Problem Statements**: Write clear, well-formatted problem statements
- **Appropriate Difficulty**: Match problem difficulty to the assignment level
- **Good Test Cases**: Include edge cases and various scenarios
- **Educational Value**: Ensure problems teach relevant Python concepts

### File Organization

- **Consistent Naming**: Use consistent aliases (e.g., `python_X` for sequential problems)
- **Proper Structure**: Follow the existing folder structure
- **Language Files**: Use `es.markdown` for Spanish content, add other languages as needed

### Documentation

- **Update README**: If creating a new assignment, consider updating course documentation
- **Comments**: Add comments in JSON files if non-standard settings are used

## Troubleshooting

### Problem Not Syncing

- **Check Permissions**: Ensure `CourseBot` has admin permissions for the problem
- **Verify Branch**: Make sure you're working with the `sync-course` branch
- **Check GitHub Actions**: Review the Actions tab for sync errors

### Content Not Appearing

- **Wait for Sync**: GitHub Actions may take a few minutes to complete
- **Check Logs**: Review the sync action logs for errors
- **Verify Path**: Ensure the problem is in the correct assignment folder

### Formatting Issues

- **Markdown Syntax**: Verify Markdown syntax in problem statements
- **JSON Validity**: Ensure JSON files are valid (use a JSON validator)
- **Encoding**: Use UTF-8 encoding for all text files

## Additional Resources

- [Main Documentation](../DOCUMENTATION.md)
- [Syncing Content Guide](../DOCUMENTATION.md#syncing-content-from-omegaupcom-to-this-repository)
- [Modifying Problems Guide](../DOCUMENTATION.md#modifying-existing-problems-content)
- [omegaUp Platform Documentation](https://omegaup.com/docs/)

## Support

If you encounter issues or need assistance:

1. Check the [GitHub Issues](https://github.com/omegaup/public-courses/issues)
2. Review the [Comprehensive Documentation](../DOCUMENTATION.md)
3. Contact the course administrators or repository maintainers

---

**Last Updated**: 2026
**Maintained By**: Public Course Administrators
