---
layout: post
title: Git merge back into any given branch
tags:
  - programming
  - coding
  - git
  - bash
---
Many times as team you branch of to implement new feature using git, and before you finalize your features some new changes are pushed to your base (origin) branch,
you are left with two options 
1. Go ahead and push your code for someone else to look at and fix when merging.
2. Merge back into the origin branch and fix any problems that might arise, then push your code.

It's always prefered to merge back and handle any merge conflicts that might come up.

### Merge back
To merge back you would need to do the following

```bash
git checkout base-branch
git pull origin base-branch
git checkout current-branch
git merge base-branch
```

Although this is simple, it is a tedious job, especially when you have to repeat it many times.

I advise teams to merge back as often as possible to avoid having conficts later on, and to avoid long halts on new features branches as this can have major consequences on the development and code integrity.
### Automating merge backs

Today I published a small good-old bash script to do just that.

To quickly install it run the following command

```bash
wget https://raw.githubusercontent.com/yatabani/scripts/main/merge-back/install.sh
sudo chmod +x install.sh
sudo ./install.sh
```

This will install the mb (merge-back) script into your `/usr/local/sbin` directory

Another option would be to clone the git repo and place a symbolic link to the latest scripts, this will allow you to always get the new code as it is released

```bash
git clone https://github.com/yatabani/scripts.git
sudo ln -s /path/to/scripts/merge-back/mb /usr/local/sbin/mb
```

### Finally

Here is how to use this merge-back script. 

Simply go into the directory of your code and type

```bash
mb master
```

This will merge your current branch into the master branch, you can merge back into any other branch as long as you have originally branched of from it then you should be fine and no major conflicts would occour.

I hope you this helps you out, please feel free to drop me a line down in the comments, or issue on [github](https://github.com/yatabani/scripts)

Happy coding