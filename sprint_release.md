# Sprint release procedure for [uniprot-website](https://github.com/ebi-uniprot/uniprot-website)
On the main branch perform the following:
1. [Update and release Franklin](franklin_release.md)
2. Update dependencies ([see below](#upgrade-uniprots-package-dependencies) (including the just updated Franklin)). If an update has several breaking changes and requires too much effort, create a Jira instead and update the [table below](#list-of-currently-not-updated-dependencies)
3. Update the coverage ([see below](#coverage-bump))
4. Push the updated `main` to remote: `git push origin main`
5. Tag a release, adding the list of implemented features and bug fixes (compiled in sprint review doc) ([see below](#tag-a-new-release))
6. Tell everyone it's ready 🎉
7. Delete stale branches upon confirmation from the team 🧹

## Details

### Upgrade UniProt's package dependencies
Note: do [the same process on Franklin](https://github.com/ebi-uniprot/coding-guidelines/blob/main/franklin_release.md#upgrade-franklins-package-dependencies) first as UniProt depends on Franklin. It will allow us to have the same up-to-date version of common dependencies at the same time.

It is assumed you're on UniProt's main and have all branches for that sprint merged in (if ready). Select all compatible upgrades and test:
```
yarn upgrade-interactive --latest
<select compatible upgrades>
yarn test
```
Now upgrade one-by-one the packages with breaking upgrades:
```
yarn upgrade-interactive --latest
<select an upgrade>
yarn test
```

### List of currently not updated dependencies
| Name                          | Version           | Reason                                        | Priority    |
| ----------------------------- | ----------------- | --------------------------------------------- | ----------- |
| d3                            | 5.16.0  ❯  7.2.1  | Breaking changes imcompatible with Nightingale| Low         |
| @types/d3                     | 5.16.3  ❯  7.1.0  | Breaking changes imcompatible with Nightingale| Low         |
| history                       | 4.10.1  ❯  5.1.0  | Needs proper testing, coordinate with franklin| Medium      |
| react-router-dom              | 5.0.4   ❯  6.0.2  | Link update with history, needs testing       | Medium      |
| @svgr/webpack                 | 5.5.0   ❯  6.1.1  | Update alongside SVG optimisation in webpack  | Low         |
| @storybook/*                  | 6.3.*   ❯  6.4.9  | Issue with router, linked to react-router-dom?| Low         |
| react-beautiful-dnd-test-utils| 3.2.1   ❯  4.1.0  | API change for makeDnd()                      | Low         |
| axios                         | 0.22.0  ❯  0.24.0 | Type changes, might be easy but needs checking| Low         |


### Coverage bump
Bump the test coverage as to define a new reference for the new sprint:
```
yarn coverage-bump
```

### Tag a new release
Tag the release with the relevant release notes https://github.com/ebi-uniprot/uniprot-website/releases
- To tag on your local machine: `git tag -a v<version> -m "v<version>"` eg `git tag -a v0.18-alpha -m "v0.18-alpha"`
- To push (annotated) tags: `git push --follow-tags origin main`
- Draft a new release
- Put the sprint goal as release title
- Write the list of new features/bug fixes (already compiled in sprint review document)

### Delete stale branches
Check in github if there any stale branches within both uniprot and franklin and if so, inform the team via slack that you will delete them unless anybody has objections. If all OK, delete the branches.
