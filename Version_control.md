One golden rule: `master` should never break (compiles, tests pass, lints)

## Feature branch
Whenever you have to work on a feature, you should create a branch from the sprint goal branch following the pattern `YYYY_sprintnumber-feature_name`. Once the feature has been implemented, a pull request should be submitted (via GitHub) to merge into the goal branch. Please make sure that the code is adequately tested, the tests pass and the code style (lint) is respected. And don't forget, commit often, push at the end of the day!

# Pull requests & code reviews
Code reviews exist to ensure code quality, but also to disseminate knowledge amongst developers.

## Code review checklist:
1. Make sure the formatting is correct and adheres to style rules
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
