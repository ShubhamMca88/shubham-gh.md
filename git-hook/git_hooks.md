# Git Hooks

Git hooks are scripts that Git executes before or after events such as commit, push, and receive. They let you automate tasks and enforce workflows within your Git repository.

## Key Terms

* **Hook:** A script triggered by a specific Git event.
* **Local Hooks:**  Hooks that reside in the `.git/hooks` directory of your local repository and are executed only for that repository.
* **Server-Side Hooks:** Hooks that reside on the server hosting your Git repository and are executed for all users interacting with that repository.
* **Pre-Hooks:** Scripts that run before a Git event. They can modify the event or abort it entirely.
* **Post-Hooks:** Scripts that run after a Git event. They cannot affect the outcome of the event but can be used for notifications or other actions.

## Useful Git Hooks

Here are some of the most commonly used Git hooks and their applications:

### 1. `pre-commit`

* **Purpose:** Runs before a commit is made.
* **Use Cases:**
    * **Code Quality:** Enforce code style guidelines (e.g., using linters) and run tests to prevent commits with errors or bad formatting.
    * **Security Checks:** Scan for sensitive information like passwords or API keys before they are committed.
    * **Commit Message Validation:**  Ensure commit messages adhere to specific patterns or conventions.

### 2. `prepare-commit-msg`

* **Purpose:** Runs before the commit message editor is opened. 
* **Use Cases:**
    * **Pre-populate Commit Messages:**  Automatically generate a commit message template or include relevant information like branch name or issue number.

### 3. `commit-msg`

* **Purpose:** Runs after the commit message is entered but before the commit is created.
* **Use Cases:**
    * **Further Commit Message Validation:** Perform more complex validation of commit messages that couldn't be done with `prepare-commit-msg`.
    * **Notification:** Send notifications about the commit (e.g., to a chat application).

### 4. `post-commit`

* **Purpose:** Runs after a commit is made.
* **Use Cases:**
    * **Notification:**  Notify team members or update project management tools about the commit.
    * **Local Build:** Trigger a local build of the project after a successful commit.

### 5. `pre-push`

* **Purpose:** Runs before changes are pushed to a remote repository.
* **Use Cases:**
    * **Final Checks:** Perform a final set of tests or checks before pushing code.
    * **Prevent Accidental Pushes:**  Block pushes to specific branches (e.g., master) or require additional confirmation.

### 6. `pre-receive` (Server-Side)

* **Purpose:** Runs on the server when receiving pushed commits.
* **Use Cases:**
    * **Enforce Branch Policies:**  Prevent force pushes or direct commits to protected branches.
    * **Access Control:** Restrict who can push to certain branches or repositories.

### 7. `post-receive` (Server-Side)

* **Purpose:** Runs on the server after receiving pushed commits.
* **Use Cases:**
    * **Deployment:** Trigger deployment scripts to update staging or production environments.
    * **Continuous Integration:**  Initiate a continuous integration build process.

## Important Notes:

* **Bypassing Hooks:** Most hooks can be bypassed with the `--no-verify` option.
* **Script Language:** You can write Git hooks in any scripting language (e.g., Bash, Python, Ruby). Ensure the script has execute permissions.
* **Sharing Hooks:** Git hooks are not included in the repository by default. To share hooks with your team, you can store them in the repository and instruct team members to install them or use a tool like Husky to manage hooks.

By utilizing Git hooks effectively, you can significantly improve your development workflow, enhance code quality, and automate various tasks related to your Git repository.