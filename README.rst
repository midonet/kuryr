===============================
kuryr
===============================

.. image:: https://raw.githubusercontent.com/openstack/kuryr/master/doc/images/kuryr_logo.png
    :alt: Kuryr
    :width: 67
    :height: 112
    :align: center


Docker for OpenStack Neutron

Kuryr is a Docker network plugin that uses Neutron to provide networking
services to Docker containers. It provides containerised images for the
common Neutron plugins.


* Free software: Apache license
* Documentation: http://docs.openstack.org/developer/kuryr
* Source: http://git.openstack.org/cgit/openstack/kuryr
* Bugs: http://bugs.launchpad.net/kuryr

Features
--------

* TODO


Prerequisites
-------------

::

    $ sudo pip install -r requirements.txt

Running Kuryr
-------------

Currently, Kuryr utilizes a bash script to start the service.

::

    $ sudo ./scripts/run_kuryr.sh

After the booting, please restart your Docker service, e.g.,

::
    $ sudo service docker restart

The bash script creates the following files if they are missing.

* ``/usr/lib/docker/plugins/kuryr/kuryr.json``: Json spec file for libnetwork;
* ``/etc/kuryr/kuryr.conf``: Configuration file for Kuryr.

Note the root privilege is required for creating and deleting the veth pairs
with `pyroute2 <http://docs.pyroute2.org/>`_ to run.

Testing Kuryr
-------------

::

    $ tox

You can also run specific test cases using the ``-e`` flag, e.g., to only run
the *fullstack* test case.

::

    $ tox -e fullstack

Generating Documentation
------------------------


We use `Sphinx <https://pypi.python.org/pypi/Sphinx>`_ to maintain the
documentation. You can install Sphinx using pip.

::

    $ pip install -U Sphinx

The source code of the documentation are under *doc*, you can generate the
html files using the following command. If the generation succeeds,a
*build/html* dir will be created under *doc*.

::

    $ cd doc
    $ make html

Now you can serve the documentation at http://localhost:8080 as a simple
website.

::

    $ cd build/html
    $ python -m SimpleHTTPServer 8080
