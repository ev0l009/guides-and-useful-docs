# 🚀 Professional Git & GitHub Collaboration Workflow

> 🎯 Mission
> Master the complete collaborative development cycle: from planning and writing code to testing, peer review, merging, and final integration.
>
> **The Golden Rule:** Never treat code as finished just because it runs on your machine. It must satisfy requirements, pass appropriate tests, survive review, and integrate correctly with the rest of the application.

---

# 🗂️ PART 1 — Repository Setup & Task Planning

## 📁 Step 1: Prepare the Repository

Before writing code, establish a clean and understandable project structure.

```text
project/
├── main.py
├── README.md
├── .gitignore
├── requirements.txt
├── services/
│   ├── __init__.py
│   └── ...
├── tests/
│   └── ...
└── docs/
    ├── ai-learning-log.md
    └── design-decisions.md
```

### 🔍 Know Your Files

| File/Directory | Responsibility |
|---|---|
| `main.py` | Application entry point and coordination |
| `README.md` | Project overview, setup, and usage instructions |
| `.gitignore` | Excludes files Git should not track |
| `requirements.txt` | Lists external Python dependencies, if any |
| `services/` | Contains application logic organized into modules |
| `tests/` | Contains automated tests |
| `docs/ai-learning-log.md` | Records technical lessons and learning progress |
| `docs/design-decisions.md` | Documents important architectural decisions |

💡 **Remember:** Adapt the structure to the project. Don't create files or folders merely to fill a template.

## 🎫 Step 2: Create GitHub Issues

Navigate to:

**GitHub Repository → Issues → New Issue**

Break the project into manageable tasks and assign each task to an engineer.

Every issue should define:

- 🎯 **Objective:** What needs to be accomplished?
- 📋 **Acceptance Criteria:** What conditions must be satisfied?
- 👤 **Assignee:** Who is responsible?
- 🔗 **References:** Related issues, requirements, or documentation, if applicable.

### Example: Issue #1

**Title:** Implement Request Validation

**Acceptance Criteria:**
- Validate incoming request data.
- Reject invalid or incomplete inputs.
- Prevent invalid data from entering application state.
- Include unit tests for valid and invalid inputs.

### Example: Issue #2

**Title:** Implement Workflow Logic

**Acceptance Criteria:**
- Implement the required state transitions.
- Reject invalid transitions.
- Enforce workflow rules.
- Include unit tests for permitted and prohibited transitions.

> 🧠 Engineering Mindset
> An issue defines **what the software must accomplish**, not necessarily every detail of how it must be implemented.

---

# 🌿 PART 2 — Branching & Conventional Commits

## 🔄 Step 3: Synchronize and Create a Feature Branch

Avoid implementing features directly on `main`.

Start by updating your local repository:

```bash
git switch main
git pull origin main
```

Create a branch dedicated to your task:

```bash
git switch -c feat/1-request-validation
```

### 🏷️ Branch Naming Examples

```text
feat/1-request-validation
feat/2-access-workflow
fix/5-invalid-status-transition
docs/7-update-project-guide
```

| Prefix | Purpose |
|---|---|
| `feat/` | New functionality |
| `fix/` | Bug fixes |
| `docs/` | Documentation changes |
| `test/` | Test-related work |
| `refactor/` | Code restructuring |

💡 Branch naming conventions vary between teams. The important thing is to remain consistent.

## 💻 Step 4: Implement and Test Your Changes

Work on the files relevant to your assigned task.

Follow this cycle:

1. 📝 Implement the required functionality.
2. 🧪 Write or update the relevant tests.
3. ▶️ Run the tests.
4. 🔍 Inspect the changes for mistakes and unrelated modifications.
5. 📦 Prepare a focused commit.

### Running the Tests

For projects using `unittest`:

```bash
python -m unittest discover -s tests
```

For projects using `pytest`:

```bash
pytest
```

Use the testing framework configured for your project.

## 📦 Step 5: Commit Using Conventional Prefixes

Commits should describe the purpose of a change clearly.

| Prefix | Purpose | Example |
|---|---|---|
| `feat:` | New functionality | `feat: validate access requests` |
| `fix:` | Bug correction | `fix: reject invalid status transitions` |
| `test:` | Test-related changes | `test: cover invalid request inputs` |
| `docs:` | Documentation changes | `docs: update project setup guide` |
| `refactor:` | Internal code improvements | `refactor: simplify request lookup` |
| `chore:` | Maintenance tasks | `chore: update development dependencies` |

### Example Commit

```bash
git add services/requests.py tests/
git commit -m "feat: validate access requests"
```

> [!warning] ⚠️ Watch What You Stage
> Prefer `git add <specific-files>` over blindly staging everything with `git add .`.
>
> Before committing, inspect your changes:
>
> ```bash
> git status
> git diff
> ```

## ☁️ Step 6: Push Your Branch to GitHub

