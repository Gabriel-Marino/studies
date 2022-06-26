# _'Introdução ao Git e ao Github'_, _'Trabalhando com Branches no Github'_ and _'Git e Github focado em PullRequest'_ class notes from Digital Innovation One

[Digital Innovation One | Dio](https://dio.me)

----------------------------------------------------------------------------------------------------------------------------------------------------------------------
## Begging with GIT and Authenticating

* at the any directory you can run the following command to generate a ssh key and authenticate github with the git cli.
``` bash
    [user@dir ]$ ssh-keygen -t ed25519 -C <email_registered_on_github>
```

* go to the key directory and get the ssh public key (first line of the following commands) - the public key is the file ended with .pub - then go to github and add the key to you account; then initate the ssh agent (second line of the following commands) and the add your private key (third line of the following commands).
``` bash
    [user@key-dir ]$ cat id_ed25519.pub
    [user@key-dir ]$ eval $(ssh-agent -s)
    [user@key-dir ]$ ssh-add id_ed25519
```

* then you can clone any of yours repositorys from github with the ssh key of the repo with the following command.
``` bash
    [user@dir ]$ git clone <ssh key>
```

[GitHub docs about autheticating via ssh](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

<!------------------------------------------------------------------------------------------------------------------------------------------------------------------->

----------------------------------------------------------------------------------------------------------------------------------------------------------------------
## Git Commands

[Git docs](https://git-scm.com/docs)

> **_a good tip is always use --help or -h after the command to see a sum up version of the docs about the command_**

* git config --global user.email &lt;email_registered_on_github&gt; &rarr; command to login into github, so the github can recognize you as the owner of the repo and as author;
* git config --global user.name &lt;name_registered_on_github&gt; &rarr; command to login into github, so the github can recognize you as the owner of the repo and as author;
* git init &rarr; command to iniate a local repository;
* git add . &rarr; add all files from your work area to the repository (move from work area to staging area);
* git commit &rarr; save the changes from the files added (from the git add .) (move from staging area to the repository area);
  * git commit will ask for a commentary of about the commit is, is possible to do this inline using git commit -m "comment";
* git status &rarr; repository status;
* git push &rarr; update remote repositorys;
  * You can push to a specific branch using git push origin &lt;branch&gt;
* git remote add origin &lt;https_url_repo&gt; &rarr; Add the remote location of the repository to your local repository, so you can push your work to the cloud.
* git checkout &rarr; to change between branches;
  * git checkout work like git branch and git switch at the same time and have other functionalities;
  * git checkout -b &lt;name&gt; &rarr; create a new branch;
* git branch -m old_name new_name &rarr; rename branch;
* git merge &rarr; merge branches;
* git log &rarr; show the history of commits;
  * git log --oneline &rarr; show a sum up version of git log;
  * git log --graph &rarr; show a graphic version of git log without a gui;
  * for git bash in windows gitk is a gui tool of git log;
  * [More GIT GUI here!](https://git-scm.com/downloads/guis)
* git statsh &rarr; create a area to save what you're working in a directory and don't carry files from one branch to another;
  * git stash save "comment" &rarr; create the area to save the working files, the comment is a context to you remember what youa re working on;
  * git stash pop &lt;index&gt; &rarr; to open the created stash and back to work with the files saved in the stash, the index is the index of the stash once you can crate countless stashs;
  * git stash list &rarr; list all created stashs;
  * git stash clear &rarr; remove all stashs;
* git config --global core.editor "code --wait"

[A cool tool to see how git manage the files/commits!](https://git-school.github.io/visualizing-git/)

> HEAD is a pointer which contain the last state of the repository.

<!------------------------------------------------------------------------------------------------------------------------------------------------------------------->

----------------------------------------------------------------------------------------------------------------------------------------------------------------------
## Reverting commits

> **_a good tip is always use --help or -h after the command to see a sum up version of the docs about the command_**

* git reset
  * git reset HEAD~&lt;n&gt; &rarr; back to the commit nth behind HEAD;
  * git reset --soft &rarr; undo the last commit, work like git add, but move the file from the repo to the staging area;
  * git reset --hard &rarr; will delete the files, as like the commit was never created;
  * git reset --mixed &rarr; is the standard behavior and move the file to the working area;
  * in all the command you can specify the path and the standard (no specification) behavior is with HEAD~1;
* git revert HEAD~&lt;n&gt; &rarr; create a revert commit and will work like a commit but as backward and remove the pointed commit;

<!------------------------------------------------------------------------------------------------------------------------------------------------------------------->

----------------------------------------------------------------------------------------------------------------------------------------------------------------------
## Making Commits

* Atomic commits are set of rules to avoid short and badly made commits. An atomic commits is a unity and concise commit, so instead of sparse and short commits you can make a only commit which bring context to all changes made.
  * Structure: Subject, Body and Footer;
    * Subject, lean and understanding with maximum of 50 characters in an imperative form, so is possible to know what changed in just one line;
    * Body, more details about the commit, try to break the line with 75 characters, use markdown, explain everything you will modifie, recognize your audience so you can keep up to what matter;
    * Footer, optionally, refer to related subjects.
      * in the footer you can e. g. refer a issue just with '#&lt;issue_number&gt;', and close the issue within the commit using 'Closes #&lt;issue_number&gt;'.
  * It's a more generic way to do commits.
* Semantic Versioning
  * Semantic Versioning is a model how to version a program with num1.num2.num3.
  * num1 is the major version, when the compatibility is broken between versions.
  * num2 is the minor version, when add a functionality but doesn't break compatibilitty.
  * nume3 is the patch version, when correct minor problems and bugs.
  * [Read more about semantic versioning here!](https://semver.org)
* Semantic Commits
  * Is a convection whith joint with semantic versioning, so it's possible to create a more detailed history of commits and so you can keep track of certain features.
    * the commit initiate with the type of commit and follow the version number, e. g. committed a fix type commit so the patch number increase, or commit a feat type and increase the minor number, etc.
  * [Read more about semantic commits here!](https://conventionalcommits.org)

<!------------------------------------------------------------------------------------------------------------------------------------------------------------------->

----------------------------------------------------------------------------------------------------------------------------------------------------------------------
## Forks, Pull Requests, Permissions, Issues and Aliases

* When you are not the owner of a repo you can fork the repo from the owner profile to your profile, so you can contribute to the repo.
* So when you want to send your changes to the original repo, you need to do a Pull Request.
* in settings &rarr; manage access is possible to add colaborators, so other people can commit and clone the repo without being the owner of the repo.
* Organizations and Teams, Companies can create an organization inside of github so the companie be in charge of keep the repo and create different teams with differents permissions, so the colaborators of the companie can work in a more organized way and having only acess to what they need.
* [If you speak portuguese this is a cool repository to you do your first Pull Request](https://github.com/aprenda-git/pull-request)
* As the repo earn colaborators and visibility is good to have a template for issues so for who watch the repo is more easy to keep track of the issues. The same way is possible to do templates to Pull Request so when reviewing code is possible to skip some steps.
* git config --global alias.&lt;your_alais&gt; &lt;git_command&gt;
  * e. g. git config --global alias.s status

<!------------------------------------------------------------------------------------------------------------------------------------------------------------------->

----------------------------------------------------------------------------------------------------------------------------------------------------------------------