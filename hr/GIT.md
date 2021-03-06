# Git Flow Usage Examples

This document provides examples of common git workflows to show new developers how use the [git flow](https://jeffkreeftmeijer.com/git-flow/) branch conventions.

## Working on a feature

If there isn't one already, create a new branch for the feature, based on `develop`.

```
git checkout develop
git checkout -b fireball-spell
```

Do your work, commit, update, push.

```
git commit -a -m "Added the Fireball ability to wizards, Trello ticket #51"
git pull origni develop
git push origin fireball-spell
```

Submit a pull request from `fireball-spell` targetting `develop`. Another developer on the project should review and comment on your changes. When everyone agrees, anyone can merge the changes. The `fireball-spell` branch is then deleted after being merged.

## Small non-critical patch (update README.md)

A small documentation changes and tests don't always need a feature branch. It's up to your judgement to decide if it's worth someone else reviewing small changes. If not, commit right to develop.

```
git checkout develop
```

make changes to README.md

```
git commit -a -m "Document deployment steps for trolls."
git pull origin develop
git push origin develop
```

## Hotfix

If production is broken, you want to fastrack a fix into master. Only for emergencies.


```
git checkout master
```

make your bugfix (and no other changes here.)

```
git commit -a -m "Hotfix broken CSS on elven smartphone resolutions."
git pull origin master
git push origin master
```

Then deploy the changes (different for every project currently).

