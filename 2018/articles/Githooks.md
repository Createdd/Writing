# Improve development workflow with your team with Githooks

[<img src="https://images.unsplash.com/photo-1536743654498-52cbbf194df5?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=12a2850349440cae58fd38718400d379&auto=format&fit=crop&w=1329&q=80">](
https://unsplash.com/photos/erQu7dP0jCE)
Photo by rawpixel on Unsplash - https://unsplash.com/photos/erQu7dP0jCE

Every product that is developed by more than 1 programmer needs to have some guidelines to harmonize the workflow.

Standardized software development workflow between programmers allows for example:
- faster engineering since each developer can rely on a habitual activity
- less errors since the workflow itself shall be structured in a way to avoid some mistakes
- easy integration of new members
- improved log of history

In (web)development one very easy to use feature are "[Githooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks)". (If you are using Git for version control).

In this article I want to show how easy it actually  is to set up a few workflow guidelines with githooks to allow your team to be on one page when developing software.


## Table of Contents

##

## Why Githooks?

Githooks are, as the word suggests, a hook for [Git](https://git-scm.com/) commands. Intuitivly this makes sense, because with Git you are essentally managing the workflow of a piece of software. Every Branch is a part of the whole piece. Every Commit is a building block of a Branch.

So in order to standardize quality in software development, one must standardize actions in the building process of the product.

There are many Git commands that can be hooked for setting standards. Remember, there are quite a few:
- applypatch-msg
- pre-applypatch
- post-applypatch
- pre-commit
- prepare-commit-msg
- commit-msg
- post-commit
- pre-rebase
- post-checkout
- post-merge
- pre-receive
- pre-push
- update
- post-update
- pre-auto-gc
- post-rewrite

To establish an improved workflow you don't have to use all of them. Focus on the few important. In my experience so far, those are:
- commit-msg/pre-commit
- post-checkout
- pre-push

Let me explain why.

## GitFlow and Checkout, Commit, Push

Using Git as version control system allows to set a workflow. I do this using the [GitFlow method](https://datasift.github.io/gitflow/IntroducingGitFlow.html).

![gitflow image](https://datasift.github.io/gitflow/GitFlowHotfixBranch.png)

It is basically to develop a piece of software where each feature is represented by a branch.

In the following examples I will always check naming with Regex tests or execute another script.

### Post-checkout

The increased importance of a branch allows for the first hook on "post-checkout". It is triggered after a new branch is created with Git.

Often a naming convention is applied to make branches comparable and understand their use for the whole product.

You can create a simply shell script like this to ensure naming:

https://gist.github.com/Createdd/93a8582bde38112ede09e08beb889970


### Commit-msg

In web development there are multiple libraries that help with setting up a hook for commiting. Often they are not necessary, as simple scripts can be written by yourself as well.

See validation of a git message for example:

https://gist.github.com/Createdd/437ac97100c4c0ee0a6b2e077c65ca25


### Pre-push

Pushing is the process of "sharing" you branch with the team. It is often the last step before opening a pull-request for a merge with the main branch.

This a good time to check other guidelines like "linting" of the code, or if all tests are passing.

An example  for executing another script could be: https://gist.github.com/Createdd/7f6e620d9204f18e8e3c6ec7e9eb09dc

## "Enforce" the hooks

Another step is how to actually enforce those hooks.

In JavaScript and NPM/Yarn package mangers there is a "postinstall" script already built in. It allows for the execution of a script after the installing process. But what exactely should be executed?

Create an own install script! Like:

https://gist.github.com/Createdd/3ccacf58185fa269e26680ba96207f09

## Fix one common problem

One issue that kept me guessing for a while was that Git hooks are NOT executable by default. This means that they need to be made executable with

`chmod +x <pathToHook>`

See StackOverflow discussion [here](https://stackoverflow.com/questions/8598639/why-is-my-git-pre-commit-hook-not-executable-by-default).

---

I hope that this will help some of you to align the workflow of your development team and makes the life of everyone involved much easier :)


---

Thanks for reading my article! Feel free to leave any feedback!

---

Daniel is a LL.M. student in business law, working as a software engineer and organizer of tech related events in Vienna.
His current personal learning efforts focus on machine learning.

Connect on:
- [LinkedIn](https://www.linkedin.com/in/createdd)
- [Github](https://github.com/Createdd)
- [Medium](https://medium.com/@ddcreationstudi)
- [Twitter](https://twitter.com/_createdd)
- [Steemit](https://steemit.com/@createdd)
- [Hashnode](https://hashnode.com/@DDCreationStudio)

<!-- Written by Daniel Deutsch (deudan1010@gmail.com) -->