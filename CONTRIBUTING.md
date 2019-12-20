GITHUB Quick Documentation for Contributors
===========================================

This section guides you in setting up on your local workstation the
(forked) git repositories needed to contribute to the |odh| project,
along with some troubleshooting concerning pull requests and merge
conflicts. For more detailed help, please refer to the online Github
help, at https://help.github.com/.

Prerequisites
-------------

In the following documentation some example names are used. Please
replace them with your names:

- You need an account on Github to be able to fork projects and contribute to the IOTA Meetup Packages project.
- Replace `your-username` with your username on GitHub.
- Replace `feature-branch` with the branch name you will develop in your forked version.


Project Checkout
----------------

Before starting the development, you need to fork the original
(upstream) repository.

1. Navigate to the repository on GitHub, e.g.,
   https://github.com/iota-community/iota-meetup-packages

2. Create a fork of the repository by clicking on the **Fork** button. If you are not logged in, you will be asked for a github username and password

3. Navigate to your forked repository on GitHub, e.g.,
   https://github.com/your-username/iota-meetup-packages

4. Check out the forked repository on your local machine, using the
   link that appears in your repository:

       git clone git@github.com:your-username/iota-meetup-packages.git


Create a pull request
---------------------

In order to let your contribution be accepted in the |odh| code base,
you need to follow the following steps.

1. Checkout the **development** branch:

        git checkout development

2. Create a new branch from the **development** branch locally on your machine:

       git checkout -b feature-branch

3. Make some changes to the code and commit them:

       git add -A
       git commit -m "Some commit message"

4. Push the new branch to GitHub:

       git push --set-upstream origin feature-branch

5. Navigate to your feature branch on Github
   (https://github.com/your-username/iota-meetup-packages/pull/new/feature-branch)
   to create a new pull request

   You can write some description as well, to describe your changes.

6. Commit and push any changes of the pull request to this new branch

7. For every commit the continuous integration pipeline will execute the tests and display the results in the pull request

Syncing a Fork
--------------

Your forked repository does not receive the updates of the original
repository automatically. To sync for example the
**development** branch of the two repositories and to keep the
forked repository up-to-date with all the latest changes of the
**development** branch from the original repository, the
following steps have to be performed.

Before you can sync your fork with the original repository (an
upstream repository), you must configure a remote that points to the
upstream repository in Git. A more detailed description for the
following steps can be found in the online Github help
https://help.github.com/articles/configuring-a-remote-for-a-fork/.

1. List the current configured remote repository for your fork

       git remote -v


2. Specify a new remote upstream repository that will be synced with the fork

       git remote add upstream https://github.com/noi-techpark/bdp-core.git


3. Verify the new upstream repository you've specified for your fork

       git remote -v

You need sync a fork of a repository to keep it up-to-date with the
original repository (upstream repository). A more detailed description
for the following steps can be found in the online Github help https://help.github.com/articles/syncing-a-fork/.

1. Fetch the branches and their respective commits from the upstream
   repository. Commits to **development** will be stored in a local branch, **upstream/development**

       git fetch upstream

2. Check out your fork's local **development** branch

       git checkout development

3. Merge the changes from **upstream/development** into your local **development** branch. This brings your fork's development branch into sync with the upstream repository, without losing your local changes

       git merge upstream/development

Resolving Merge Conflicts
-------------------------

When creating and working on a pull request, it could happen that the
destination branch of the original repository will change. These
changes could result in merge conflicts when pulling your code.

To resolve merge conflicts, the following steps must be performed.

1.Sync your forked repository and make sure
   your local destination (development) branch is up to date with the original (upstream) repository branch.

2. Check out your feature branch

       git checkout feature-branch


3. Merge the changes of the development branch to the feature branch

       git merge development


   The command will output the files with merge conflicts.

4. Go the the listed files of the previous output and resolve all merge conflicts. The conflicts in the files begin with `<<<<<<<` and end with `>>>>>>>`. The `=======` separates the two versions.

   You can resolve a conflict by simply deleting one of the two versions of the code **and** the inserted helper lines beginning with `<<<<<<<`, `=======`, and `>>>>>>>`.

   If none of the two versions is completely correct, then you can delete the conflict entirely and write your own code to solve the
   conflict.

5. Add all resolved files to the index, commit the changes and push the changes to the server.

       git add -A
       git commit
       git push


6. After resolving the merge conflicts, the pull request can be accepted.

A more detailed description can be found in the online Github help: https://help.github.com/articles/resolving-a-merge-conflict-using-the-command-line/.

Attribution
-------------------------

This Code of Conduct is adapted from the Open Data Hub Documentation available at https://github.com/noi-techpark/odh-docs/blob/master/source/contributors.rst © Copyright 2018-2019, The ODH Team
