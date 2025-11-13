# CLAUDE.md - AI Assistant Guide for Playground Repository

**Last Updated:** 2025-11-13
**Repository:** harijaiswal29/Playground
**Primary Language:** Python 3.8+

## Table of Contents
1. [Repository Overview](#repository-overview)
2. [Codebase Structure](#codebase-structure)
3. [Development Workflows](#development-workflows)
4. [CI/CD Pipeline](#cicd-pipeline)
5. [Git Conventions](#git-conventions)
6. [Python Development Guidelines](#python-development-guidelines)
7. [Testing Standards](#testing-standards)
8. [AI Assistant Guidelines](#ai-assistant-guidelines)

---

## Repository Overview

This is a Python-based playground repository designed for experimentation and learning. The repository uses modern CI/CD practices with automated linting, testing, and deployment workflows.

**Key Characteristics:**
- **Purpose:** Development playground and experimentation
- **Language:** Python 3.8
- **CI/CD:** GitHub Actions with lint, test, and deploy stages
- **Testing:** pytest framework
- **Linting:** flake8 code style enforcement

---

## Codebase Structure

```
Playground/
├── .github/
│   └── workflows/
│       └── ci-cd.yml        # GitHub Actions CI/CD pipeline
├── test2.txt                 # Sample text file
└── CLAUDE.md                 # This file - AI assistant guide
```

### Directory Purposes

- **`.github/workflows/`**: Contains GitHub Actions workflow definitions
- **Root directory**: Currently minimal, expected to contain Python source files, tests, and configuration

### Expected Future Structure

Based on the CI/CD configuration, the repository is expected to grow with:
- Python source files (`.py`)
- Test files (likely in a `tests/` directory)
- Requirements/dependencies file (`requirements.txt` or `pyproject.toml`)
- README.md for user-facing documentation

---

## Development Workflows

### Standard Development Flow

1. **Create Feature Branch**
   - AI assistants use branches prefixed with `claude/claude-md-` followed by session ID
   - Example: `claude/claude-md-mhxucit7m2vq9onk-01EJTaQ943Grc7XLaC5mYdMJ`

2. **Make Changes**
   - Write clean, well-documented Python code
   - Follow PEP 8 style guidelines
   - Include docstrings for functions and classes

3. **Test Locally**
   - Run `flake8 .` to check code style
   - Run `pytest` to execute tests
   - Fix any issues before committing

4. **Commit and Push**
   - Write clear, descriptive commit messages
   - Push to the feature branch: `git push -u origin <branch-name>`
   - CI/CD pipeline runs automatically on push

5. **Create Pull Request**
   - After CI passes, create PR for review
   - Ensure all checks are green

---

## CI/CD Pipeline

The repository uses GitHub Actions for continuous integration and deployment.

### Pipeline Configuration (`.github/workflows/ci-cd.yml`)

**Triggers:**
- Push events to any branch
- Pull request events

**Jobs:**

#### 1. Lint Job
- **Purpose:** Enforce code quality and style
- **Tool:** flake8
- **Python Version:** 3.8
- **Command:** `flake8 .`

#### 2. Test Job
- **Purpose:** Run automated tests
- **Tool:** pytest
- **Python Version:** 3.8
- **Command:** `pytest`
- **Runs:** Parallel with lint job

#### 3. Deploy Job
- **Purpose:** Deploy the application/model
- **Dependency:** Requires test job to pass
- **Current Status:** Placeholder (needs deployment script)
- **Command:** `echo "Deploying the model..."`

### CI/CD Best Practices

1. **Always ensure CI passes** before creating pull requests
2. **Fix lint errors immediately** - they indicate style violations
3. **All tests must pass** - deploy job won't run otherwise
4. **Add tests for new features** to maintain coverage
5. **Update deployment script** in deploy job when needed

---

## Git Conventions

### Branch Naming

**AI Assistant Branches:**
- Format: `claude/claude-md-<session-id>`
- Example: `claude/claude-md-mhxucit7m2vq9onk-01EJTaQ943Grc7XLaC5mYdMJ`
- Critical: Branch must start with `claude/` and end with matching session ID
- Failure to follow this convention results in 403 HTTP errors on push

**Human Developer Branches:**
- Feature branches: `feature/<feature-name>`
- Bug fixes: `bugfix/<issue-description>`
- Hotfixes: `hotfix/<issue-description>`

### Commit Messages

Follow conventional commit format:

```
<type>: <short description>

<optional detailed description>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, missing semicolons, etc.)
- `refactor`: Code refactoring
- `test`: Adding or modifying tests
- `chore`: Maintenance tasks

**Examples:**
```
feat: Add user authentication module
fix: Resolve edge case in data validation
docs: Update README with installation instructions
test: Add unit tests for helper functions
```

### Push/Pull Best Practices

**Pushing:**
- Always use: `git push -u origin <branch-name>`
- Retry up to 4 times on network errors with exponential backoff (2s, 4s, 8s, 16s)

**Fetching/Pulling:**
- Prefer specific branch fetches: `git fetch origin <branch-name>`
- For pulls: `git pull origin <branch-name>`
- Retry up to 4 times on network failures with exponential backoff

---

## Python Development Guidelines

### Python Version
- **Minimum:** Python 3.8
- **Recommended:** Use the latest stable Python 3.x version

### Code Style
- **Standard:** PEP 8
- **Enforcer:** flake8
- **Line Length:** 79 characters (PEP 8 default, configurable)

### Code Quality Checklist

- [ ] All functions have docstrings
- [ ] Complex logic is commented
- [ ] Variable names are descriptive
- [ ] No unused imports
- [ ] No print statements in production code (use logging)
- [ ] Error handling is implemented where needed
- [ ] Type hints are used for function signatures (recommended)

### Dependencies Management

When adding dependencies:
1. Create `requirements.txt` if it doesn't exist
2. Pin versions for reproducibility: `package==1.2.3`
3. Update CI/CD workflow to install dependencies
4. Document any system-level dependencies

---

## Testing Standards

### Testing Framework
- **Tool:** pytest
- **Location:** Tests should be in a `tests/` directory or use `test_*.py` naming

### Test Coverage Goals
- **Minimum:** 80% code coverage
- **Ideal:** 90%+ for critical paths
- **Tool:** pytest-cov (recommended to add)

### Writing Tests

**File Naming:**
- `test_<module_name>.py`

**Function Naming:**
- `test_<functionality_description>()`

**Structure:**
```python
def test_feature_does_expected_behavior():
    # Arrange
    input_data = setup_test_data()

    # Act
    result = function_under_test(input_data)

    # Assert
    assert result == expected_output
```

### Test Types to Include

1. **Unit Tests:** Test individual functions/methods
2. **Integration Tests:** Test component interactions
3. **Edge Cases:** Test boundary conditions
4. **Error Handling:** Test exception scenarios

---

## AI Assistant Guidelines

### When Working on This Repository

#### Initial Analysis
1. Check current repository state with `git status`
2. Review recent commits with `git log --oneline -10`
3. Understand the task requirements fully before coding
4. Check if tests exist and understand their structure

#### Code Development
1. **Read before writing:** Always read existing files before modifying
2. **Follow existing patterns:** Match the style and structure of existing code
3. **Write tests first:** TDD approach when adding new features
4. **Keep it simple:** Prefer clarity over cleverness

#### Quality Assurance
1. Run `flake8 .` after code changes
2. Run `pytest` to verify tests pass
3. Check for security vulnerabilities (no hardcoded secrets, SQL injection, XSS, etc.)
4. Verify changes don't break existing functionality

#### Git Operations
1. Always develop on the designated `claude/` branch
2. Never push to main/master without explicit permission
3. Use clear, descriptive commit messages
4. Implement retry logic for network operations

#### Communication
1. Explain what you're doing and why
2. Provide file paths with line numbers: `file.py:42`
3. Highlight any concerns or potential issues
4. Ask for clarification when requirements are ambiguous

#### Security Considerations
1. Never commit secrets, API keys, or credentials
2. Validate and sanitize all user inputs
3. Use parameterized queries for database operations
4. Implement proper error handling without exposing sensitive information
5. Follow OWASP Top 10 security guidelines

### Tools and Commands Reference

**Useful Commands:**
```bash
# Run linter
flake8 .

# Run tests
pytest

# Run tests with coverage
pytest --cov=.

# Check Python version
python --version

# Install dependencies
pip install -r requirements.txt

# List branches
git branch -a

# View git status
git status

# Push with retry logic
git push -u origin <branch-name>
```

### Common Tasks

#### Adding a New Python Module
1. Create the module file in appropriate directory
2. Add docstrings and type hints
3. Create corresponding test file in `tests/`
4. Write tests for the new functionality
5. Run flake8 and pytest
6. Commit with descriptive message

#### Fixing a Bug
1. Understand the bug and reproduce it
2. Write a failing test that captures the bug
3. Fix the bug in the source code
4. Verify the test now passes
5. Check for similar issues in codebase
6. Commit with fix description

#### Updating Dependencies
1. Update `requirements.txt`
2. Test locally with new versions
3. Update CI/CD workflow if needed
4. Verify CI pipeline passes
5. Document any breaking changes

---

## Additional Resources

### Python Resources
- [PEP 8 Style Guide](https://pep8.org/)
- [pytest Documentation](https://docs.pytest.org/)
- [flake8 Documentation](https://flake8.pycqa.org/)

### Git Resources
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Git Best Practices](https://git-scm.com/book/en/v2)

### Security Resources
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [Python Security Best Practices](https://python.readthedocs.io/en/latest/library/security_warnings.html)

---

## Changelog

### 2025-11-13
- Initial creation of CLAUDE.md
- Documented repository structure and CI/CD pipeline
- Established Python development guidelines
- Defined git conventions and workflows
- Added AI assistant operational guidelines

---

## Notes for Future Updates

This document should be updated when:
- New workflows or processes are established
- Project structure changes significantly
- New tools or frameworks are adopted
- CI/CD pipeline is modified
- New conventions are agreed upon

**Update Frequency:** Review quarterly or after major changes
