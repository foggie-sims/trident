# Trident

[![CircleCI](https://circleci.com/gh/foggie-sims/trident/tree/main.svg?style=svg)](https://circleci.com/gh/foggie-sims/trident/tree/main)
[![Coverage Status](https://coveralls.io/repos/github/foggie-sims/trident/badge.svg?branch=main)](https://coveralls.io/github/foggie-sims/trident?branch=main)
[![Documentation Status](https://readthedocs.org/projects/foggie-trident/badge/?version=latest)](https://foggie-trident.readthedocs.io/en/latest/?badge=latest)

This is the official trident version of the FOGGIE project.

Trident is a Python package for making synthetic spectra from
astrophysical simulations. It can also generate fields representing
ion abundances from data tables assuming ionization equilibrium.

## Installation

See the Installation section of the
[documentation](http://foggie-trident.readthedocs.org) for detailed
instructions. This assumes that you already have some version of conda
installed. FOGGIE-trident must be install from source.

```
git clone git@github.com:foggie-sims/trident YOUR_CODE_DIR/trident
cd YOUR_CODE_DIR/trident
pip install -e .
```

The above will not work if you do not have your ssh key on github
or do not have write access to the FOGGIE-trident repo. If you
don't think you'll need to do any development yourself, you can do
this command to clone instead.
```
git clone https://github.com/foggie-sims/trident
```

### Updating trident (or other source repositories)
To pull in the latest changes to trident (or yt, yt_astro_analysis),
do the following:
```
cd YOUR_CODE_DIR/trident
git pull origin main
```

And you're done! Take the rest of the day off.

## Configuring Trident

Oh right, you want to use trident! Coming soon.

## Development

Trident development happens through pull requests. In a nutshell, you
create your own branch, make changes, push them to the repo, and issue
a pull request.

### 1. Make a new branch
You can name your branch whatever you want.
```
git checkout -b NEW_BRANCH_NAME
```

### 2. Make changes, commit them.
Make whatever changes you want. Assuming you want to commit every
altered file, do the following:
```
git commit -am 'A bunch of changes.'
```
Repeat as necessary.

### 3. Push to the main repository
```
git push origin NEW_BRANCH_NAME
```
If this is the first time pushing the new branch, you will see a URL
for opening a pull request. If not, go to the
[main repo](https://github.com/foggie-sims/trident) in a web browser
and follow the instructions there to issue your pull request.

After your pull request has been issued, steps 2 and 3 can be repeated
to add new changes until your pull request has been merged.

### Don't do what Donnie Don't does

The main branch of trident is called `main`. Try not to ever push
changes on the main branch directly to the main repository (i.e.,
`git push origin main`). This will add your changes for
everyone. However, if done accidentally, don't worry, it can be
undone.

## Resources

 * Documentation: http://foggie-trident.readthedocs.org
