.. |br| raw:: html

   <br />

.. _model-common:

Common
==========

.. _model-common-result:

API Result
------------------

.. rst-class:: text-align-justify

**Example**:

.. code-block:: json

    {
        "code": 0,
        "desc": "Ok"
    }

**Definition**

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+---------------------------+----------+-----+-----------------------------------+
| Key                       | Type     | M/O | Description                       |
+===========================+==========+=====+===================================+
| code                      | integer  | M   | Result Code (0:Success)           |
+---------------------------+----------+-----+-----------------------------------+
| error                     | string   | O   | Error                             |
+---------------------------+----------+-----+-----------------------------------+
| desc                      | string   | M   | Description                       |
+---------------------------+----------+-----+-----------------------------------+

   |br|

   .. _model-common-pagination:

Pagination
------------------

.. rst-class:: text-align-justify

**Example**:

.. code-block:: json

    {
         "page": 1,
         "nitem": 10,
         "total": 45
    }

**Definition**

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+---------------------------+----------+-----+-----------------------------------+
| Key                       | Type     | M/O | Description                       |
+===========================+==========+=====+===================================+
| page                      | integer  | M   | Current page number. default is 1 |
+---------------------------+----------+-----+-----------------------------------+
| nitem                     | integer  | M   | Number of items in a page         |
+---------------------------+----------+-----+-----------------------------------+
| total                     | integer  | O   | Total number of items             |
+---------------------------+----------+-----+-----------------------------------+
