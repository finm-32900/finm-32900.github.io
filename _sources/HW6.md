# Homework 6

## Learning Outcomes

- **Contribute to open-source projects:** Gain hands-on experience contributing to a collaborative open-source Python package
- **Practice Git workflows:** Create branches, submit pull requests, and respond to code reviews
- **Conduct code reviews:** Review peer contributions and provide constructive feedback
- **Write production-quality code:** Implement functions with proper documentation, type hints, and unit tests
- **Quantitative finance methods:** Implement practical functions used in quantitative finance, replicating functionality from QuantLib and Bloomberg Terminal

## Assignment Overview

In this assignment, you will contribute to an open-source Python package for quantitative finance: [finm](https://github.com/jmbejara/finm). This package is designed as a learning tool where each student will add useful quantitative finance functions.

You will complete **three distinct tasks**:

1. **Implement a feature** - Solve one issue by implementing a new function
2. **Review two pull requests** - Provide constructive code reviews for two classmates
3. **Respond to reviews** - Address feedback on your own pull request

## Part 0 (not graded)

Before starting the assignment, familiarize yourself with:

- The [finm package repository](https://github.com/jmbejara/finm)
- Review the `README.md` to understand the package structure
- Look at existing merged pull requests to see examples of completed work
- Review the [contributing guidelines](https://github.com/jmbejara/finm/blob/main/CONTRIBUTING.md) (if available)

If you need a refresher on pull requests and code reviews, revisit these GitHub Skills tutorials:
- [Review pull requests](https://github.com/skills/review-pull-requests)
- [Resolve merge conflicts](https://github.com/skills/resolve-merge-conflicts)

## Part 1: Implement a Feature (graded)

### Step 1: Choose an Issue

1. Go to the [Issues page](https://github.com/jmbejara/finm/issues) of the finm repository
2. Browse the available issues labeled `student-assignment`
3. Find an issue that is **not yet assigned** to another student
4. Comment on the issue saying "I would like to work on this issue"
5. Wait for the instructor to assign the issue to you (you will receive a notification)

**Important:** Do not start work until the issue is officially assigned to you to avoid duplicate effort.

**Types of Issues Available:**

Issues fall into several categories. Here are a few examples:

- **QuantLib Replications:** Implement functions that replicate functionality from QuantLib
  - Example: Calculate Black-Scholes option prices from WRDS OptionMetrics data
  - Example: Implement bond pricing with various day count conventions

- **Bloomberg Function Replications:** Implement functions that replicate Bloomberg Terminal functionality
  - Example: Calculate implied repo rate for Treasury futures
  - Example: Compute bond yield-to-maturity with various settlement conventions

- **Data Access Functions:** Create utilities for accessing financial data
  - Example: Pull options data from WRDS OptionMetrics with authentication
  - Example: Fetch Treasury futures data and format for analysis

- **Risk Analytics:** Implement common risk metrics
  - Example: Calculate Greeks for options portfolios
  - Example: Compute Value-at-Risk using various methods

### Step 2: Implement the Function

1. **Fork and clone** the repository (if you haven't already)
2. **Create a new branch** for your work (e.g., `feature/issue-42-black-scholes`)
3. **Implement the function** as described in the issue
   - Add your function to the appropriate module (or create a new one if necessary)
   - Include proper documentation with docstrings (use NumPy or Google style)
   - Add type hints for all parameters and return values
   - Follow PEP 8 style guidelines

4. **Write unit tests** for your function
   - Create tests in the `tests/` directory
   - Include edge cases and validation of expected behavior
   - Ensure all tests pass locally by running `pytest`

5. **Update documentation** if needed
   - Add examples in the docstring
   - Update README.md if your function is particularly noteworthy

### Step 3: Submit a Pull Request

1. **Push your branch** to your fork
2. **Open a pull request** against the main repository
   - Use a clear title: "Fix #[issue-number]: [brief description]"
   - Reference the issue in the PR description using "Closes #[issue-number]" or "Fixes #[issue-number]"
   - Describe what your implementation does
   - Mention any design decisions you made

3. **Ensure CI/CD passes**
   - GitHub Actions will automatically run tests
   - Fix any failures before requesting review

## Part 2: Review Two Pull Requests (graded)

After submitting your pull request, you must review **two other students' pull requests**.

### Finding Pull Requests to Review

1. Go to the [Pull Requests page](https://github.com/jmbejara/finm/pulls)
2. Look for PRs labeled `needs-review` that are **not your own**
3. Choose PRs that don't already have two student reviews

### Conducting a Code Review

Your review should be **thorough and constructive**. Consider:

**Code Quality:**
- Does the code follow PEP 8 style guidelines?
- Are variable and function names clear and descriptive?
- Is the code efficient and well-organized?

**Correctness:**
- Does the implementation match the issue requirements?
- Are there any bugs or edge cases not handled?
- Do the unit tests adequately cover the functionality?

**Documentation:**
- Is there a clear docstring with parameter descriptions?
- Are type hints present and correct?
- Are there usage examples?

**Testing:**
- Do all tests pass?
- Are edge cases tested?
- Are test names descriptive?

### Submitting Your Review

1. **Add review comments** on specific lines of code where appropriate
2. **Write a summary review** with overall feedback
3. **Choose a review status:**
   - "Approve" if the code is ready to merge
   - "Request changes" if fixes are needed (be specific about what needs changing)
   - "Comment" if you have suggestions but no blocking issues

4. Be professional and constructive in your feedback

## Part 3: Respond to Reviews (graded)

Once your pull request receives reviews, you must:

1. **Read all review comments carefully**
2. **Respond to each comment:**
   - If you agree with a suggestion, implement it and reply "Fixed in [commit hash]"
   - If you disagree, explain your reasoning politely and professionally
   - Ask clarifying questions if feedback is unclear

3. **Push new commits** addressing the feedback
4. **Request re-review** after making substantial changes

The instructor will make the final decision on merging your pull request.

## Grading Criteria

This assignment will be graded on:

1. **Implementation Quality (40%)**
   - Correctness of the implemented function
   - Code quality and adherence to style guidelines
   - Completeness of unit tests
   - Quality of documentation

2. **Code Reviews (30%)**
   - Thoroughness of your reviews (15% each)
   - Constructiveness and professionalism of feedback
   - Quality of suggestions and insights

3. **Response to Feedback (20%)**
   - Responsiveness to review comments
   - Quality of revisions
   - Professionalism in discussions

4. **Process (10%)**
   - Following the proper Git workflow
   - Timely completion of tasks
   - Proper use of GitHub features (issue references, labels, etc.)

## Deadlines

- **Issue selection:** [TBD]
- **Initial pull request submission:** [TBD]
- **Code reviews completed:** [TBD]
- **Final revisions submitted:** [TBD]

## Tips for Success

- **Start early** - Don't wait until the last minute
- **Ask questions** - Use the course discussion board if you're stuck
- **Test thoroughly** - Run `pytest` frequently as you develop
- **Be respectful** - Code reviews should be helpful, not harsh
- **Iterate** - It's normal for pull requests to go through several rounds of review
- **Read existing code** - Look at merged PRs to understand the codebase style

## Common Issues and Solutions

### My tests pass locally but fail on GitHub Actions
- Make sure you've committed all necessary files
- Check that you haven't hardcoded any local paths
- Verify that all dependencies are listed in `requirements.txt` or `pyproject.toml`

### How do I handle merge conflicts?
- Pull the latest changes from the main branch
- Resolve conflicts in your local branch
- See: [GitHub's guide on resolving merge conflicts](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts)

### What if someone is working on the issue I wanted?
- Check the Issues page for other unassigned issues
- If all issues in your area of interest are taken, ask the instructor

### Can I work with a partner?
- No, each student must complete their own issue
- However, you can (and should) help each other through discussion and code review

## Additional Resources

- [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/)
- [Python Type Hints](https://docs.python.org/3/library/typing.html)
- [pytest documentation](https://docs.pytest.org/)
- [NumPy docstring guide](https://numpydoc.readthedocs.io/en/latest/format.html)
- [PEP 8 Style Guide](https://pep8.org/)
