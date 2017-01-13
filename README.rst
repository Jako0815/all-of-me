linuxmuster.net documentation
#############################

.. image:: https://travis-ci.org/linuxmuster-docs/all-of-me.svg?branch=v7
    :target: https://travis-ci.org/linuxmuster-docs/all-of-me

.. image:: http://readthedocs.org/projects/linuxmuster/badge/?version=v7
    :target: http://docs.linuxmuster.net/de/v7/?badge=v7
    :alt: Documentation Status

::

  All of me, why take not all of me.
                   -- Seymour Simons

Die gesamte Dokumentation zu linuxmuster.net v7

The full documentation of linuxmuster.net v7

Installation
++++++++++++
Clone the repository "all-of-me" using git

.. code:: bash

   ~$ git clone https://github.com/linuxmuster-docs/all-of-me.git  # if you have no ssh-key within github
   ~$ git clone git@github.com:linuxmuster-docs/all-of-me.git # if you have a ssh-key within github

Install sphinx, e.g. under Ubuntu 16.04, do

.. code:: bash

   ~$  sudo aptitude -R install git python3-sphinx texlive texlive-latex-extra texlive-lang-german

Make a local copy of your documentation using

.. code:: bash

   ~$ cd all-of-me
   ~/all-of-me$ make clean
   ~/all-of-me$ make html

Later, if you work again on the repository, update it with

.. code:: bash

   ~/all-of-me$ git pull



Contribute to the documentation
+++++++++++++++++++++++++++++++

Fork the repository "all-of-me" within the github-webinterface_

.. _github-webinterface: https://github.com/linuxmuster-docs/all-of-me

* Clone your fork

  .. code:: bash

     ~$ git clone https://github.com/mein-github-konto/all-of-me.git docs
     ~$ cd docs
     ~/docs$ make html

* Make changes in your fork
* Commit your changes to your fork

  .. code:: bash

     ~/docs$ git commit -a -m"bugfix for bug in ticket #314 ..."

* Push your changes to your fork on github

  .. code:: bash

     ~/docs$ git push

* Create a new pull-request on github
* If you are done and the pull-request was merged, you can delete your fork and create a new one.

Update your fork
----------------

Instead of deleting and creating a new fork you can bring your own fork up-to-date the following way:

* Any changes you made you have to stash away for a while:

  .. code:: bash

     ~/docs$ git stash

* Add a remote tracking branch:

  .. code:: bash

     ~/docs$ git remote add upstream https://github.com/linuxmuster-docs/all-of-me.git

* Fetch and merge the remote master

  .. code:: bash

     ~/docs$ git fetch upstream
     ~/docs$ git merge upstream/master
  
* (If the merge does not end in an fast-forward result, you better delete and refork.) Push your changes into your fork.

  .. code:: bash
  
     ~/docs$ git push

* Now you can get your stashed away changes:

  .. code:: bash

     ~/docs$ git stash pop


Translation
+++++++++++

We use `Transifex <https://www.transifex.com/linuxmusternet/official-documentation/dashboard/>`__ to translate the documentation. Get started there!

Build documentation in English
++++++++++++++++++++++++++++++

First you have to install ``sphinx-intl`` and the ``transifex-client``.

.. code:: bash

   $ pip install sphinx-intl
   $ pip install transifex-client

Make sure that ``sphinx-intl`` and ``transifex-client`` are in your PATH!

Then run to following commands (inside the document root):

.. code:: bash

   $ make gettext
   $ tx init
   $ sphinx-intl update -p build/locale -l en
   $ sphinx-intl update-txconfig-resources --pot-dir build/locale --transifex-project-name official-documentation
   $ tx pull -l en
   $ make -e SPHINXOPTS="-D language='en'" html

Read the `Internationalization chapter <http://www.sphinx-doc.org/en/stable/intl.html>`__ in the offical sphinx documentation for a more detailed description.


Further reading
+++++++++++++++

See the documentation on linuxmuster.net_.

.. _linuxmuster.net: http://www.linuxmuster.net/wiki/dokumentation:sphinx
