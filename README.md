# git-tutorial
git tutorial
#### 1. How to squash commit from working branch (only 1 commit on branch)
##### Case 1: Working branch isn't conflict with dev branch
1. Commit to “woking branch”
2. Checkout the dev branch
 -> ```git checkout dev & git pull origin dev```
3. Checkout to "working branch"
  -> ```git checkout "working branch"```
4. rebase dev branch
  -> ```git rebase -i dev```
  editor will show all of commit massages with the format: ```pick commit_id commit_message```
    ```  
      pick a02bd1a this is commit 1
      pick 058cf8f this is commit 2
      pick 5fd1b03 this is commit 3
    ```
    ![Alt text](https://i.imgur.com/PSj9243.jpg)
    change ```pick``` to ```f``` if you want to remove this message.
     ```  
      pick a02bd1a this is commit 1
      f 058cf8f this is commit 2
      f 5fd1b03 this is commit 3
    ```
    ![Alt text](https://i.imgur.com/6TOMXAw.jpg)
    Keep the message commit 1 and remove commit 2, commit 3.
    Save and exit editor
5. Force push branch to remote repository
    -> ```git push origin "working branch" --force```
##### Case 2: Working branch is conflict with dev branch

1. Solve conflict and commit to “woking branch”
2. Checkout the dev branch
 -> ```git checkout dev & git pull origin dev```
3. Create a new branch from it(dev) as follows
->```git checkout -b (feat/fix/refactor/…)/ga-xxx```
4. Squash merge with your local branch that you have already
 -> ```git merge --squash “woking branch”```
5. Commit your changes (this will be the only commit that goes in dev-branch)
 -> ```git commit -m "ga-xxx message commit"```
6. Push the branch to your local repository
->```git push origin (feat/fix/refactor/…)/ga-xxx```
