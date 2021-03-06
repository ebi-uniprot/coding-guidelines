# Sprint release procedure for [uniprot-website](https://github.com/ebi-uniprot/uniprot-website)
1. Merge current sprint goal branch into master
2. Tag a release on master, adding list of implemented features and bug fixes (compiled in sprint review doc)
3. [Update and release Franklin](franklin_release.md)
3. Create a new sprint goal branch, following the `YYYY_sprintnumber` pattern
4. Update dependencies, including Franklin - if breaking change and requires too much effort, create a Jira instead
5. Update the coverage (see below)
6. Push the new sprint branch to remote, and tell everyone it's ready 🎉


## Details
### Merge goal branch into master (if agreed by the PO)

Check to ensure all PRs from this sprint are merged into the sprint branch. Then get the latest sprint branch
`git pull origin <sprint branch>`

Ensure tests are passing on the sprint branch
```
rm -rf node_modules; yarn; yarn test
```

Checkout master and pull the latest
```
git checkout master
git pull origin master
```

Merge in the sprint branch
```
git merge <sprint branch>
```

Resolve any merge conflicts. Then reinstall `node_modules` and test
```
rm -rf node_modules; yarn; yarn test
```

For a sanity check access the following pages with the console visible:
  -   [http://localhost:8080/](http://localhost:8080/)
  -   [http://localhost:8080/uniprotkb/P05067](http://localhost:8080/uniprotkb/P05067)
  -   [http://localhost:8080/uniprotkb/P05067/feature-viewer](http://localhost:8080/uniprotkb/P05067/feature-viewer)
  -   [http://localhost:8080/uniprotkb/P05067/publications](http://localhost:8080/uniprotkb/P05067/publications)
  -   [http://localhost:8080/uniprotkb/P05067/external-links](http://localhost:8080/uniprotkb/P05067/external-links)
  -   [http://localhost:8080/uniprotkb?query=a4](http://localhost:8080/uniprotkb?query=a4)
  -   [http://localhost:8080/tool-dashboard](http://localhost:8080/tool-dashboard)

If all looks OK then push to master
```
git push origin master
```

### Upgrade UniProt's package dependencies and release the new UniProt sprint branch
Note: do [the same process on Franklin](https://github.com/ebi-uniprot/coding-guidelines/blob/master/franklin_release.md#upgrade-franklins-package-dependencies) first as UniProt depends on Franklin. It will allow to have the same up-to-date version of common dependencies at the same time.

It is assumed you're on UniProt's master and have the current sprint merged in. To create the new branch where the sprint branch name format is YYYY_MM 
```
git checkout -b <new sprint branch>
```

Select all compatible upgrades and test
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
| html-loader         | 1.3.2   ❯  2.1.1  | Relies on webpack update                      | Low         |
| html-webpack-plugin | 4.5.1   ❯  5.2.0  | Relies on webpack update                      | Low         |
| sass-loader         | 10.1.1  ❯  11.0.1 | Incompatible with current Webpack version     | Low         |
| webpack             | 4.44.2  ❯  5.24.2 | BIG change                                    | Medium      |
| webpack-cli         | 3.3.12  ❯  4.5.0  | BIG change                                    | Medium      |

Bump the test coverage as to define a new reference for the new sprint:
```
yarn coverage-bump
```

Check if anything has gone into master recently and if so, merge it in and test again
```
git fetch
git merge master
rm -rf node_modules; yarn; yarn test
```

Push to the remote
```
git push origin <new sprint branch>
```

Tag the release with the relevant release notes https://github.com/ebi-uniprot/uniprot-website/releases
- Draft a new release
- Put the sprint goal as release title
- Write the list of new features/bug fixes (already compiled in sprint review document)
