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

## Checkout, Commit, Push



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