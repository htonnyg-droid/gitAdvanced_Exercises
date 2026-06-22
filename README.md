**Part 1: Refining Git History (10 Challenges)**
**Note: If the codes seems ununderstandable check the last to see the reflog as it encompasses all that happened**

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

3. **Keeping History Tidy - Squashing Commits:**

   - Squashing combines multiple commits into a single one. Let's merge "Create second file" into "Create initial file" for a cleaner history.

   **Challenge:** Use interactive rebasing with the `squash` command to achieve this. learn more about `squash`

4. **Splitting a Commit:**

   - Imagine "Create third and fourth files" describes too much at once. Separate them for better tracking with two different commit messages: "Create Third File"       and "Create fourth file".

   **Challenge:** Leverage `git reset` to separate the files into individual commits with distinct messages. learn more about `splitting commits`

5. **Advanced Squashing:**

   - Let's explore more complex squashing. Can you combine the last two commits ("Create third file" and "Create fourth file") into a single commit named "Create       third and fourth files"?

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

 
6. **Dropping a Commit:**

   - We all make mistakes. Imagine needing to completely remove an unwanted commit from your history.

   - Create a new file named `unwanted.txt` add some changes and commit it with a message like "Unwanted commit".

   **Challenge:** Use `git rebase -i` to identify and remove the "Unwanted commit" commit, cleaning up your history. learn more about `dropping commits`

