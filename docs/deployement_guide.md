7. How to Deploy Your Code: A Quick Guide (for Developers) 🚀
If you're a developer, you'll be deploying your code changes. Here's a simplified version of the steps. Your team will provide more detailed, hands-on training.

Get the Code: First, you'll "clone" our code repository (Azure Repos) to your computer using git clone.

Common Git Command: git clone <repository-url>

Work on 'dev': You'll usually start by making sure your local 'dev' branch is up-to-date: git checkout dev then git pull origin dev.

Common Git Commands:

git checkout <branch-name>: Switch to a branch.

git pull origin <branch-name>: Get latest changes from remote.

Make Your Changes: Open the relevant code file (e.g., an Apache Airflow DAG { data-tooltip="Directed Acyclic Graph: In our Airflow system, this is like a flowchart that defines a series of tasks and the order they need to run in for a specific data process." } file) and make your updates.

Create a New Branch: Always work in a new "feature branch" for your changes: git checkout -b 'your-descriptive-branch-name'.

Common Git Command: git checkout -b <new-branch-name>

Save & Commit: Save your changes, then "add" them to be tracked (git add .) and "commit" them with a clear message (git commit -m 'Your brief description').

Common Git Commands:

git add .: Stage all changes.

git commit -m 'Your message': Commit staged changes.

git status: Check current status of your working directory.

git diff: See changes before staging/committing.

Push Your Branch: Send your new branch to our central code repository: git push -u origin your-descriptive-branch-name.

Common Git Command: git push -u origin <your-branch-name>

Create a Pull Request (PR) to 'dev': Go to Azure DevOps (your team will provide the specific URL). You'll create a PR from your new branch to the 'dev' branch. This is where automated checks run and your teammates review your code.

Merge to 'dev': Once your PR is approved and all checks pass, it gets merged into the 'dev' branch. This automatically deploys your changes to our development environment for testing.

Create a PR to 'main' (for Production): After successful testing in the development environment, you'll create another PR, this time from the 'dev' branch to the 'main' branch. This also requires review and approval.

Merge to 'main': Once approved, merging to 'main' automatically deploys your changes to our production environment (our live system).

Verify: Always check the Airflow UI after deployment to make sure your changes are live and working as expected!

Potential Improvements for this Section:
Link to Detailed Guides: For each step, provide a link to a more detailed internal guide or a short video tutorial (if available).

Common Git Commands: Add a small box with commonly used Git commands for developers (e.g., git status, git diff, git log).

Troubleshooting Deployment Issues: Briefly mention common reasons for deployment failures and where to look for logs (e.g., "If your pipeline fails, check the Azure DevOps pipeline logs").