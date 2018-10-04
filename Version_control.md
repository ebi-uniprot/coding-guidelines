One golden rule: `master` should never break (compiles, tests pass, lints)

# Feature branch
Whenever you have to work on a feature, you should create a branch (if possible including the Jira issue in the branch name). Once the feature has been implemented, a pull request should be submitted (via GitHub). Please make sure that the code is adequately tested, the tests pass and the code style (lint) is respected. And don't forget, commit often, push at the end of the day!

# Pull requests & code reviews
Code reviews are there to ensure code quality, but also to disseminate knowledge amongst developers.

## Code review checklist:
1. Make sure the formatting is correct and adheres to style rules (`eslint`)
2. Make sure tests past and the new features are tested adequately
3. A review should be less than 600 lines - if the developer realises during implementation that the feature is bigger than expected, discuss with other devs and break down in subtasks
4. Names should be readable, descriptive and make it easy to understand what a method / variable / class is doing (so no need for documentation)
5. Change reviewers often if possible
6. Code reviews should take a couple of hours at most - if it takes more than 20 min to understand, they should be paired reviews
7. Reviews should be done in a timely fashion (max 3 working days after submission)
8. If it keeps going back and forth, involve someone else
9. Make sure your review is complete before submitting

## Accepting the code review
Once the code review is accepted, all the commits should be squashed and it should go into `master`. There's a nifty GitHub button which allows you to do that (ace!).

# Release
# GitHub release 
https://blog.github.com/2013-07-02-release-your-software/

# Hotfix
A branch should be created, then when the fix is ready that same branch should be tagged with a minor release `x.x.1`. Don't forget to merge your branch into master. **TBD: What about PRs, and squash merge?**

# gh-pages
Github pages is a great way to showcase an application. For this we use `git worktree`.

## Initial setup
```
rm -rf build
git worktree add build gh-pages
yarn build
cd build
git add --all
git commit -m 'initial gh-pages commit'
git push origin gh-pages
cd ..
```

## To update
```
yarn build
cd build
git add --all
git commit -m 'initial gh-pages commit'
git push origin gh-pages
cd ..
```