7. **Reordering Commits:**

   - Delve deeper into `git rebase -i`. Can you rearrange commits within your history using this command? learn more about `ordering commits`
   ```

   The previous cherry-pick is now empty, possibly due to conflict resolution.
   If you wish to commit it anyway, use:
   
       git commit --allow-empty
   
   Otherwise, please use 'git rebase --skip'
   interactive rebase in progress; onto 6ca623d
   Last commands done (3 commands done):
      pick 43d1f9a # Create Third and Fourth File
      pick 1efdf55 # chore: Create initial file
     (see more in file .git/rebase-merge/done)
   Next commands to do (3 remaining commands):
      pick a5d6718 # chore: Create second file
      pick f94fdaa # first commit with first and second challenge in part 1 of the git advanced exercises
     (use "git rebase --edit-todo" to view and edit)
   You are currently rebasing branch 'main' on '6ca623d'.
     (all conflicts fixed: run "git rebase --continue")
   
   nothing to commit, working tree clean
   Could not apply 1efdf55... # chore: Create initial file
   
   PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (main|REBASE 3/6)
   $ git rebase --skip
   bash: $'\302\203git': command not found
   
   PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (main|REBASE 3/6)
   $ git rebase --skip
   The previous cherry-pick is now empty, possibly due to conflict resolution.
   If you wish to commit it anyway, use:
   
       git commit --allow-empty
   
   Otherwise, please use 'git rebase --skip'
   interactive rebase in progress; onto 6ca623d
   Last commands done (4 commands done):
      pick 1efdf55 # chore: Create initial file
      pick a5d6718 # chore: Create second file
     (see more in file .git/rebase-merge/done)
   Next commands to do (2 remaining commands):
      pick f94fdaa # first commit with first and second challenge in part 1 of the git advanced exercises
      pick d6e6ab9 # Added and commited test4.md
     (use "git rebase --edit-todo" to view and edit)
   You are currently rebasing branch 'main' on '6ca623d'.
     (all conflicts fixed: run "git rebase --continue")
   
   nothing to commit, working tree clean
   Could not apply a5d6718... # chore: Create second file
   
   PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (main|REBASE 4/6)
   $ git rebase --skip
   The previous cherry-pick is now empty, possibly due to conflict resolution.
   If you wish to commit it anyway, use:
   
       git commit --allow-empty
   
   Otherwise, please use 'git rebase --skip'
   interactive rebase in progress; onto 6ca623d
   Last commands done (6 commands done):
      pick f94fdaa # first commit with first and second challenge in part 1 of the git advanced exercises
      pick d6e6ab9 # Added and commited test4.md
     (see more in file .git/rebase-merge/done)
   No commands remaining.
   You are currently rebasing branch 'main' on '6ca623d'.
     (all conflicts fixed: run "git rebase --continue")
   
   nothing to commit, working tree clean
   Could not apply d6e6ab9... # Added and commited test4.md
   
   PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (main|REBASE 6/6)
   $ git rebase --skip
   Successfully rebased and updated refs/heads/main.
   
   PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git log --oneline
   45f18bc (HEAD -> main) first commit with first and second challenge in part 1 of the git advanced exercises
   43d1f9a Create Third and Fourth File
   50105b5 chore: Create initial file
   
   PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git reset --hard origin/main
   bash: $'\302\203git': command not found
   
   PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git reset --hard origin/main
   HEAD is now at 22d7028 Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises pulling previous changes
   
   PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git log --oneline
   22d7028 (HEAD -> main, origin/main, origin/HEAD) Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises pulling previous changes
   43d1f9a Create Third and Fourth File
   50105b5 chore: Create initial file
   f94fdaa first commit with first and second challenge in part 1 of the git advanced exercises
   d6e6ab9 Added and commited test4.md
   a5d6718 chore: Create second file
   1efdf55 chore: Create initial file
   
   PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git checkout -b ft/branch
   Switched to a new branch 'ft/branch'
   
   PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (ft/branch)
   $ echo "test 5 is new" > test5.md
   
   PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (ft/branch)
   $ git add test5.md
   warning: in the working copy of 'exercise_one/test5.md', LF will be replaced by CRLF the next time Git touches it
   
   PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (ft/branch)
   $ git commit -m 'Implemented test5.md'
   bash: $'\302\203git': command not found
   
   PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (ft/branch)
   $ git commit -m 'Implemented test5.md'
   [ft/branch 27eec5a] Implemented test5.md
    1 file changed, 1 insertion(+)
    create mode 100644 exercise_one/test5.md
   
   PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (ft/branch)
   $ git log --oneline
   27eec5a (HEAD -> ft/branch) Implemented test5.md
   22d7028 (origin/main, origin/HEAD, main) Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises pulling previous changes
   43d1f9a Create Third and Fourth File
   50105b5 chore: Create initial file
   f94fdaa first commit with first and second challenge in part 1 of the git advanced exercises
   d6e6ab9 Added and commited test4.md
   a5d6718 chore: Create second file
   1efdf55 chore: Create initial file
   
   PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (ft/branch)
   $ git checkout main
   Switched to branch 'main'
   Your branch is up to date with 'origin/main'.
   
   PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ gi t
   bash: $'\302\203gi': command not found
   
   PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git cherry-pick 27eec5a
   [main 152f196] Implemented test5.md
    Date: Mon Jun 15 11:32:36 2026 +0200
    1 file changed, 1 insertion(+)
    create mode 100644 exercise_one/test5.md
   
   PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git log --oneline
   152f196 (HEAD -> main) Implemented test5.md
   22d7028 (origin/main, origin/HEAD) Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises pulling previous changes
   43d1f9a Create Third and Fourth File
   50105b5 chore: Create initial file
   f94fdaa first commit with first and second challenge in part 1 of the git advanced exercises
   d6e6ab9 Added and commited test4.md
   a5d6718 chore: Create second file
   1efdf55 chore: Create initial file
   
   PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git log --graph
   * commit 152f19689736de93e133a03f08a9d7cdc23f68ad (HEAD -> main)
   | Author: htonnyg@gmail.com <htonnyg@gmail.com>
   | Date:   Mon Jun 15 11:32:36 2026 +0200
   |
   |     Implemented test5.md
   |
   *   commit 22d702846b3f0cbf92ea4c8d666cbf7a81eaf032 (origin/main, origin/HEAD)
   |\  Merge: 43d1f9a f94fdaa
   | | Author: htonnyg@gmail.com <htonnyg@gmail.com>
   | | Date:   Thu Jun 11 11:22:20 2026 +0200
   | |
   | |     Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises
   | |     pulling previous changes
   | |
   | * commit f94fdaa5799d066a88b5ba6765d8102484ed13a4
   | | Author: htonnyg-droid <htonnyg@gmail.com>
   | | Date:   Wed Jun 10 16:35:42 2026 +0200
   | |
   | |     first commit with first and second challenge in part 1 of the git advanced exercises
   | |
   | * commit d6e6ab9068ba5bf280b0247af4ea4af9a027f366
   | | Author: htonnyg@gmail.com <htonnyg@gmail.com>
   | | Date:   Wed Jun 10 12:15:31 2026 +0200
   | |
   | |     Added and commited test4.md
   | |
   | * commit a5d6718ae4c1b576e2961157cf19fafcd4ec58ff
   | | Author: htonnyg@gmail.com <htonnyg@gmail.com>
   | | Date:   Wed Jun 10 12:15:30 2026 +0200
   | |
   | |     chore: Create second file
   | |
   | * commit 1efdf55b9fccc1fe0769970d998907160e6c535d
   |   Author: htonnyg@gmail.com <htonnyg@gmail.com>
   |   Date:   Wed Jun 10 12:15:29 2026 +0200
   
      remote: Enumerating objects: 5, done.
      remote: Counting objects: 100% (5/5), done.
      remote: Compressing objects: 100% (3/3), done.
      remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
      Unpacking objects: 100% (3/3), 1.88 KiB | 147.00 KiB/s, done.
      From https://github.com/htonnyg-droid/gitAdvanced_Exercises
       * branch            main       -> FETCH_HEAD
         22d7028..89d552f  main       -> origin/main
      Merge made by the 'ort' strategy.
       README.md | 138 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++--
       1 file changed, 134 insertions(+), 4 deletions(-)
      
      PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (main)
      $ git push origin main
      Enumerating objects: 10, done.
      Counting objects: 100% (9/9), done.
      Delta compression using up to 8 threads
      Compressing objects: 100% (5/5), done.
      Writing objects: 100% (6/6), 679 bytes | 679.00 KiB/s, done.
      Total 6 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
      remote: Resolving deltas: 100% (1/1), completed with 1 local object.
      To https://github.com/htonnyg-droid/gitAdvanced_Exercises.git
         89d552f..96fbb8b  main -> main
      
      PC@Tonnys MINGW64 /C/Users/PC/Desktop/web_design/Git&GitHub/exercise_one (main)
      $ git push origin ft/branch
      Enumerating objects: 6, done.
      Counting objects: 100% (6/6), done.
      Delta compression using up to 8 threads
      Compressing objects: 100% (3/3), done.
      Writing objects: 100% (4/4), 363 bytes | 181.00 KiB/s, done.
      Total 4 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
      remote: Resolving deltas: 100% (1/1), completed with 1 local object.
      remote:
      remote: Create a pull request for 'ft/branch' on GitHub by visiting:
      remote:      https://github.com/htonnyg-droid/gitAdvanced_Exercises/pull/new/ft/branch
      remote:
      To https://github.com/htonnyg-droid/gitAdvanced_Exercises.git
       * [new branch]      ft/branch -> ft/branch

   ```

