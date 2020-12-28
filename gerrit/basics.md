# Gerrit

### To create a change and push for code review
git push origin HEAD:refs/for/branch_name (eg: git push origin HEAD:refs/for/master) The branch should be already created in remote repository.
For each change created the one change-id will be created along with the commit message using commit-msg hook. This should be locally installed on local repository. We can copy this hook from remote repository to local using scp
```
scp -p mygerrit:hooks/commit-msg .git/hooks/
```
If you are amending the change created the new change-id will not be craeted, instaed patch set 2 will be craeted in the same change published.
If you did not amend and push, it will be craeted as new change and the new commit-id will be created.

### To push directly to branch, bypassing the code-review proccess
git push origin branch_name (eg: git push origin master)
To push directly to master you need a proper access.

### To add permissions to push directly to branch without code-review process
1. Craete a Group and add users to that group
![Adding user to group](https://github.com/vigneshsweekaran/notes/blob/master/gerrit/gerrit-adding-users-to-group.PNG)

