**Part 1: Refining Git History (10 Challenges)**

1. **Missing File Fix:**

   - Run `git status` and `git log` to assess the current state of your repository.
   - From the status you will see that you forgot to add `test4.md` in the last commit.

   **Challenge:** Recover from this error by staging/adding `test4.md` and amending the commit message with an appropriate description.

2. **Editing Commit History:**

   - It's crucial to maintain accurate commit messages. Modify the message from "Create another file" to "Create second file".

   **Challenge:** Utilize interactive rebasing (`git rebase -i HEAD~2`) to edit the commit message and ensure clarity. learn more about git `rebase`
   ```
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (master)
    $ touch test{1..4}.md
    git add test1.md && git commit -m "chore: Create initial file"
    git add test2.md && git commit -m "chore: Create another file"
    git add test3.md && git commit -m "chore: Create third and fourth files"
    [master (root-commit) d2e8d96] chore: Create initial file
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 test1.md
    [master 139469f] chore: Create another file
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 test2.md
    [master b372527] chore: Create third and fourth files
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 test3.md
    
    PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (master)
    $ git status
    On branch master
    Untracked files:
      (use "git add <file>..." to include in what will be committed)
            test4.md
    
    nothing added to commit but untracked files present (use "git add" to track)
    
    PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (master)
    $ git add test4.md
    
    PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (master)
    $ git log
    commit b372527409c9fe3726877d9aa9d5e47a2e20f6b1 (HEAD -> master)
    Author: htonnyg@gmail.com <htonnyg@gmail.com>
    Date:   Wed Jun 10 10:30:58 2026 +0200
    
        chore: Create third and fourth files
    
    commit 139469f461e51e2967fb34f3cb9ad9e4eb13e919
    Author: htonnyg@gmail.com <htonnyg@gmail.com>
    Date:   Wed Jun 10 10:30:57 2026 +0200
    
        chore: Create another file
    
    commit d2e8d966b8edd4c4612f4c74d17bfa958cb85d10
    Author: htonnyg@gmail.com <htonnyg@gmail.com>
    Date:   Wed Jun 10 10:30:57 2026 +0200
    
        chore: Create initial file
    
    PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (master)
    $ git status
    On branch master
    Changes to be committed:
      (use "git restore --staged <file>..." to unstage)
            new file:   test4.md
    
    
    PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (master)
    $ git commit -m "Added fourth file and comitted it"
    [master f4a4d2a] Added fourth file and comitted it
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 test4.md
    
    PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (master)
   git rebase -i HEAD~2
   [detached HEAD a5d6718] chore: Create second file
     Date: Wed Jun 10 12:15:30 2026 +0200
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 exercise_one/test2.md
    Successfully rebased and updated refs/heads/master.
    
    PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (master)
    $ git log
    commit d6e6ab9068ba5bf280b0247af4ea4af9a027f366 (HEAD -> master)
    Author: htonnyg@gmail.com <htonnyg@gmail.com>
    Date:   Wed Jun 10 12:15:31 2026 +0200
    
        Added and commited test4.md
    
    commit a5d6718ae4c1b576e2961157cf19fafcd4ec58ff
    Author: htonnyg@gmail.com <htonnyg@gmail.com>
    Date:   Wed Jun 10 12:15:30 2026 +0200
    
        chore: Create second file
    
    commit 1efdf55b9fccc1fe0769970d998907160e6c535d
    Author: htonnyg@gmail.com <htonnyg@gmail.com>
    Date:   Wed Jun 10 12:15:29 2026 +0200
    
        chore: Create initial file


   ```

4. **Keeping History Tidy - Squashing Commits:**

   - Squashing combines multiple commits into a single one. Let's merge "Create second file" into "Create initial file" for a cleaner history.

   **Challenge:** Use interactive rebasing with the `squash` command to achieve this. learn more about `squash`

5. **Splitting a Commit:**

   - Imagine "Create third and fourth files" describes too much at once. Separate them for better tracking with two different commit messages: "Create Third File" and "Create fourth file".

   **Challenge:** Leverage `git reset` to separate the files into individual commits with distinct messages. learn more about `splitting commits`