8. **Cherry-Picking Commits:**

   - Create a branch, call it `ft/branch`, and add a new file named `test5.md` with some content. Commit these changes with a message like "Implemented test 5".
   - Imagine you only desire a specific commit from `ft/branch`. Research and use `git cherry-pick` to selectively bring that commit into your current branch          which is `main`.
   
   learn more about `cherry-pick`

9. **Visualizing Commit History (Bonus):**

   - Tools like `git log --graph` or a graphical Git client can help visualize your commit history. Explore these tools for a clearer understanding of your             workflow.

10. **Understanding Reflogs (Bonus):**

   - Reflogs track Git operation history. Research about `git reflog` to learn how you can navigate back to previous states in your repository if needed.
```
      PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
      $ git reflog
      96fbb8b (HEAD -> main, origin/main, origin/HEAD) HEAD@{0}: pull origin main: Merge made by the 'ort' strategy.
      152f196 HEAD@{1}: cherry-pick: Implemented test5.md
      22d7028 HEAD@{2}: checkout: moving from ft/branch to main
      27eec5a (origin/ft/branch, ft/branch) HEAD@{3}: commit: Implemented test5.md
      22d7028 HEAD@{4}: checkout: moving from main to ft/branch
      22d7028 HEAD@{5}: reset: moving to origin/main
      45f18bc HEAD@{6}: rebase (finish): returning to refs/heads/main
      45f18bc HEAD@{7}: rebase (pick): first commit with first and second challenge in part 1 of the git advanced exercises
      43d1f9a HEAD@{8}: rebase: fast-forward
      50105b5 HEAD@{9}: rebase: fast-forward
      6ca623d HEAD@{10}: rebase (start): checkout 6ca623d3ccbf39e574c7de157ce6a159cb7dd6dc
      22d7028 HEAD@{11}: rebase (abort): returning to refs/heads/main
      50105b5 HEAD@{12}: rebase: fast-forward
      0fe386e HEAD@{13}: rebase (start): checkout 0fe386eed7dfc9d28e286ceb106f8c140579380f
      22d7028 HEAD@{14}: rebase (abort): returning to refs/heads/main
      43d1f9a HEAD@{15}: rebase: fast-forward
      50105b5 HEAD@{16}: rebase: fast-forward
      5c9e3db HEAD@{17}: rebase (start): checkout 5c9e3dbe16f6ca10cac4cf81e6cf9f4a4682c55b
      22d7028 HEAD@{18}: rebase (finish): returning to refs/heads/main
      22d7028 HEAD@{19}: rebase (start): checkout HEAD~1
      3667ba6 HEAD@{20}: rebase (abort): returning to refs/heads/main
      43d1f9a HEAD@{21}: rebase (start): checkout HEAD~2
      3667ba6 HEAD@{22}: commit: Unwanted Commit
      22d7028 HEAD@{23}: pull origin main --allow-unrelated-histories: Merge made by the 'ort' strategy.
      43d1f9a HEAD@{24}: rebase (finish): returning to refs/heads/main
      43d1f9a HEAD@{25}: commit (amend): Create Third and Fourth File
      4e43fc7 HEAD@{26}: rebase: fast-forward
      50105b5 HEAD@{27}: rebase: fast-forward
      dba4e85 HEAD@{28}: rebase (start): checkout dba4e85479b31ca08548d1c841d7d9ed4fc773dd
      4e43fc7 HEAD@{29}: rebase (finish): returning to refs/heads/main
      4e43fc7 HEAD@{30}: rebase: fast-forward
      50105b5 HEAD@{31}: rebase: fast-forward
      7dd4915 HEAD@{32}: rebase (start): checkout 7dd49150583b07aeb9f3296631cefe0fc0625246
      4e43fc7 HEAD@{33}: rebase (finish): returning to refs/heads/main
      4e43fc7 HEAD@{34}: rebase (pick): Create Fourth File
      50105b5 HEAD@{35}: rebase (squash): chore: Create initial file
      c2c2f8d HEAD@{36}: rebase: fast-forward
      9a943c3 HEAD@{37}: rebase (start): checkout 9a943c39d781b4cb88af79438d21841c106efad5
      5c8e06d HEAD@{38}: rebase (finish): returning to refs/heads/main
      5c8e06d HEAD@{39}: commit (amend): Create Fourth File
      03813bd HEAD@{40}: rebase: fast-forward
      a60ad3f HEAD@{41}: rebase: fast-forward
      c2c2f8d HEAD@{42}: rebase: fast-forward
      5fa000c HEAD@{43}: rebase (start): checkout 5fa000ce5effcbf8eef9a107e0e2c170d06da2ad
      03813bd HEAD@{44}: rebase (finish): returning to refs/heads/main
      03813bd HEAD@{45}: rebase (pick): Added and commited test4.md
      a60ad3f HEAD@{46}: commit: Created Third File
      c2c2f8d HEAD@{47}: reset: moving to HEAD~1
      5627c59 HEAD@{48}: rebase: fast-forward
      c2c2f8d HEAD@{49}: rebase (start): checkout HEAD~2
      3362ef9 HEAD@{50}: rebase (finish): returning to refs/heads/main
      3362ef9 HEAD@{51}: rebase (pick): Added and commited test4.md
      5627c59 HEAD@{52}: rebase (pick): chore: Create third and fourth files
      c2c2f8d HEAD@{53}: rebase (squash): chore: Create initial file
      1efdf55 HEAD@{54}: rebase: fast-forward
      60f593d HEAD@{55}: rebase (start): checkout 60f593ddbd3f2a0e43eb0cbddadf1751a9ba1936
      d907c8b HEAD@{56}: rebase (finish): returning to refs/heads/main
      d907c8b HEAD@{57}: rebase (start): checkout d7316e1
      d907c8b HEAD@{58}: reset: moving to HEAD
      d907c8b HEAD@{59}: rebase (finish): returning to refs/heads/main
      
      PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)

```
**Part 2: Branching Basics (10 Challenges)**

