.. _installation:

Installation
============

FOGGIE-Trident must be installed installed from source, but all other
dependencies can be installed using their stable, released versions.
Occasionally, bugs in ``yt`` or ``yt_astro_analysis`` may get fixed
and there is a delay before new stable versions are released. It is
then necessary to install those packages from source. See
:ref:`install-dev-versions` for information on that.

Install Conda
-------------

Conda is a package manager providing a clean, stand-alone installation of
python that is self-contained in its installation directory.  yt & trident
require a modern installation of python to work.  conda provides that
installation.

You can see if conda is already installed by running:

.. code-block:: bash

   $ conda -h

If conda is installed, move to the next step.  Otherwise install Mini-conda.

Use the appropriate conda install script for your architecture.  We recommend
getting the latest version of conda for Python3 for your architecture here:
https://repo.continuum.io/miniconda/

For modern macs:

.. code-block:: bash

   $ curl -O https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh
   $ bash Miniconda3-latest-MacOSX-x86_64.sh

For modern linux machines:

.. code-block:: bash

   $ wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
   $ bash Miniconda3-latest-Linux-x86_64.sh

At the end of the installation step, allow conda to add its installation
directory to the $PATH.

Clone FOGGIE-Trident Repository and Install
-------------------------------------------

Clone the FOGGIE-Trident repository and install from it by doing the following:

.. code-block:: bash

   $ git clone git@github.com:foggie-sims/trident trident
   $ cd trident
   $ pip install -e .

This will install all hard dependencies as well. You will need to keep this
directory.

Install Additional Dependencies
-------------------------------

You may also want to install ``mpi4py`` to allow trident to run in parallel. This
is not required, but can be done with either ``conda`` or ``pip``.

.. code-block:: bash

   $ conda install mpi4py

.. code-block:: bash

   $ pip install mpi4py

Updating Your FOGGIE-Trident Installation
-----------------------------------------

To pull in the latest changes, return to your trident directory and use git to
update your repository.

.. code-block:: bash

   $ cd trident
   $ git pull origin main

.. _verify-installation:

Get Ionization Table and Verify Installation
--------------------------------------------

In order to calculate the ionization fractions for various ions from
density, temperature, metallicity fields, you will need an ionization table
datafile and a configuration file.  Because this datafile can be large, it is
not packaged with the main source code.  The first time you try to do anything
that requires it, Trident will attempt to automatically set this all up for
you with a series of interactive prompts.  **This step requires an internet
connection the first time you run it.**

In addition, Trident provides a simple test function to verify that your
install is functioning correctly.  This function not only tries to set up
your configuration and download your ion table file, but it will
create a simple one-zone dataset, generate a ray through it, and
create a spectrum from that ray.  This should execute very quickly,
and if it succeeds it demonstrates that your installation has been totally
successful:

.. code-block:: bash

   $ python
   >>> import trident
   >>> trident.verify()
   ...Series of Interactive Prompts...

If you cannot directly access the internet on this computer, or you lack write
access to your ``$HOME`` directory, or this step fails for any reason, please
follow our documentation on :ref:`manual-config`.

Science!
--------

Congratulations, you're now ready to use Trident!  Please refer to the
documentation for how to use it with your data or with one of our sample
datasets.  A good place to start is the
:ref:`annotated example <annotated-example>`, and the `example scripts found
in the source code
<https://github.com/foggie-sims/trident/tree/main/examples>`_.

.. _install-dev-versions:

Installing Development Versions of yt and yt_astro_analysis
-----------------------------------------------------------

Installing ``yt`` or ``yt_astro_analysis`` from source is similar to
installing trident. Clone the repo and use ``pip`` to install.

yt
^^

.. code-block:: bash

    $ git clone https://github.com/yt-project/yt yt
    $ cd yt
    $ pip install -e .

yt_astro_analysis
^^^^^^^^^^^^^^^^^

.. code-block:: bash

    $ git clone https://github.com/yt-project/yt_astro_analysis yt_astro_analysis
    $ cd yt_astro_analysis
    $ pip install -e .

Updating yt and yt_astro_analysis Installations
-----------------------------------------------

To update either ``yt`` or ``yt_astro_analysis`` do:

.. code-block:: bash

   $ cd <repo-directory>
   $ git pull origin main
   $ pip install -e .

Note, the final step of ``pip install -e .`` is necessary whenever cython
files have been modified, as these require rebuilding.

.. _manual-config:

Manually Installing your Ionization Table
-----------------------------------------

If for some reason you are unable to install the config file and ionization
table data automatically, you must set it up manually.  When Trident runs,
it looks for a configuration file called ``config.tri`` in the
``$HOME/.trident`` directory or alternatively in the current working
directory (for users lacking write access to their ``$HOME`` directories).
This configuration file is simple in that it tells Trident a few things about
your install including the location and filename of your desired ionization
table.  Manually create a text file called ``config.tri`` with contents
following the form::

    [Trident]
    ion_table_dir = ~/.trident
    ion_table_file = hm2012_hr.h5

To manually obtain an ion table datafile, download and gunzip one from:
http://trident-project.org/data/ion_table .  While the ``config.tri`` file
needs to exist in your ``$HOME/.trident`` directory or in the working directory
when you import trident, the ion_table datafile can exist anywhere on the
file system.  Just assure that the config file points to the proper location
and filename of the ion table datafile.

Now, to confirm everything is working properly, verify your installation
following :ref:`verify-installation`.  If this fails or you have additional
problems, please contact our mailing list.

.. _uninstallation:

Uninstallation or Switching Code Versions
-----------------------------------------

If you installed via pip, do:

.. code-block:: bash

   $ pip uninstall trident

To fully remove the code from your system, remember to remove any ion table
datafiles you may have downloaded in your ``$HOME/.trident`` directory,
and follow the instructions for how to `uninstall yt
<http://yt-project.org/docs/dev/installing.html>`_.
