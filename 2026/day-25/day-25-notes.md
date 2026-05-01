Task:1
What is the difference between --soft, --mixed, and --hard?

--soft : move HEAD,keep changes staged.
--mixed: move HEAD,unstage changes.
--hard : move HEAD,discard all changes.

Which one is destructive and why?

--hard is destructive because it permanently discards all uncommitted changes in your staging area and working directory.

When would you use each one?

--soft : when you want to undo a commit but keep changes staged,for example to edit the commit message.
--mixed: when you want to undo a commit and unstage changes,so you can modify them before recommitting.
--reset: when you want to completely remove commits and all changes.

Should you ever use git reset on commits that are already pushed?

--No,once commits are pushed,others may have already pulled and worked on them,so resetting them can cause confusion and conflicts.

Task 2: Git Revert 
How is git revert different from git reset?

--git revert: Creates a new commit that undoes changes from a previous commit.Keeps original commit in history
--git reset : Can rewrite history.Moves the branch pointer to an earlier commit

Why is revert considered safer than reset for shared branches?

--git revert does not rewrite history.

When would you use revert vs reset?

--git revert: On branches that are already pushed/shared.To undo a commit without breaking history.
--git reset : When you want to rewrite history or completely remove commits.

Task 3: Reset vs Revert — Summary
                                                     git reset	                                                                                                                                    git revert
What it does	Can rewrite history.Moves the branch pointer to an earlier commit	Creates a new commit that undoes changes from a previous commit.Keeps original commit in history
Removes commit from history?	 Yes	                                                                                                                                                 No
Safe for shared/pushed branches?	  No                                                                                                                                              	Yes
When to use	When you want to rewrite history or completely remove commits	On branches that are already pushed/shared.To undo a commit without breaking history

Task 4: Branching Strategies
GitFlow

How it works:

main : Contains production-ready code.Every commit here is a stable release.

develop : The integration branch where new features are merged before they’re ready to go live.

feature : For building out new functionality.Created from develop and merged back when complete.

release : Used to prep a new version for production.Created from develop and merged into both main and develop.

hotfix : For urgent fixes on production.Created from main,then merged back into both main and develop.

Text Diagram:

[main] (Production-ready)
|
o <----------------------------------------- (Start)
| \
|  \ [develop] (Integration)
|   |
|   o <------------------------------------- (Develop Start)
|   | \
|   |  \ [feature/login] (New functionality)
|   |   |
|   |   o (Feature Commit)
|   |   |
|   |   o (Feature Complete)
|   |  /
|   o / (Merge feature to develop)
|   |
|   | \
|   |  \ [release/1.0] (Prep for production)
|   |   |
|   |   o (Release Prep/Bug Fix)
|   |   |
|   |   o (Release Ready)
|   |  / \
|   o /   o (Merge release to develop)
|  /
o / (Merge release to main & tag v1.0)
|
| \
|  \ [hotfix/1.0.1] (Urgent fix)
|   |
|   o (Apply Fix)
|  / \
o /   o (Merge hotfix to develop)
|
V
When/where it's used:

Team follows scheduled release cycles

Need to maintain multiple versions

Pros:

Clear separation of concerns across features,releases,and hotfixes.
Cons:

Can result in long-lived branches,increasing the risk of merge conflicts.
GitHub Flow

How it works:

Create a feature branch from main
Push commits to the feature branch
Open a pull request for code review and automated tests.
Once approved, merge back to main.
Deploy immediately.
Everything in main should always be production-ready.
Text Diagram:


  [main] (Always Production-Ready)
    |
    o (Start)
    |
    |\_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ 
    |                               \
    |                                \ [feature/login]
    |                                 |
    |                                 o (Commit 1)
    |                                 |
    |                                 o (Commit 2)
    |                                 |
    |                                 o (Pull Request & Review)
    |<_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _/
    |                               
    o (Merge & Auto-Deploy)
    |
    v
When/where it's used:

ship frequent,small releases
Pros:

Fast merge & deploy
Cons:

In large teams,it can result in frequent merge conflicts
Trunk-Based Development

How it works:

There’s one main branch, often called main or trunk. All development happens here
Developers commit directly to main, often multiple times per day
Changes are small,incremental
Text Diagram:

 [main] (The Trunk)
   |
   o (Start)
   |
   |\_ _ _ _ _ _ _ 
   |             \
   |              o (Dev A: Small Change)
   |<_ _ _ _ _ _ /
   |             /
   o (Merge & Test)
   |
   |\_ _ _ _ _ _ _ 
   |             \
   |              o (Dev B: Small Change)
   |<_ _ _ _ _ _ /
   |             /
   o (Merge & Test)
   |
   v
When/where it's used:

building SaaS products or anything that updates frequently
Pros:

Delivers the fastest feedback from dev to prod
Cons:

Can be risky without tests
Answer:

Which strategy would you use for a startup shipping fast?

Trunk-Based Development
Which strategy would you use for a large team with scheduled releases?

GitFlow