1. **Feature Branch Creation:**

   - Imagine working on a new feature named `ft/new-feature`. Let's establish a dedicated branch for it.

   **Challenge:** Create a new branch named `ft/new-feature` and switch to that branch.

2. **Working on the Feature Branch:**

   - Create a new file named `feature.txt` in this branch and add some content to it.
   - Commit these changes with a descriptive message like "Implemented core functionality for new feature".

3. **Switching Back and Making More Changes:**

   - It's common to switch between branches during development.

   **Challenge:** Switch back to the `main` branch (previously master) and create a new file named `readme.txt` with some introductory content. Commit these changes with a message like "Updated project readme".


4. **Local vs. Remote Branches:**

   - So far, we've been working with local branches that exist on your machine. Research the concept of remote branches, which are copies of your local branches stored on a Git hosting platform like GitHub.
   
5. **Branch Deletion:**

   - After merging or completing work on a feature branch, it's good practice to remove it.

   **Challenge:** Delete the `ft/new-feature` branch once you're confident the changes are integrated into `main`.
   
   # Here's the code and graph from 1-5
   ```
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (ft/new-feature)
   $ touch feature.txt

   Merge made by the 'ort' strategy.
    exercise_one/feature.txt | 0
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 exercise_one/feature.txt
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git branch -d ft/new-feature
   Deleted branch ft/new-feature (was f305db4).
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git push origin --delete ft/new-feature
   To https://github.com/htonnyg-droid/gitAdvanced_Exercises.git
    - [deleted]         ft/new-feature
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git log --oneline
   6e09cb1 (HEAD -> main) Merging branch 'ft/new-feature' to 'main'
   6a5ea7e Updated project readme
   f305db4 Implemented core functionality for new feature
   7b81774 (origin/main, origin/HEAD) Final update to part 1
   95117e2 Update README.md
   96fbb8b Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises
   152f196 Implemented test5.md
   89d552f Update README.md by adding codes for 3, 4 and 5
   22d7028 Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises pulling previous changes
   43d1f9a Create Third and Fourth File
   50105b5 chore: Create initial file
   f94fdaa first commit with first and second challenge in part 1 of the git advanced exercises
   d6e6ab9 Added and commited test4.md
   a5d6718 chore: Create second file
   1efdf55 chore: Create initial file
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git graph --oneline
   git: 'graph' is not a git command. See 'git --help'.
   
   The most similar commands are
           branch
           grep
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git log --graph --oneline
   *   6e09cb1 (HEAD -> main) Merging branch 'ft/new-feature' to 'main'
   |\
   | * f305db4 Implemented core functionality for new feature
   * | 6a5ea7e Updated project readme
   |/
   * 7b81774 (origin/main, origin/HEAD) Final update to part 1
   * 95117e2 Update README.md
   *   96fbb8b Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises
   |\
   | * 89d552f Update README.md by adding codes for 3, 4 and 5
   * | 152f196 Implemented test5.md
   |/
   *   22d7028 Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises pulling previous changes
   |\
   | * f94fdaa first commit with first and second challenge in part 1 of the git advanced exercises
   | * d6e6ab9 Added and commited test4.md
   | * a5d6718 chore: Create second file
   | * 1efdf55 chore: Create initial file
   * 43d1f9a Create Third and Fourth File
   * 50105b5 chore: Create initial file

   ```
   6. **Creating a Branch from a Commit:**

   - You can also create a branch from a specific commit in your history.

   **Challenge:** Use `git checkout -b ft/new-branch-from-commit commit-hash` (adjust the commit hash as needed) to create a new branch named `ft/new-branch-from-commit` starting from the commit two positions back in your history. 

