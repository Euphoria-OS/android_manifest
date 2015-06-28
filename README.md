$ repo init -u git://github.com/Euphoria-OS/android_manifest.git -b lollipop-5.1

$ repo sync

How to Use Our Gerrit Code Review
 Prerequisites:
Sign up at gerrit.euphoria-os.ninja
Create a username on gerrit (Account Settings -> HTTP Password)
Register your public ssh key (Account Settings -> SSH Keys)
Set your gerrit username on your local machine using: 
git config --global review.eosgerrit.ddns.net.username  “username” (no quotes)
Pushing Commits for review - via repo (suggested way)
You should make sure you use different repo branches for your patch, to ensure you don’t have an unneeded dependency on another patch. Use repo start for every new changeset you make, and repo checkout to switch between your changes. For more on repo and git see Using repo and git Repo usage
repo start <branch> <path to repo>
i.e. repo start testing frameworks/base
cd to working directory
i.e. cd frameworks/base
make your changes
Manually adding changes
Cherry-Picking From another source
Note: If you're cherry-picking a commit that has not gone through a change-Id process, it will not push. We suggest you push the cherry-pick and if it errors because of this requirement, add the suggested change-Id it produces for you using the ‘git commit --amend’ command)
git add to add your files to staging
git add <path to files changed> or git add . for all files changed
commit your changes
git commit
IMPORTANT: Make sure to be descriptive when making your commit message.  The first line of the commit should be a short summary of what the commit changes.  The body of the commit should detail what you changed and why it was changed
upload your changes
repo upload <project path>
i.e. repo upload frameworks/base

Pushing Commits for review (if repo doesn’t work):
cd to your working folder 
add a remote to Euphoria-OS gerrit -- git remote add gerrit ssh://USERNAME@eosgerrit.ddns.net:29418/Euphoria-OS/PROJECTNAME
make all of your changes
Manually adding changes
Cherry-Picking From another source
Note: If you're cherry-picking a commit that has not gone through a change-Id process, it will not push. We suggest you push the cherry-pick and if it errors because of this requirement, add the suggested change-Id it produces for you using the ‘git commit --amend’ command)
Commit your changes
git commit
IMPORTANT: Make sure to be descriptive when making your commit message.  The first line of the commit should be a short summary of what the commit changes.  The body of the commit should detail what you changed and why it was changed.
Push your changes for review
git push <remotenamehere> HEAD:refs/for/branch 
example:
git push gerrit HEAD:refs/for/lollipop-5.1
Do NoT PUSH to gerrit lollipop-5.1, it will not show up
Updating an existing commit in review/rebasing:
 Make sure your previous commit submission is at the head of the repo tree 
if necessary, cherry-pick the commit from gerrit to move it to the top
Make any necessary changes
Add your changes
git add -A
git commit --amend
add to the description if you feel it’s needed
git push gerrit HEAD:refs/for/lollipop-5.1



Thanks to PA & Omnirom for pieces of this information
