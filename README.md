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