7. **Branch Merging:**

   - Now that you've completed work on your feature branch, it's time to integrate it into `main`.

   **Challenge:** Merge the `ft/new-branch-from-commit` branch into the `main` branch. Address any merge conflicts that might arise.

8. **Branch Rebasing:**

   - Rebasing is another method to integrate changes from a feature branch. It rewrites your branch history by incorporating its commits on top of the latest commit in the target branch (`main` in our case).

   **Challenge:** Try rebasing the `ft/new-branch-from-commit` branch onto the `main` branch. Remember, rebasing rewrites history, so use it with caution, especially in shared repositories.

9. **Renaming Branches:**

   - Branch names can sometimes evolve. Let's rename `ft/new-branch-from-commit` to a more descriptive name.

   **Challenge:** Use `git branch -m ft/new-branch-from-commit ft/improved-branch-name` to rename your branch.

10. **Checking Out Detached HEAD:**

   - In specific situations, you might need to detach HEAD from your current branch. Research `git checkout <commit-hash>` (replace with the desired commit hash) to understand this concept.

   # Answers(part 2: (6-10)
   ```
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git checkout -b ft/new-branch-from-commit 6e09cb1
   Switched to a new branch 'ft/new-branch-from-commit'

   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (ft/new-branch-from-commit)
   $ git log --oneline
   6e09cb1 (HEAD -> ft/new-branch-from-commit) Merging branch 'ft/new-feature' to 'main'
   6a5ea7e Updated project readme
   f305db4 Implemented core functionality for new feature
   7b81774 Final update to part 1
   95117e2 Update README.md
   96fbb8b Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises
   152f196 Implemented test5.md
   89d552f Update README.md by adding codes for 3, 4 and 5
   22d7028 Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises pulling previous changes
   43d1f9a Create Third and Fourth File
   50105b5 chore: Create initial file
   f94fdaa first commit with first and second challenge in part 1 of the git advanced exercises
   d6e6ab9 Added and commited test4.md
   a5d6718 chore: Create second file
   1efdf55 chore: Create initial file
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (ft/new-branch-from-commit)
   $ git checkout main
   Switched to branch 'main'
   Your branch is ahead of 'origin/main' by 4 commits.
     (use "git push" to publish your local commits)
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git merge ft/new-branch-from-commit
   Already up to date.
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git checkout ft/new-branch-from-commit
   Switched to branch 'ft/new-branch-from-commit'
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (ft/new-branch-from-commit)
   $ git rebase main
   Successfully rebased and updated refs/heads/ft/new-branch-from-commit.
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (ft/new-branch-from-commit)
   $ git log --oneline
   c7eddd4 (HEAD -> ft/new-branch-from-commit, main) Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises
   41167fe (origin/main, origin/HEAD) Update README.md
   6e09cb1 Merging branch 'ft/new-feature' to 'main'
   6a5ea7e Updated project readme
   f305db4 Implemented core functionality for new feature
   7b81774 Final update to part 1
   95117e2 Update README.md
   96fbb8b Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises
   152f196 Implemented test5.md
   89d552f Update README.md by adding codes for 3, 4 and 5
   22d7028 Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises pulling previous changes
   43d1f9a Create Third and Fourth File
   50105b5 chore: Create initial file
   f94fdaa first commit with first and second challenge in part 1 of the git advanced exercises
   d6e6ab9 Added and commited test4.md
   a5d6718 chore: Create second file
   1efdf55 chore: Create initial file
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (ft/new-branch-from-commit)
   $ git branch -m ft/new-branch-from-commit ft/improved-branch-name
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (ft/improved-branch-name)
   $ git checkout -b ft/new-branch-from-commit 6a5ea7e
   Switched to a new branch 'ft/new-branch-from-commit'
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (ft/new-branch-from-commit)
   $ git rebase main
   Successfully rebased and updated refs/heads/ft/new-branch-from-commit.
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (ft/new-branch-from-commit)
   $ git log --oneline
   c7eddd4 (HEAD -> ft/new-branch-from-commit, main, ft/improved-branch-name) Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises
   41167fe (origin/main, origin/HEAD) Update README.md
   6e09cb1 Merging branch 'ft/new-feature' to 'main'
   6a5ea7e Updated project readme
   f305db4 Implemented core functionality for new feature
   7b81774 Final update to part 1
   95117e2 Update README.md
   96fbb8b Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises
   152f196 Implemented test5.md
   89d552f Update README.md by adding codes for 3, 4 and 5
   22d7028 Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises pulling previous changes
   43d1f9a Create Third and Fourth File
   50105b5 chore: Create initial file
   f94fdaa first commit with first and second challenge in part 1 of the git advanced exercises
   d6e6ab9 Added and commited test4.md
   a5d6718 chore: Create second file
   1efdf55 chore: Create initial file
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (ft/new-branch-from-commit)
   $ git checkout main
   Switched to branch 'main'
   Your branch is ahead of 'origin/main' by 4 commits.
     (use "git push" to publish your local commits)
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git branch -d ft/new-branch-from-commit
   Deleted branch ft/new-branch-from-commit (was c7eddd4).
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git log --oneline
   c7eddd4 (HEAD -> main, ft/improved-branch-name) Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises
   41167fe (origin/main, origin/HEAD) Update README.md
   6e09cb1 Merging branch 'ft/new-feature' to 'main'
   6a5ea7e Updated project readme
   f305db4 Implemented core functionality for new feature
   7b81774 Final update to part 1
   95117e2 Update README.md
   96fbb8b Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises
   152f196 Implemented test5.md
   89d552f Update README.md by adding codes for 3, 4 and 5
   22d7028 Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises pulling previous changes
   43d1f9a Create Third and Fourth File
   50105b5 chore: Create initial file
   f94fdaa first commit with first and second challenge in part 1 of the git advanced exercises
   d6e6ab9 Added and commited test4.md
   a5d6718 chore: Create second file
   1efdf55 chore: Create initial file
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git branch
     ft/branch
     ft/improved-branch-name
   * main

   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git checkout f305db4
   Note: switching to 'f305db4'.
   
   You are in 'detached HEAD' state. You can look around, make experimental
   changes and commit them, and you can discard any commits you make in this
   state without impacting any branches by switching back to a branch.
   
   If you want to create a new branch to retain commits you create, you may
   do so (now or later) by using -c with the switch command. Example:
   
     git switch -c <new-branch-name>
   
   Or undo this operation with:
   
     git switch -
   
   Turn off this advice by setting config variable advice.detachedHead to false
   
   HEAD is now at f305db4 Implemented core functionality for new feature
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one ((f305db4...))
   $ git checkout main
   Previous HEAD position was f305db4 Implemented core functionality for new feature
   Switched to branch 'main'
   Your branch is ahead of 'origin/main' by 4 commits.
     (use "git push" to publish your local commits)
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)

   ```
 # Part 3
   **Part 3: Advanced Workflows (10+ Challenges)**

