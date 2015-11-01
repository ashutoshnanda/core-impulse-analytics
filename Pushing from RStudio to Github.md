This is mostly as a reference guide to myself, but anyone with the same environment (on Mac before OS X 10.11, coding in RStudio, pushing to GitHub) should feel free to use it. I conjecture that this only needs to be done once per machine, but that is left as an exercise to the reader. ;)

#What do all these things do?

Good question. Git is a *version control* system; it keeps track of all of your source code and how it changes, meaning that it allows you to go back to previous versions of code when stuff breaks. GitHub is a place where you can store Git repositories online, so that others may also view them; although GitHub provides a (beautiful) visual front-end to your Git repository, you do not need to use GitHub if you're using Git. RStudio is where we'll be programming our various scripts (the source code).

#What if I don't do the things in this document?

Without following these directions, you'll have to do all of the Git operations (staging files, committing them, pushing to the remote repository, etc.) on the command line. But who likes switching between two applications?

#What if I follow this document?

You'll be able to manage your Git repository from within RStudio. Woo for efficiency!

#Steps to Making RStudio and GitHub play nicely with each other

(This document assumes that you already have an RStudio project that has version control enabled. If that isn't the case, check [here](https://support.rstudio.com/hc/en-us/articles/200526207-Using-Projects).)

There are a couple hoops to jump through, so let's get started:

1. Install [`mac-ssh-askpass`](https://github.com/markcarver/mac-ssh-askpass); if you use `brew`, [this repo](https://github.com/theseal/homebrew-ssh-askpass) might be very handy: `brew tap theseal/ssh-askpass; brew install ssh-askpass`. In any case, make sure to run this line when you're done: `sudo ln -s /usr/local/bin/ssh-askpass /usr/libexec/ssh-askpass`. (Change the first path if you didn't install with `brew`.)

2. Set up your repository with an SSH URL rather than an HTTPS URL: `git remote add origin git@github.com:<USERNAME>/<REPONAME>.git`. If you've already added a remote, this information is also located in `<REPODIR>/.git/config`; just look for the heading `[remote "origin"]` and add the following line: `url = git@github.com:<USERNAME>/<REPONAME>.git`.

3. For the final bit of magic, walk through [this article](https://help.github.com/articles/generating-ssh-keys/). This will make sure that your computer can talk to GitHub.

You've made it! Hopefully, you can now push from RStudio to GitHub. Try it by pushing the "Push" button (with green up arrow next to it) in the Git pane.