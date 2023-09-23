# GIT

## Materials

1. [The most useful git commands](https://orga.cat/posts/most-useful-git-commands)
2. [Vim](https://docs.oracle.com/cd/E19683-01/806-7612/editorvi-5/index.html)

## Practice

## Important

1. Please note that all commit messages, the amount of commits, branches names *must* be the same as in tasks to successfully pass tests.
2. After the task is completed, push all your branches to GitHub *without* any additional commits (do not change 'master' branch name to 'main').
   And provide a link in Repo class:

```java
public class Repo {
    public static String REPO_LINK = "https://github.com/username/reposotoryName";
}
```

### Task 1

We are going to set up a simple git branching strategy.

1. Create an empty git repository with *<span class="underline">git init</span>* command. Also read up about --bare option
   and [bare repositories](https://www.saintsjd.com/2011/01/what-is-a-bare-git-repository/) themselves.
   ![](media/image1.png)

2. Create a new file with *<span class="underline">touch [README.md](https://www.geeksforgeeks.org/what-is-readme-md-file/) </span>* command.
   ![](media/image2.png)

3. To modify the existing file, we will use VIM text editor. This editor is widely used for rebasing and other git activities so every developer should get used to it. Type vim
   README.md command to open vim text editor. Press letter *<span class="underline">i</span>* to enter the insert mode. Type in “Hello World” or something you like.
   Press *<span class="underline">escape</span>* on the keyboard to exit from insert mode and go to the command mode. In the command mode press *<span class="underline">shift +
   ZZ</span>* to save current file and exit.
   ![](media/image3.png)
   ![](media/image4.png)\
   In the bottom left corner of the above screenshot you can see that currently the editor is in insert mode.

4. To check the progress type *<span class="underline">git status</span>* command. You should see that readme file is untracked now. You should check for a status as often as it is
   possible. If you always read status carefully enough, you will never end up in strange unpredictable situations.\
   ![](media/image5.png)

5. To track readme you can use *<span class="underline">git add .</span>* command. This will track and stage all the files in the current directory. Now you should see that your
   readme file is green which means it is also staged. Take a moment to read about tracking and staging and how they are different with each other.\
   ![](media/image6.png)

6. It is time to commit changes. To create commit use *<span class="underline">git commit -m “created readme”</span>* command which will create commit with corresponding message.
   Your working tree should be clean now.
   ![](media/image7.png)

7. We are going to create new branch called develop, which will contain all the functionality you are currently working on. To create a new branch,
   execute *<span class="underline">git checkout -b develop</span>* command. This will create new branch from the current (master). Create ***git\_task*** branch from ***develop***
   and ***git\_0*** branch from ***git\_task***.
   ![](media/image8.png)\
   You can use *<span class="underline">git show-branch</span>* command to view all branches at once. The branch you are currently working with is marked with ***\**** symbol.\
   ![](media/image9.png)

8. Now we will add some changes to README.md, with ***vim***, check status, stage changes with *<span class="underline">git add README.md</span>* command, commit changes, check the
   result (status) then checkout to ***git\_task*** branch (with *<span class="underline">git checkout git\_task</span>* command) and **merge** changes from ***git\_0*** branch
   with *<span class="underline">git merge git\_0 --no-ff</span>* command. Take some time to read about merging and **no-ff** option. <span class="underline">This is usually the
   default pull request merging behavior so you will work with it on you daily basis</span>.
   ![](media/image10.png)\
   Also note that you can view staged changes with *<span class="underline">git diff --cached</span>* command. For example tere we can see that new line “changes from git\_0” was
   added to the file.\
   ![](media/image11.png)
   ![](media/image12.png)\
   Also note that you can view your latest changes with *<span class="underline">gitk</span>* command (which should invoke gitk tool). If this command does nothing or returns
   error, this usually means that you do not have gitk installed by default (e.g. working from mac). This tool is not necessary and is the matter of choice.\
   ![](media/image13.png)\
   You can also use *<span class="underline">git show-branch</span>* command (or even *<span class="underline">git log</span>* command) to quickly look through your recent work.
   ![](media/image14.png)

9. Now repeat merging process to get your commit to ***master*** (through ***develop*** of course) branch. When you finish, you can use something this *<span class="underline">git
   log --all --graph --decorate --oneline --simplify-by-decoration</span>* or this *<span class="underline">git log --graph --oneline –all</span>* command. These commands were
   found on the stackoverflow as an answer to a question of viewing git history as a tree. This is not the best solution but it is more than enough for our needs. You output should
   look similar to this:
   ![](media/image15.png)\
   From this picture you can see that the HEAD is currently looking at the master’s latest commit. We have created 5 commits: 2 with actual edits and 3 merge commits.
10. Synchronize all created branches with a remote repository. 

**The idea here is simple.** You should always develop you features in custom branches made from ***develop*** branch. When you feature is ready it goes to the ***develop***
branch (usually with pull request instead of merge). When the release time has come, all the merging to the ***develop*** branch should stop (or you may create custom ***
pre\_release*** branches with locked functionality). ***develop*** branch (or ***pre\_release***) should be tested and stabilized. As soon as the branch is stable, it goes to
the ***master*** branch (or you may have different ***release*** branches and even don’t have a ***master***, or don’t use ***master*** branch at all). This procedure might differ
from project to project and always <span class="underline">should be designed with the respect to the concrete project and goals</span>. All this helps to keep the repository clean
and always have some stable versions for the production.

### Task 2

#### Part 1

We are going to practice some skills obtained in the previous task. If you come across something you still don’t know, please use links provided in the descriptions, internet
search, other students as sources of knowledge and help.
For this task you will create two separate branches ***git\_1*** and ***git\_2*** in your remote repository and local <span class="underline">tracked</span> branches with same
names. Both these branches should be made of the ***git\_task*** branch.

1. ***git\_1***: Add and commit *firstFile.txt* file with 10 lines with message 'Added firstFile.txt to git_1'.
2. ***git\_1***: Add and commit *secondFile.txt* file with 10 lines with message 'Added secondFile.txt to git_1'.
3. Merge branch ***git\_1*** to ***git\_2*** with default message 'Merge branch 'git_1' into git_2'
4. ***git\_2*:** Update and commit any **two** lines in *secondFile.txt* with message 'Changed 2 lines in secondFile.txt in git_2'
5. ***git\_1*:** Update and commit **the same** 2 lines with the different info in *secondFile.txt* with message 'Changed 2 lines in secondFile.txt in git_1'.
6. Merge branch ***git\_2*** to ***git\_1*,** resolve conflict. Left **all** (4) modified lines. Commit with message 'Fixed merge conflict'
7. ***git\_1***: Update and commit 1.txt file, modify two lines. Message - 'Changed 2 lines in firstFile.txt in git_1'
8. ***git\_1***: Update and commit 1.txt file, modify **another** two lines: 'Changed another 2 lines in firstFile.txt in git_1'
9. Transfer changes of commit from <span class="underline">Step 7 only</span> to ***git\_2*,** using **format patch**. Commit: 'Apply patch'
10. Transfer changes of commit from <span class="underline">Step 8 only</span> to ***git\_2*,** using **cherrypick** command.
11. ***git\_2*:** Concatenate the last two commits ('Apply patch' and 'Changed another 2 lines in firstFile.txt in git_1') using ***reset** + **commit*** commands. 
12. ***git\_2*:** Change author and message of the last commit and add non-empty *thirdFile.txt* file to it. Message - 'Concatenated two commits', author - Ivan Ivanovich <Ivan_Ivanovich>
13. ***git\_2***: Create a **new** commit that *reverts* changes of the last one. Leave the default message - 'Revert "Concatenated two commits"'
14. ***git\_2*:** Create and commit *thirdFile.txt* file. Message - 'Added thirdFile.txt to git_2'
15. ***git\_2***: Run command that removes all changes of the last two commits. You will end up with commit - 'Concatenated two commits' 
16. Synchronize ***git\_1*** and ***git\_2*** with a remote repository.

#### Part 2

For this task you should learn how to use **interactive rebase**, thus other ways of achieving the same are prohibited.

1. Create ***git\_3*** branch from ***git\_task***. Checkout to ***git\_3***.
2. Add new empty file *doubtingFile.txt* and commit it with message - 'Added doubtingFile.txt to git_3'.
3. Add a line to a file and commit changes. Do it 5 times. You should end up with 5 lines in a file and 6 commits: 1 for creating an empty file and 5 for adding a line. Messages are the following: 'Added line 1', 'Added line 2' ...
4. Check your log and copy it somewhere.
5. Launch interactive rebase for 5 last commits, squash all the latest commits into the first one. Reword first commit. You should end up with 2 commits: 1 for creating an empty
   file (Added doubtingFile.txt to git_3) and second for adding 5 lines. Second commit should have a new commit message - 'Rebased commits'
6. Check your log and compare it with the previous one. Look at the hash, date, commit message. Explain what changed and why.
7. Check your reflog. Explain what you can see and why.
8. Synchronize ***git\_3*** with a remote repository.

## Extra Materials

1. [Useful git commands](https://davidwalsh.name/git-commands)
2. [Vim commands cheat sheet](https://www.fprintf.net/vimCheatSheet.html)
3. [Basic Vim commands - For getting started](https://coderwall.com/p/adv71w/basic-vim-commands-for-getting-started)
4. [vim adventures](https://vim-adventures.com/)
5. [Introduction to Git - Branching and Merging](https://www.youtube.com/watch?v=FyAAIHHClqI)