1. **Stashing Changes:**

   - Imagine you're working on some changes in the `main` branch but need to attend to something urgent. You don't want to lose your uncommitted work.

   **Challenge:** Stash your current changes in the `main` branch using `git stash`.

2. **Retrieving Stashed Changes:**

   - Later, when you're ready to resume working on those stashed changes, you can retrieve them.

   **Challenge:** Apply the most recent stash back onto the `main` branch using `git stash pop`.

3. **Branch Merging Conflicts (Continued):**

   - Merge conflicts can arise when the same lines of code are modified in both branches being merged.

   **Challenge:** Simulate a merge conflict scenario (you can create conflicting changes in a file on both `main` and a new feature branch). Then, try merging again and resolve the conflicts manually using your text editor.

4. **Resolving Merge Conflicts with a Merge Tool:**

   - Explore using a merge tool like `git mergetool` to help you visualize and resolve merge conflicts more efficiently.
# Answers for 1-4


   ```
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ echo "Work in progress" >> feature.txt
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git stash
   warning: in the working copy of 'exercise_one/feature.txt', LF will be replaced by CRLF the next time Git touches it
   Saved working directory and index state WIP on main: f65a02f Merge branch 'main' of https://github.com/htonnyg-droid/gitAdvanced_Exercises
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git status
   On branch main
   Your branch is up to date with 'origin/main'.
   
   nothing to commit, working tree clean
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git stash pop
   On branch main
   Your branch is up to date with 'origin/main'.
   
   Changes not staged for commit:
     (use "git add <file>..." to update what will be committed)
     (use "git restore <file>..." to discard changes in working directory)
           modified:   feature.txt
   
   no changes added to commit (use "git add" and/or "git commit -a")
   Dropped refs/stash@{0} (9d707dec7d5affb45ec458ab129e12c748dd0fbb)
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ echo "Hello from here from main" > file.txt
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git add file.txt
   warning: in the working copy of 'exercise_one/file.txt', LF will be replaced by CRLF the next time Git touches it
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git commit -m 'modified file.txt in main'
   [main fe333aa] modified file.txt in main
    1 file changed, 1 insertion(+), 1 deletion(-)
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git checkout -b ft/conflict-branch2 HEAD~1
   Switched to a new branch 'ft/conflict-branch2'
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (ft/conflict-branch2)
   $ echo "hello again from conflict" > file.txt
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (ft/conflict-branch2)
   $ git add file.txt
   warning: in the working copy of 'exercise_one/file.txt', LF will be replaced by CRLF the next time Git touches it
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (ft/conflict-branch2)
   $ git commit -m "modified file.txt in conflict2"
   [ft/conflict-branch2 cdad0c5] modified file.txt in conflict2
    1 file changed, 1 insertion(+), 1 deletion(-)
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (ft/conflict-branch2)
   $ git checkout main
   Switched to branch 'main'
   Your branch is ahead of 'origin/main' by 4 commits.
     (use "git push" to publish your local commits)
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git merge ft/conflict-branch2
   Auto-merging exercise_one/file.txt
   CONFLICT (content): Merge conflict in exercise_one/file.txt
   Automatic merge failed; fix conflicts and then commit the result.
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|MERGING)
   $ cat file.txt
   <<<<<<< HEAD
   Hello from here from main
   =======
   hello again from conflict
   >>>>>>> ft/conflict-branch2
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|MERGING)
   $ echo "Hellooooooo" > file.txt
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|MERGING)
   $ git add file.txt
   warning: in the working copy of 'exercise_one/file.txt', LF will be replaced by CRLF the next time Git touches it
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|MERGING)
   $ git commit -m 'Resolved conflict'
   [main b4ca07f] Resolved conflict
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ echo "Hello again" > file.txt
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git add file.txt
   warning: in the working copy of 'exercise_one/file.txt', LF will be replaced by CRLF the next time Git touches it
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git commit -m "Changed file.txt again"
   [main 7e1e2b5] Changed file.txt again
    1 file changed, 1 insertion(+), 1 deletion(-)
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git checkout -b ft/conflict-branch3 HEAD~1
   Switched to a new branch 'ft/conflict-branch3'
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (ft/conflict-branch3)
   $ echo "Again hello" > file.txt
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (ft/conflict-branch3)
   $ git add file.txt && git commit -m "Changed file.txt in conflict3"
   warning: in the working copy of 'exercise_one/file.txt', LF will be replaced by CRLF the next time Git touches it
   [ft/conflict-branch3 476a21f] Changed file.txt in conflict3
    1 file changed, 1 insertion(+), 1 deletion(-)
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (ft/conflict-branch3)
   $ git checkout main
   Switched to branch 'main'
   Your branch is ahead of 'origin/main' by 7 commits.
     (use "git push" to publish your local commits)
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main)
   $ git merge ft/conflict-branch3
   Auto-merging exercise_one/file.txt
   CONFLICT (content): Merge conflict in exercise_one/file.txt
   Automatic merge failed; fix conflicts and then commit the result.
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|MERGING)
   $ git mergetool --tool=vscode
   Merging:
   exercise_one/file.txt
   
   Normal merge conflict for 'exercise_one/file.txt':
     {local}: modified file
     {remote}: modified file
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|MERGING)
   $ git mergetool --tool=vscode
   No files need merging
   
   PC@Tonnys MINGW64 ~/Desktop/web_design/Git&GitHub/exercise_one (main|MERGING)
   $ git commit -m "Resolved conflict with merged tool"
   [main 52d2f2d] Resolved conflict with merged tool

   ```
