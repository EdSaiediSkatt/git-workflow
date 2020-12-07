# **Table of Contents** 

- [SECTION A. BASIC COLLABORATION](#section-a)

	- [CHECKLIST A](#checklist-a)

	- [CHECKLIST A WITH EXPLANATIONS](#checklist-a-detailed)

- [SECTION B. SYNCHRONOUS AND FULL COLLABORATION](#section-b)

	- [CHECKLIST B](#checklist-b)

	- [WHAT IS REBASING?](#what-is-rebasing)

	- [CREATING PULL REQUESTS](#creating-pull-requests)

- [IMPORTANT OPTIONS](#important-options)

<a name="section-a"></a>
## SECTION A. BASIC COLLABORATION
 
### FOR WHEN YOU ARE SURE OTHERS ARE NOT WORKING ON THE REPOSITORY AT THE SAME TIME

**This is for collaborating when you are sure that others are not working simultaneously on the script! That is why it is called "Basic collaboration", in that it is "not Synchronous Collaboration".**

***"Don't Mess with the Master" Checklist:***

This checklist (and this document) originated from summarizing this article:

<https://thenewstack.io/dont-mess-with-the-master-working-with-branches-in-git-and-github/>

***(pulling, branching, working, merging and pushing commands)***



<a name="checklist-a"></a>
#### CHECKLIST A
| STEPS     | ☐    |  COMMAND AND EXPLANATIONS | POTENTIAL ERRORS |   
| --------|---------|-------|--------|
| 1       | ☐      | Be in the Git project directory you want to work on (it\'ll be created automatically if you \"`git clone`\")          |         |
| 2       | ☐      |  `git pull origin master`    																						 |         |
| 3       | ☐      |  `git checkout --b feature_branch`     																						 |         |
| 4       | ☐      |  *DEVELOP A NEW FEATURE, i.e. DO ALL THE CHANGES YOU WANT TO ADD A FEATURE WHICH HAS ONE OR MANY ADDED FUNCTIONALITIES. ASSIGN EACH ADDED FUNCTIONALITY AS ONE COMMIT ITERATIVELY (i.e. add an Atomic Commit). WHEN FINISHED, SAVE THE FILES & PROCEED AS BELOW* (Ensure you are in the same folder in the terminal):    																						 |         |
|         | ☐      |  *Hint:* In stages 5 or 6, you can type "git status" to see suggestions on what to do.    																						 |         |
| 5 (iterative) | ☐      |  `git add \--all`    																						 |         |
| 6 (iterative) | ☐      |  `git commit -m "git commit message"`    																						 |         |
| 7       | ☐      |  `git checkout master`    																						 |  .a      |
| 8       | ☐      |  `git fetch`    																						 |         |
| 9       | ☐      |  `git diff origin/master` (to ensure no changes have been done to master while you were working)     																						 |         |
| 10       | ☐      |  `git merge feature_branch \--no-ff` and (optionally) write a merge commit message and ensure to exit (in Git Bash you exit by pressing esc, and entering `:wq`)     																						 |         |
| 11       | ☐      |  `git push`     																						 |         |
| 12       | ☐      |  `git branch -d feature_branch`     																						 | .a      |

<a name="checklist-a-detailed"></a>
#### CHECKLIST A WITH EXPLANATIONS

| STEPS     | ☐    |  COMMAND  | EXPLANATIONS |   
| --------|---------|-------|--------|
| 1       | ☐      | Be in the Git project directory you want to work on          |         |
| 2       | ☐      |  `git pull origin master`    		 |  \"Download\" the latest version on the remote (called origin)'s master branch, and replace contents in my local Git folder       |
| 3       | ☐      |  `git checkout --b feature_branch`  |  Go to a branch called feature_branch (if there is no such branch, this will create a new branch called feature_branch) and start tracking changes in that branch.       |
| 4       | ☐      | DEVELOP A NEW FEATURE (See checklist above for more details  |         |
| 5       | ☐      |  `git add \--all`   | You effectively add all the changes made into the staging area, ready to be committed (all this is happening on your local branch).        |
| 6       | ☐      |  `git commit -m "git commit message"`   | You commit the changes from the staging area into your local repository on your local branch.         |
| 7       | ☐      |  `git checkout master`   | You switch back to the local master branch (it's only from here that you can merge your branch to the master) |
| 8       | ☐      |  `git fetch`   | This fetches the latest remote (or origin) master repository into your local master branch. |
| 9       | ☐      |  `git diff origin/master` (to ensure no changes have been done to master while you were working)   | A command to check if anything has changed in the master since you were working on your branch. If the terminal shows nothing, you know that the origin/master branch has not changed from your local master branch. If you see differences, then you will know that the master has changed; In this case, you will want to checkout your feature_branch branch, and rebase your changes onto the new origin/master branch and only after ensuring everything works, merge your changes as per steps below. For rebasing, see steps 4-6 in checklist B in the Collaboration section of this document! |
| 10       | ☐      |  `git merge feature_branch \--no-ff`  | You now merge your feature_branch branch into your local master branch. To exit the message window that pops up where you can change the message, but the default message is fine, so you type ":wq" to exit.  |
|          |       |    | *Note: \--no-ff preserves feature history and easy full-feature reverts* |
| 11       | ☐      |  `git push`  | You \"upload\" code from the local master to the remote master repository (on Bitbucket); you can now go to Bitbucket and check to see if the changes are made (It is a good idea). |
| 12       | ☐      |  `git branch -d feature_branch`    | Delete the feature_branch branch by running this code. |

<a name="section-b"></a>
## SECTION B. SYNCHRONOUS AND FULL COLLABORATION 
### FOR WHEN OTHERS MAY BE WORKING ON THE SCRIPT AT THE SAME TIME, AND WHEN YOU MAY WANT FEEDBACK ON A FEATURE:

This follows Atlassian's Simple Git workflow article: <https://www.atlassian.com/git/articles/simple-git-workflow-is-simple>

<a name="checklist-b"></a>
### CHECKLIST B.

| Steps                                  | ☐ | Command and Explanations                                                                                                                                                                                                    |
| ---------------------------------------|---|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1                                      | ☐ | Be in the Git project directory you want to work on (it\'ll be created automatically if you \"git clone\")                                                                                                                                                                                                    |
| 2                                      | ☐ | `git pull origin master`                                                                                                                                                                                                                                                                                        |
| *3*                                    | ☐ | `git checkout --b feature_branch`                                                                                                                                                                                                                                                                               |
| 4                                      | ☐ | DEVELOP A NEW FEATURE: DO ALL THE CHANGES YOU WANT. ASSIGN EACH ADDED FUNCTIONALITY AS ONE COMMIT. SINCE *YOU KNOW OTHERS MAY BE WORKING ON THE MASTER, REGULARLY REBASE (rebasing is equivalent to step 7 below)!*                                                                                           |
| 5                                      | ☐ | `git add \--all`                                                                                                                                                                                                                                                                                                |
| 6                                      | ☐ | `git commit -m "git commit message"`                                                                                                                                                                                                                                                                            |
| 7                                      | ☐ | `git fetch origin` <br>       																																																																					|
| (iterative -- pre-conflict-resolution) |   | `git rebase origin/master` AND RESOLVE ANY CONFLICTS COMING OUT OF THE REBASE!                                                                                                                                                                                                                                                               |
|                                        |   | YOU HAVE STARTED THE REBASING PROCESS. IF THERE ARE NO CONFLICTS, THE REBASING PROCESS IS FINISHED, GO TO STEP 8. OTHERWISE, RESOLVE ANY CONFLICTS COMING OUT OF THE REBASE ATTEMPT BY EDITING THE CONFLICTING FILES (Read the line saying CONFLICT (content): Merge conflict in \<conflicted_files\>): THEN, |
|                                        |   | `git add \<conflicted_files\>`                                                                                                                                                                                                                                                                                  |
|                                        |   | `git rebase \--continue`                                                                                                                                                                                                                                                                                        |
| 7b                                     | ☐ | IF you want other people to help you develop the same feature branch, push it to remote by typing:                                                                                                                                                                                                            |
| (conditional)                          |   | `git push origin feature_branch`                                                                                                                                                                                                                                                                                |
| 7c                                     | ☐ | IF you already had pushed the feature branch remotely, and you ARE working with other people on the same shared remote feature branch, then in addition to step 7, rebase changes coming from the remote feature branch by typing:                                                                            |
| (conditional)                          |   | `git rebase origin/feature_branch`                                                                                                                                                                                                                                                                              |
|                                        |   | and then SOLVE ANY CONFLICTS.                                                                                                                                                                                                                                                                                 |
| 7d                                     | ☐ | IF you want others to test your new feature, BEFORE it becomes merged with the remote master, then push this feature_branch to Bitbucket, by typing:                                                                                                                                                          |
| (optional and conditional)             |   | `git push --u origin feature_branch`                                                                                                                                                                                                                                                                            |
|                                        |   | AND THEN CREATE A PULL-REQUEST. If you got feedback from your pull-request you can incorporate it and go back to the iterative step 7, and then 8.                                                                                                                                                            |
| 8                                      | ☐ | MAKE SURE YOUR FEATURE IS DEPLOYABLE (i.e. IT WORKS) AND NO ONE HAS CHANGED THE REMOTE MASTER SINCE YOU REBASED (i.e. during the time you were resolving conflicts), BEFORE YOU MERGE AND PUSH IT TO THE REMOTE MASTER AS BELOW.                                                                              |
|                                        |   | *Hint:* *You can refresh the repository commits page on Bitbucket to ensure no one has done this during the time you were rebasing.*                                                                                                                                                                          |
| 9                                      | ☐ | `git checkout master`                                                                                                                                                                                                                                                                                           |
| 11                                     | ☐ | `git merge feature_branch \--no-ff`                                                                                                                                                                                                                                                                             |
| 12                                     | ☐ | `git push`                                                                                                                                                                                                                                                                                                      |
| 13                                     | ☐ | `git branch -d feature_branch`                                                                                                                                                                                                                                                                                  |

<a name="what-is-rebasing"></a>
### WHAT IS REBASING?

Rebasing is to change the base of the branch you are working on! It is used when the reference branch you are building on, e.g. master, has one or more commits after you had started branching off and developing your feature. The graphic below explains it best:

![](media\image5.png){width="6.435685695538058in" height="3.123847331583552in"}

In the graphic above, each circle is a commit (read left to right). You can see that since the Feature branched off first, two more commits were implemented on the master branch. Well, we cannot merge and push our feature out directly now. So what we do, is we fetch it, then we rebase it (i.e. ask git to move our changes on top of the two new master commits). Git does this, but often conflicts can happen, which you would have to resolve. Fortunately, git tells you in which file the conflicts happen. Then you can go into the file (e.g. Python file, etc) and fix them, and then continue the rebase, until it is successful. The asterisks \* inside the circles above, show how the two commits of the feature branch moved on top of the latest master changes. Now your feature branch head is at the blue-asterisked circle. If you git checkout master and git merge it, then the Master head will move there too.

<a name="creating-pull-requests"></a>
### CREATING PULL REQUESTS: 

(The purpose of a pull request is to have the code maintainer(s) see your new feature and decide if they would like to merge it themselves, or give you the go-ahead to merge it if you have permissions)

1.  In the Bitbucket repository where you would like to make the pull-request, click on "Create Pull Request" (which is the icon that can be seen in the photo below).

![](media\image6.png){width="6.299212598425197in" height="3.015768810148731in"}

2.  Clicking that will bring you to the snapshot shown above. Then simply select your branch (as in photo below; feature_branch), click on Continue:

![](media\image7.png){width="6.299212598425197in" height="3.6002635608048994in"}

3.  Now type a meaningful description and choose your desired reviewers (you must have had permissions) and click Create.

![](media\image8.png){width="6.299212598425197in" height="3.465177165354331in"}

4.  Now your chosen reviewer will receive an e-mail from <bitbucket-aurora@skatteetaten.no> stating that you have created a pull request. The code maintainer/reviewer can then comment on your code, write feedback, highlight problematic lines, or choose to approve or merge your code. Be aware that if your code maintainer approves your code, it does not mean that (s)he has merged it (even though they have the choice of merging it).

5.  Once the code maintainer has approved of your code, you will receive an e-mail, where you click "View Pull Request". Now you can merge your feature, either by clicking merge (top-right of snapshot below; **make sure** to rebase if time has passed and others may have developed the master further, and ensure the rebased code is deployable) or by repeating steps 7-13 of the Section B Checklist.

![](media\image9.png){width="6.299212598425197in" height="3.5378455818022747in"}

6.  You will be prompted with a dialogue box asking you whether to merge in the feature_branch to the master. Let the "Delete source branch" option be checked (it ensures too many branches are left lying around and confusing developers, and is not that risky as the atomically-added commits in the feature_branch will always be preserved)

![](media\image10.png){width="6.299212598425197in" height="3.2251760717410325in"}

7.  Ensure you git pull origin master afterwards on your Git Bash. Congratulations. Now you are done.

Beware that if you do not do a pull request, when your feature needed a second test or set of eyes, your operations (Ops) team or code maintainers or collaborators may be have to deal with it:

![H:\\Mine Dokumenter\\Programs\\Git\\Test.jpg](media\image11.jpeg){width="4.724540682414698in" height="3.5454549431321083in"}

<a name="important-options"></a>
## IMPORTANT OPTIONS

If you wanted to push your local branch directly to the remote, as a remote branch, you run this (after git add \--all and git commit -m "\<YOUR COMMIT MESSAGE\>" and then git checkout master:

git push origin feature_branch

(Hint: essentially all git push and pulls have this structure, whether the remote is called origin, developer, etc.: "git push \<remote\> \<branch\>")

\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*


