# Trident

[![CircleCI](https://circleci.com/gh/foggie-sims/trident/tree/master.svg?style=svg)](https://circleci.com/gh/foggie-sims/trident/tree/master)
[![Coverage Status](https://coveralls.io/repos/github/foggie-sims/trident/badge.svg?branch=master)](https://coveralls.io/github/foggie-sims/trident?branch=master)
[![Documentation Status](https://readthedocs.org/projects/foggie-trident/badge/?version=latest)](https://foggie-trident.readthedocs.io/en/latest/?badge=latest)

Trident is a Python package for creating synthetic absorption-line spectra
from astrophysical hydrodynamics simulations.  It utilizes the yt package
to read in simulation datasets and extends it to provide realistic
synthetic observations appropriate for studies of the interstellar,
circumgalactic, and intergalactic media.

## Installation (after yt installed)

Trident can be installed with pip:

```
pip install trident
```

To get the development version, clone this repository and install like this:

```
git clone https://github.com/foggie-sims/trident
cd trident
pip install -e .
```

## Resources

 * Trident documentation: http://foggie-trident.readthedocs.org
