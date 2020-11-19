# Franklin release

Franklin releases can happen at anything  point in time.
1. Merge feature branch into master
2. Update dependencies and push after running tests. If breaking change/too much effort, create relevant Jira(s). If in doubt ask for help.
3. Release the module: `yarn release`
4. Tag the release on Github, adding the list of new features/bug fixes

## Details
### Upgrade Franklin's package dependencies

Notes:
* Communicate with the rest of the team any breaking changes while upgrading (to be put in backlog, or solved during new sprint)
* The history package should remain on v4 as react-router v5 is relying on it. Also upgrading D3 to higher than v5 may break Nightingale. This applies to the uniprot-website repository as well.
* Upgrading packages may result in unusual babel or webpack related errors. In some cases deleting the yarn.lock file and regenerating it may help.


Change to Franklin's directory, get the latest commits, and start upgrading
```
git checkout master
git pull origin master
yarn upgrade-interactive --latest
```

Select all package upgrades that are backwards compatible then test:
```
yarn test
```

Now one by one update the breaking upgrades:
```
yarn upgrade-interactive --latest
<select an upgrade>
yarn test
```

Sanity check by viewing some of the components.

### Release Franklin
```
git push
yarn release
```
### Tag the release
Tag the release with the relevant release notes https://github.com/ebi-uniprot/franklin-sites/releases
- Draft a new release
- Leave the release title empty
- Write the list of new features/bug fixes