6. **Advanced Squashing:**

   - Let's explore more complex squashing. Can you combine the last two commits ("Create third file" and "Create fourth file") into a single commit named "Create third and fourth files"?

   **Challenge:** Utilize interactive rebasing with the `squash` command to achieve this advanced squash. **Check step 4**
   ```
   $ git status
   On branch main
   Your branch and 'origin/main' have diverged,
   and have 3 and 2 different commits each, respectively.
     (use "git pull" if you want to integrate the remote branch with yours)
   
   nothing to commit, working tree clean
   
   Stopped at 5627c59...  # chore: Create third and fourth files
   You can amend the commit now, with
   
     git commit --amend
   
   Once you are satisfied with your changes, run
   
     git rebase --continue
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|REBASE 1/2)
   $ git reset HEAD~1
   bash: $'\302\203git': command not found
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|REBASE 1/2)
   $ git status
   interactive rebase in progress; onto c2c2f8d
   Last command done (1 command done):
      edit 5627c59 # chore: Create third and fourth files
   Next command to do (1 remaining command):
      pick 3362ef9 # Added and commited test4.md
     (use "git rebase --edit-todo" to view and edit)
   You are currently editing a commit while rebasing branch 'main' on 'c2c2f8d'.
     (use "git commit --amend" to amend the current commit)
     (use "git rebase --continue" once you are satisfied with your changes)
   
   nothing to commit, working tree clean
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|REBASE 1/2)
   $ git reset~1
   bash: $'\302\203git': command not found
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|REBASE 1/2)
   $ git reset HEAD~1
   bash: $'\302\203git': command not found
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|REBASE 1/2)
   $ git reset HEAD^
   bash: $'\302\203git': command not found
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|REBASE 1/2)
   $ git reset HEAD~
   bash: $'\302\203git': command not found
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|REBASE 1/2)
   $ git reset c2c2f8d
   bash: $'\302\203git': command not found
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|REBASE 1/2)
   $ git reset --mixed HEAD~1
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|REBASE 1/2)
   $ git status
   interactive rebase in progress; onto c2c2f8d
   Last command done (1 command done):
      edit 5627c59 # chore: Create third and fourth files
   Next command to do (1 remaining command):
      pick 3362ef9 # Added and commited test4.md
     (use "git rebase --edit-todo" to view and edit)
   You are currently editing a commit while rebasing branch 'main' on 'c2c2f8d'.
     (use "git commit --amend" to amend the current commit)
     (use "git rebase --continue" once you are satisfied with your changes)
   
   Untracked files:
     (use "git add <file>..." to include in what will be committed)
           test3.md
   
   nothing added to commit but untracked files present (use "git add" to track)
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|REBASE 1/2)
   $ git add test3.md
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|REBASE 1/2)
   $ git commit -m 'Created Third File'
   [detached HEAD a60ad3f] Created Third File
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 exercise_one/test3.md
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|REBASE 1/2)
   $ git status
   interactive rebase in progress; onto c2c2f8d
   Last command done (1 command done):
      edit 5627c59 # chore: Create third and fourth files
   Next command to do (1 remaining command):
      pick 3362ef9 # Added and commited test4.md
     (use "git rebase --edit-todo" to view and edit)
   You are currently editing a commit while rebasing branch 'main' on 'c2c2f8d'.
     (use "git commit --amend" to amend the current commit)
     (use "git rebase --continue" once you are satisfied with your changes)
   
   nothing to commit, working tree clean
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|REBASE 1/2)
   $ git rebase --continue
   
   Stopped at 4e43fc7...  # Create Fourth File
   You can amend the commit now, with
   
     git commit --amend
   
   Once you are satisfied with your changes, run
   
     git rebase --continue
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|REBASE 2/2)
   $ git commit --amend -m 'Create Third and Fourth File'
   [detached HEAD 43d1f9a] Create Third and Fourth File
    Date: Wed Jun 10 12:15:31 2026 +0200
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 exercise_one/test4.md
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|REBASE 2/2)
   $ git rebase --continue
   Successfully rebased and updated refs/heads/main.
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git log --oneline
   43d1f9a (HEAD -> main) Create Third and Fourth File
   50105b5 chore: Create initial file

   ```

 
8. **Dropping a Commit:**

   - We all make mistakes. Imagine needing to completely remove an unwanted commit from your history.

   - Create a new file named `unwanted.txt` add some changes and commit it with a message like "Unwanted commit".

   **Challenge:** Use `git rebase -i` to identify and remove the "Unwanted commit" commit, cleaning up your history. learn more about `dropping commits`

9. **Reordering Commits:**

   - Delve deeper into `git rebase -i`. Can you rearrange commits within your history using this command? learn more about `ordering commits` 

10. **Cherry-Picking Commits:**

   - Create a branch, call it `ft/branch`, and add a new file named `test5.md` with some content. Commit these changes with a message like "Implemented test 5".
   - Imagine you only desire a specific commit from `ft/branch`. Research and use `git cherry-pick` to selectively bring that commit into your current branch which is `main`.
   
   learn more about `cherry-pick`

11. **Visualizing Commit History (Bonus):**

   - Tools like `git log --graph` or a graphical Git client can help visualize your commit history. Explore these tools for a clearer understanding of your workflow.

11. **Understanding Reflogs (Bonus):**

   - Reflogs track Git operation history. Research about `git reflog` to learn how you can navigate back to previous states in your repository if needed.
