<h1>GIT FUNDAMENTALS </h1>

<h2>List of tasks</h2>
<ol>
<li>Initialize, Commit, and Branch Basics</li>
<li>Using .gitignore and Tracking Files</li>
<li>Undoing Changes and Reverting Commits</li>
<li>Simulating and Resolving Merge Conflicts</li>
<li>Interactive Rebasing for Clean Commit History</li>
<li>Stashing Changes for Context Switching</li>
<li>Cherry-Picking Commits Between Branches</li>
<li>Using Git Hooks for Automated Checks</li>
<li>Working with Remote Repositories and Collaboration</li>
<li>Comprehensive Workflow with Forced Pushes and Recovery Objective</li>
</ol>

<h3>Task One Summary :</h3>

<h5>Initialize, Commit, and Branch Basics</h5>

| Command  | Function |
| -------- | -------  |
| git init  | Create an empty Git repository or reinitialize an existing one     |
| git branch | List, create, or delete branches      |
| git checkout    | Switch branches or restore working tree files    |
| git add | Add file contents to the index |
| git commit | Record changes to the repository |
| git status | Show the working tree status |
| git merge |  Join two or more development histories together |

<h3>Task Two Summary :</h3>

<h5>Using .gitignore and Tracking Files</h5>

<p>
  The <strong>.gitignore</strong> file is set up to exclude certain files and directories from being tracked by Git.  
  Common examples include:
</p>

<ul>
  <li>Configuration files such as <code>.env</code></li>
  <li>Executable files such as <code>.class</code>, <code>.exe</code></li>
  <li>Build directories like <code>dist/</code> and <code>build/</code></li>
  <li>Log files, temporary files, and other generated files</li>
</ul>

<p>Files listed in the <code>.gitignore</code> file are ignored by Git and will not be tracked in the repository.</p><p>The <strong>git status</strong> command allows you to check which files are being tracked by Git.</p>

<h3>Task Three Summary :</h3>

<h5>Undoing Changes and Reverting Commits</h5>

<p>To undo changes in a tracked file (e.g., index.html) before committing, use either git checkout -- <file> or git restore  <br><strong>Note:</strong>This works only <strong>before committing</strong></p>

<p>To undo a commit , use <strong>git revert</strong> or  <strong>git reset</strong></p>
<ul>
<li><strong>git revert</strong> is used to record some new commits to reverse the effect of some earlier commits</li>
<li><strong>git reset</strong> moves the branch pointer to a previous commit, removing subsequent commits. git reset doesn't always erase commits—it depends on the mode:
<ul>
<li>--soft: Keeps changes staged</li>
<li>--mixed (default): Keeps changes unstaged </li>
<li>--hard: Deletes changes permanently</li>
</ul>
</li>

</ul>


|**Feature** |	**git reset** |	**git revert** |
|--------|------------|------------|
|**Effect on history** |Rewrites history (dangerous in shared branches) |	Creates a new commit (safe) |
|**Undo commit**|	Deletes commits from history |	Reverses changes in a new commit |
|**Safe in shared branches?**|	❌ No |	✅ Yes |
|**Preserves previous commits?**|	❌ No |	✅ Yes |
|**Best for** |	Undoing local changes before pushing  |	Reverting changes after pushing |


<h3>Task Four Summary :</h3>

<h5>Simulating and Resolving Merge Conflicts</h5>

<p>Conflicts arise when the same lines of code in a common file in both branches are modified and then merged.</p>
<ul>
<li><strong>git status</strong> can be used to check which files have merge conflicts</li>
<li><strong>git diff</strong> can be used to view conflicting changes</li>
</ul>

<h3>Task Five Summary :</h3>

<h5>Interactive Rebasing for Clean Commit History</h5>

<p><strong>Interactive rebasing (git rebase -i)</strong> is used to squash, reorder, or edit commit messages.</p>
</p> <strong>Squashing commits</strong> is the process of combining multiple related commits into a single commit before merging them into the main branch. This improves the clarity and maintainability of the repository history.
</p>
<p>Key benefits : </p>
<ul>
<li>Keeps history clear and linear</li>
<li>Avoid unnecessary commits</li>
</ul>

