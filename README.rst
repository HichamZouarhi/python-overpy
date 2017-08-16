Python Overpass Wrapper
=======================

A Python Wrapper to access the Overpass API.

Have a look at the `documentation`_ to find additional information.

Features
--------

* Query Overpass API
* Parse JSON and XML response data
* Additional helper functions

same as overpy plus proxy support for python 2 ( urlib2 )

Install
-------

**Requirements:**

Supported Python versions:

* Python 2.7
* Python >= 3.2
* PyPy and PyPy3

**Install:**

.. code-block:: console
    $ git clone https://github.com/HichamZouarhi/python-overpy.git
    $ cd python-overpy
    $ pip install .

Examples
--------

Additional examples can be found in the `documentation`_ and in the *examples* directory.

.. code-block:: python

    import overpy

    api = overpy.Overpass(proxies = {'http': 'your_proxy_ip:your_proxy_port')

    # fetch all ways and nodes
    result = api.query("""
        way(50.746,7.154,50.748,7.157) ["highway"];
        (._;>;);
        out body;
        """)

    for way in result.ways:
        print("Name: %s" % way.tags.get("name", "n/a"))
        print("  Highway: %s" % way.tags.get("highway", "n/a"))
        print("  Nodes:")
        for node in way.nodes:
            print("    Lat: %f, Lon: %f" % (node.lat, node.lon))



License
-------

Published under the MIT (see LICENSE for more information)

.. _`documentation`: http://python-overpy.readthedocs.org/