Publish your feature branch:

```bash
git push -u origin feat/1-request-validation
```

The `-u` option establishes the upstream branch, simplifying subsequent pushes.

Your work is now available for collaboration and review.

---

# 🔀 PART 3 — Opening a Pull Request

## 📬 Step 7: Create a Pull Request

Navigate to:

**GitHub Repository → Pull requests → New pull request**

Select the correct branches:

- 🎯 **Base:** `main`
- 🌿 **Compare:** Your feature branch

The base branch receives the changes. The compare branch contains the proposed changes.

## 📝 Step 8: Write a Clear PR Description

### Example Title

```text
feat: implement request validation
```

### Example Description

```markdown
Closes #1

## 📋 Summary
- Added request input validation.
- Rejected invalid request data.
- Added unit tests for validation rules.

## 🧪 Testing
- Ran the automated test suite.
- Verified that invalid inputs are rejected.

## 🔍 Review Notes
- Validation is isolated in the relevant service module.
- No unrelated files were intentionally modified.
```

Replace the examples with details that accurately reflect your implementation.

### 🔗 Why Use `Closes #1`?

GitHub links the pull request to Issue #1 and normally closes that issue automatically when the PR is merged into the repository's default branch.

> ✨ Good PRs Make Reviews Easier
> A reviewer should quickly understand **what changed, why it changed, and how the change was tested**.

---

# 🕵️ PART 4 — Peer Code Review

## 👥 Step 9: Review Your Partner's Pull Request

Collaboration works best when engineers review each other's contributions.

Navigate to:

**Pull Request → Files changed**

Inspect the implementation against the issue's acceptance criteria.

### 🔎 The Review Checklist

- [ ] **Correctness:** Does the implementation satisfy the requirements?
- [ ] **Validation:** Are invalid inputs and edge cases handled?
- [ ] **Data Integrity:** Can a failed operation partially modify a record?
- [ ] **Testing:** Are important success and failure cases covered?
- [ ] **Integration:** Does the module work with the rest of the application?
- [ ] **Maintainability:** Is the code understandable and reasonably organized?
- [ ] **Documentation:** Are the README and relevant documents accurate?

### 💬 Leaving Review Comments

You can comment on specific lines of code to highlight problems or suggest improvements.

GitHub provides three main review options:

| Review Option | Meaning |
|---|---|
| 💬 **Comment** | Provide feedback without formally approving or blocking the PR |
| ✅ **Approve** | Confirm that the changes are acceptable |
| 🔄 **Request changes** | Identify issues that should be addressed before approval |

### 🧠 Review Like an Engineer

Don't focus exclusively on whether the code runs.

Ask yourself:

- What happens when the input is invalid?
- What happens if a file is missing or corrupted?
- Could the operation leave data in an inconsistent state?
- Are the tests checking the actual requirement?
- Does this change break another module?

**The objective is to improve the software, not simply to find fault with the author.**

## 🛠️ Step 10: Address Review Feedback

The author remains responsible for correcting their own branch.

Follow this cycle:

1. 📖 Read the review comments.
2. 🔧 Implement the necessary corrections.
3. 🧪 Run the relevant tests again.
4. 📦 Commit the fixes.
5. ☁️ Push the updated branch.

### Example

```bash
git add services/requests.py tests/
git commit -m "fix: address request validation feedback"
git push origin feat/1-request-validation
```

GitHub automatically updates the existing pull request with the new commits.

You do **not** need to open another PR for the same feature.

> [!important] 🔁 Review Is an Iterative Process
> Review → Fix → Test → Push → Re-review.
>
> Feedback is not fully addressed until the correction has been verified.

---

# ✅ PART 5 — Final Verification & Approval

## 🔍 Step 11: Verify the Corrections

After the author pushes the fixes, the reviewer should:

1. Inspect the updated code.
2. Confirm that the requested corrections were implemented.
3. Check whether the fixes introduced new problems.
4. Run relevant tests or confirm that required CI checks passed.
5. Resolve review conversations whose concerns have been addressed.

⚠️ **Don't resolve a conversation simply because the author replied.** Resolve it when the underlying concern has been addressed.

## 🧾 Step 12: Complete the Final Review Checklist

Before approving the PR, answer the following questions.

### 🎯 Requirements & Correctness
- [ ] Which requirement does this function satisfy?
- [ ] Does the implementation behave correctly?

### 🛡️ Data Integrity
- [ ] Can a failed action partially modify a record?
- [ ] Could loading a corrupted file destroy or overwrite valid data?

### 🧪 Testing
- [ ] Where is the test for this condition?
- [ ] Are both successful operations and relevant failure cases covered?

### 🔗 Integration
- [ ] Does the new module work correctly with the other engineer's module?
- [ ] Are imports, function signatures, and shared data structures compatible?

### 📚 Documentation
- [ ] Is the README still accurate?
- [ ] Are important design decisions and setup changes documented?

