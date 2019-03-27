.. |br| raw:: html

   <br />

.. _model-product:

Product
==========

.. _model-product-attribute:

Attribute
------------------

.. rst-class:: text-align-justify

**Example**:

.. code-block:: json

   {
         "attrId": "remark",
         "attrName": "Remark",
         "attrType": "textfield",
         "billType": "ALL",
         "custType": "ALL",
         "stateId": "cs",
         "operationId": "newcn",
         "defValue": "",
         "subDomain": "ALL"
   }

**Definition**

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+---------------------------+-----------+-----+---------------------------------------+
| Key                       | Type      | M/O | Description                           |
+===========================+===========+=====+=======================================+
| attrId                    | string    | M   | Attribute ID |br|                     |
|                           |           |     | Used for JSON key                     |
+---------------------------+-----------+-----+---------------------------------------+
| attrName                  | string    | M   | Attribute Name |br|                   |
|                           |           |     | Used for field name                   |
+---------------------------+-----------+-----+---------------------------------------+
| desc                      | string    | O   | Attribute Description                 |
+---------------------------+-----------+-----+---------------------------------------+
| attrType                  | string    | M   | Attribute Type |br|                   |
|                           |           |     | Used for field attribute              |
|                           |           |     |                                       |
|                           |           |     | +------------+-----------------+      |
|                           |           |     | | Val        | Description     |      |
|                           |           |     | +============+=================+      |
|                           |           |     | | checkbox   | Checkbox        |      |
|                           |           |     | +------------+-----------------+      |
|                           |           |     | | divider    | Divider         |      |
|                           |           |     | +------------+-----------------+      |
|                           |           |     | | dropdown   | Select box      |      |
|                           |           |     | +------------+-----------------+      |
|                           |           |     | | radio      | Radio           |      |
|                           |           |     | +------------+-----------------+      |
|                           |           |     | | textarea   | Textarea        |      |
|                           |           |     | +------------+-----------------+      |
|                           |           |     | | textfield  | Input field     |      |
|                           |           |     | +------------+-----------------+      |
+---------------------------+-----------+-----+---------------------------------------+
| billType                  | string    | M   | Billing Type                          |
|                           |           |     |                                       |
|                           |           |     | +-----+-----------------+             |
|                           |           |     | | Val | Description     |             |
|                           |           |     | +=====+=================+             |
|                           |           |     | | PPD | Prepaid         |             |
|                           |           |     | +-----+-----------------+             |
|                           |           |     | | PST | Postpaid        |             |
|                           |           |     | +-----+-----------------+             |
|                           |           |     | | ALL | Both            |             |
|                           |           |     | +-----+-----------------+             |
+---------------------------+-----------+-----+---------------------------------------+
| custType                  | string    | M   | Customer Type                         |
|                           |           |     |                                       |
|                           |           |     | +-----+-----------------+             |
|                           |           |     | | Val | Description     |             |
|                           |           |     | +=====+=================+             |
|                           |           |     | | PSN | Residential     |             |
|                           |           |     | +-----+-----------------+             |
|                           |           |     | | GRP | Corporate       |             |
|                           |           |     | +-----+-----------------+             |
|                           |           |     | | ALL | Both            |             |
|                           |           |     | +-----+-----------------+             |
+---------------------------+-----------+-----+---------------------------------------+
| stateId                   | string    | M   | State ID for order management         |
+---------------------------+-----------+-----+---------------------------------------+
| operationId               | string    | O   | Operation ID                          |
+---------------------------+-----------+-----+---------------------------------------+
| defValue                  | string    | M   | Default Value |br| |br|               |
|                           |           |     | If the attr_type is radio, checkbox,  |                                     |
|                           |           |     | or dropdown, the value is used as a   |
|                           |           |     | selection list. Each item is          |
|                           |           |     | separated by comma.                   |
|                           |           |     |                                       |
+---------------------------+-----------+-----+---------------------------------------+
| subDomain                 | string    | M   | Service SubDomain                     |
|                           |           |     |                                       |
|                           |           |     | +-----+-----------------+             |
|                           |           |     | | Val | Description     |             |
|                           |           |     | +=====+=================+             |
|                           |           |     | | 100 | Bundle          |             |
|                           |           |     | +-----+-----------------+             |
|                           |           |     | | 301 | Cable TV        |             |
|                           |           |     | +-----+-----------------+             |
|                           |           |     | | 401 | ADSL            |             |
|                           |           |     | +-----+-----------------+             |
|                           |           |     | | 402 | DDN             |             |
|                           |           |     | +-----+-----------------+             |
|                           |           |     | | 501 | NGN             |             |
|                           |           |     | +-----+-----------------+             |
|                           |           |     | | 502 | ISDN            |             |
|                           |           |     | +-----+-----------------+             |
|                           |           |     | | ALL | ALL             |             |
|                           |           |     | +-----+-----------------+             |
+---------------------------+-----------+-----+---------------------------------------+
| featureCode               | string    | O   | Feature Code for Product              |
+---------------------------+-----------+-----+---------------------------------------+

   |br|

.. _model-deposity-entity:

Deposit
------------------

.. rst-class:: text-align-justify

It'll be added for later.

   |br|