5. **Understanding Detached HEAD State:**

   - Detached HEAD refers to a state where your working directory is not associated with any specific branch. Research the implications and how to recover from this state using commands like `git checkout <branch-name>`.

6. **Ignoring Files/Directories:**

   - You might have files or directories you don't want to track in Git. Create a `.gitignore` file to specify these exclusions.

   **Challenge:** Add a pattern like `/tmp` to your `.gitignore` file to exclude all temporary files and directories from version control. more about `ignoring files` [here](https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files)

7. **Working with Tags:**

   - Tags act like bookmarks in your Git history. Create a tag to mark a specific point in your development.

   **Challenge:** Use `git tag v1.0` to create a tag named `v1.0` on the current commit in your `main` branch.  [git tags](https://www.javatpoint.com/git-tags)


8. **Listing and Deleting Tags:**

   **Challenge:** Use `git tag` to list all existing tags. Then, use `git tag -d <tag-name>` to delete a specific tag (replace `<tag-name>` with the actual tag you want to remove).

9. **Pushing Local Work to Remote Repositories:**

   - Once you're happy with your local changes and branches, it's time to share them with others.

   **Challenge:** Assuming you've set up a remote repository on a Git hosting platform (like GitHub), push the changes with the actual branch you want to push to push your local branch to the remote repository.

10. **Pulling Changes from Remote Repositories:**

   - Collaboration often involves pulling changes from the remote repository made by others.

   **Challenge:** Navigate to Github and make some changes inside your `README` file that you created on your `main` branch and in your local environment use `git pull origin <branch-name>` (replace `<branch-name>` with the actual branch you want to pull) to fetch changes from the remote repository's `main` branch and merge them into your local `main` branch. Address any merge conflicts that might arise.
