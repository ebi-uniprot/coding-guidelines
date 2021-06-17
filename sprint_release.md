# Sprint release procedure for [uniprot-website](https://github.com/ebi-uniprot/uniprot-website)
On the main branch perform the following:
1. [Update and release Franklin](franklin_release.md)
2. Update dependencies ([see below](#upgrade-uniprots-package-dependencies) (including the just updated Franklin)). If an update has several breaking changes and requires too much effort, create a Jira instead and update the [table below](#list-of-currently-not-updated-dependencies)
3. Update the coverage ([see below](#coverage-bump))
4. Push the updated `main` to remote: `git push origin main`
5. Tag a release, adding the list of implemented features and bug fixes (compiled in sprint review doc) ([see below](#tag-a-new-release))
6. Tell everyone it's ready 🎉

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
| Name                | Version           | Reason                                        | Priority    |
| ------------------- | ----------------- | --------------------------------------------- | ----------- |
| d3                  | 5.16.0  ❯  6.5.0  | Breaking changes imcompatible with Nightingale| Low         |
| @types/d3           | 5.16.3  ❯  6.3.0  | Breaking changes imcompatible with Nightingale| Low         |
| history             | 4.10.1  ❯  5.0.0  | Needs proper testing, coordinate with franklin| Medium      |
| protvista-variation-adapter | 3.1.2   ❯  3.2.1  | Type issues (see [jira](https://www.ebi.ac.uk/panda/jira/browse/TRM-25822) for details)                      | Low         |
| lit-html            | 1.3.0   ❯  1.4.1  | Needs to match the protvista-datatable version| Low         |
| sass                | 1.32.13 ❯  1.34.0 | Incompatible with current version of foundation| Low         |
| sass-loader         | 10.1.1  ❯  11.1.1 | Incompatible with current version of foundation| Low         |

### Coverage bump
Bump the test coverage as to define a new reference for the new sprint:
```
yarn coverage-bump
```

### Tag a new release
Tag the release with the relevant release notes https://github.com/ebi-uniprot/uniprot-website/releases
- Draft a new release
- Put the sprint goal as release title
- Write the list of new features/bug fixes (already compiled in sprint review document)