Record your answers in the PR review, an appropriate review comment, or the team's designated checklist.

## 🟢 Step 13: Approve the Pull Request

Once the required corrections have been verified:

1. Open **Review changes**.
2. Select **Approve**.
3. Submit the review.

Approval confirms that the reviewer considers the proposed changes acceptable.

Note that repository protection rules may require additional approvals or successful automated checks before merging is permitted.

---

# 🚀 PART 6 — Merge & Synchronize

## 🔀 Step 14: Merge the Approved Pull Request

Once the necessary approvals and checks are complete:

1. Open the approved PR.
2. Select the appropriate merge option.
3. Confirm the merge.
4. Delete the remote feature branch if it is no longer needed.

### Common Merge Strategies

| Strategy | What It Does |
|---|---|
| **Merge commit** | Preserves the branch's commit history and creates a merge commit |
| **Squash and merge** | Combines the PR's changes into a single commit |
| **Rebase and merge** | Replays commits onto the base branch without creating a merge commit |

Follow your team's chosen strategy and repository settings.

## 🔄 Step 15: Update Your Local Repository

After the PR has been merged, synchronize your local `main` branch.

```bash
git switch main
git pull origin main
```

Confirm the latest commit:

```bash
git log -1 --oneline
```

### 🌱 Start Your Next Task

Create the next feature branch from the updated `main`:

```bash
git switch -c feat/3-reporting
```

> [!warning] ⚠️ Avoid Stale Branches
> Starting a new task from outdated code can introduce unnecessary merge conflicts and integration problems.

---

# 🧪 PART 7 — Final Integration Check

## ▶️ Step 16: Run the Full Test Suite

After all required PRs have been merged, test the integrated application.

Using `unittest`:

```bash
python -m unittest discover -s tests
```

Or using `pytest`:

```bash
pytest
```

Run the appropriate command for your project.

## 🖥️ Step 17: Test the Application

Launch the application using its documented entry point.

For example:

```bash
python main.py
```

### Final Verification Checklist

- [ ] Application starts successfully.
- [ ] Modules import and interact correctly.
- [ ] Main workflows behave as expected.
- [ ] Invalid operations are rejected safely.
- [ ] Data is saved and loaded correctly.
- [ ] Important edge cases have been tested.
- [ ] No unexpected regressions have appeared.

**Remember:** Passing unit tests is valuable, but it does not automatically prove that the entire application works correctly.

## 📚 Step 18: Update the Documentation

Before closing out the task, verify that:

- [ ] `README.md` reflects the current setup and functionality.
- [ ] Important architectural decisions are documented.
- [ ] `docs/ai-learning-log.md` captures useful technical lessons.
- [ ] No secrets, unintended files, or generated artifacts have been committed.

Update only the documents relevant to the changes.

---

# 🏁 The Complete Engineering Cycle

Here's the entire workflow at a glance:

| Stage | Action | Outcome |
|---|---|---|
| 🗂️ 1 | Plan | Requirements and issues are defined |
| 🌿 2 | Branch | Work is isolated from `main` |
| 💻 3 | Implement | Functionality and tests are developed |
| 📦 4 | Commit | Changes are recorded clearly |
| ☁️ 5 | Push | Work is published to GitHub |
| 🔀 6 | Open PR | Changes are proposed for integration |
| 🕵️ 7 | Review | Code quality and correctness are evaluated |
| 🔧 8 | Revise | Feedback is addressed and verified |
| ✅ 9 | Approve | Changes satisfy review requirements |
| 🚀 10 | Merge | Approved changes enter `main` |
| 🔄 11 | Synchronize | Local repositories are updated |
| 🧪 12 | Verify | The integrated application is tested |
| 📚 13 | Document | Relevant project documentation is updated |

---

# 🧠 Core Engineering Principles

> [!success] Remember These Five Rules
>
> **1. Plan before coding.**  
> Clear requirements reduce confusion and wasted effort.
>
> **2. Isolate your work.**  
> Feature branches make collaboration safer and changes easier to review.
>
> **3. Test your assumptions.**  
> Verify successful operations, invalid inputs, failure paths, and data integrity.
>
> **4. Review before integrating.**  
> Working code is not necessarily correct, secure, or compatible with the rest of the application.
>
> **5. Verify after merging.**  
> Individual modules may work independently but still fail when combined.

## 🎯 Final Definition of Done

A feature is complete when:

- [ ] Its acceptance criteria are satisfied.
- [ ] Appropriate automated tests pass.
- [ ] The code has been reviewed and approved.
- [ ] Required corrections have been verified.
- [ ] The changes have been merged successfully.
- [ ] The integrated application behaves correctly.
- [ ] Relevant documentation is up to date.

**The goal isn't merely to write code that works. It's to build software that other people can understand, test, review, maintain, and safely extend.** 💪