<h3>Task Six Summary :</h3>

<h5>Stashing Changes for Context Switching</h5>

<p><strong>git stash</strong> allows you to temporarily save changes without committing.</p>

<p>When you're working on a feature and suddenly need to switch branches without committing unfinished work, git stash allows you to temporarily save your changes without including them in a commit. </p>

| Command  | Function |
| -------- | -------  |
| git stash list  | Show all stashed changes     |
| git stash pop | Apply the most recent stash and remove it      |
| git stash apply stash@{n}    | Apply a specific stash but keep it    |
| git stash drop stash@{n} | Delete a specific stash |
| git stash clear | Delete all stashed changes |

<h3>Task Seven Summary :</h3>

<h5>Cherry-Picking Commits Between Branches</h5>

<p><strong>Cherry-picking</strong> lets you apply a specific commit from one branch to another.It is used when a specific fix from a feature branch needs to be applied to main without merging the entire branch.</p>
<strong>Find the commit hash from another branch</strong><br>
<code>git log --oneline feature-branch</code><br>
<strong>Cherry-pick the commit</strong><br>
<code>git checkout main</code><br>
<code>git cherry-pick &lt;commit-hash&gt; </code><br>
<strong>Resolve any conflicts and commit if needed.</strong><br>

<h3>Task Eight Summary :</h3>

<h5>Using Git Hooks for Automated Checks</h5>

<ul>
  <li><strong>Git hooks</strong> allow running scripts before commits, merges, etc.</li>
  <li>Git hooks are scripts that run automatically every time a particular event occurs in a Git repository</li>
  <li>Hooks reside in the .git/hooks directory of every Git repository.</li>
</ul>

<p>Steps involved :</p>
 <ul>
  <li>Navigate to the .git/hooks directory: <code>cd .git/hooks</code></li>
  <li>Create a pre-commit hook script: <code>nano pre-commit</code></li>
  <li>Add a simple linter check or any other custom function</li>
  <li>Make it executable: <code>chmod +x pre-commit</code></li>
 </ul>

<h3>Task Nine Summary :</h3>

<h5>Working with Remote Repositories and Collaboration</h5>

<p>Steps to Work with a <strong>Remote Repository</strong>:</p>
 <ul>
  <li>Create a repository on GitHub/GitLab.</li>
  <li>Push a local repository to remote:<br><code>git remote add origin &lt;repo-url&gt;</code><br><code>git push -u origin main</code></li>
  <li>Create a branch, make changes, and push</li>
  <li>Open a Pull Request (PR) and merge via GitHub</li>
  <li>Pull the merged changes back locally:<br><code>git checkout main</code><br><code>git pull origin main</code> </li>
 </ul>

<h3>Task Ten Summary :</h3>

<h5>Comprehensive Workflow with Forced Pushes and Recovery Objective</h5>

<p>Steps to Handle <strong>Forced Pushes & Recover Lost Commits</strong>:</p>
 <ul>
  
  <li>Modify commit history and force push: <br><code>git rebase -i HEAD~3</code><br><code>git push origin main --force</code></li>
  <li>Recover lost commits using <code>git reflog</code>:<br><code>git reflog</code><br><code>git checkout &lt;commit-hash&gt;</code></li>
  <li>Best Practices : <br><ul>
  <li>Use <code>--force-with-lease</code> instead of <code>--force</code>.</li>
  <li>Avoid forced pushes on shared branches.</li>
  <li>Always communicate before rewriting history.</li>
  </ul>
  </li>

 </ul>

 <p><strong>git reflog</strong> used to view all recent changes.</p>
 <p><strong>git push --force-with-lease</strong> is a safer alternative to <strong>git push --force</strong>. It prevents accidentally overwriting remote changes that you didn't fetch before forcing a push.</p>
 <ul>
 <li>Checks if the remote branch is in the same state as your local repository’s last known state.
</li>
 <li>If no new commits were pushed by someone else, the force push happens.</li>
 <li>If new commits exist on the remote (made by others), it prevents overwriting those changes.</li>
 </ul>