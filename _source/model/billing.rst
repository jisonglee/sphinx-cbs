.. |br| raw:: html

   <br />

.. _model-billing:

Billing
==========

.. _model-billing-charge-info-cust:

Charge Information for Customer
----------------------------------

.. rst-class:: text-align-justify

**Example**:

.. code-block:: json

    {
        "charge":[
            {
                "pymType":"OTP",
                "pymCd":"0015",
                "pymCdName":"Service Saving",
                "amount":7500,
                "vat":0.1,
                "chargeId":1000001433
            }
        ],
        "custId":10000960,
        "custType":"PSN"
    }

**Definition**

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+---------------------------+----------+-----+----------------------------------+
| Key                       | Type     | M/O | Description                      |
+===========================+==========+=====+==================================+
| charge                    | array    | M   | Array of :ref:`Charge Information|
|                           |          |     | <model-billing-charge-info>`     |
+---------------------------+----------+-----+----------------------------------+
| custId                    | string   | O   | Customer ID                      |
+---------------------------+----------+-----+----------------------------------+
| custType                  | string   | O   | Customer Type                    |
|                           |          |     |                                  |
|                           |          |     | +-----+-----------------+        |
|                           |          |     | | Val | Description     |        |
|                           |          |     | +=====+=================+        |
|                           |          |     | | PSN | Residential     |        |
|                           |          |     | +-----+-----------------+        |
|                           |          |     | | GRP | Corporate,      |        |
|                           |          |     | |     | Government      |        |
|                           |          |     | +-----+-----------------+        |
+---------------------------+----------+-----+----------------------------------+

   |br|

.. _model-billing-charge-info:

Charge Information
-------------------------

.. rst-class:: text-align-justify

**Example**:

.. code-block:: json

    {
        "pymType": "OTP",
        "pymCd": "0015",
        "pymCdName": "Service Saving",
        "amount": 4000,
        "vat": 0.1,
        "chargeId": 1000002495
    }

**Definition**

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+---------------------------+----------+-----+-----------------------------------+
| Key                       | Type     | M/O | Description                       |
+===========================+==========+=====+===================================+
| pymType                   | string   | M   | Payment Type                      |
|                           |          |     |                                   |
|                           |          |     | +-----+-----------------+         |
|                           |          |     | | Val | Description     |         |
|                           |          |     | +=====+=================+         |
|                           |          |     | | OTM | One Time Charge |         |
|                           |          |     | +-----+-----------------+         |
|                           |          |     | | DEV | Device Charge   |         |
|                           |          |     | +-----+-----------------+         |
|                           |          |     |                                   |
+---------------------------+----------+-----+-----------------------------------+
| pymCd                     | string   | M   | Payment Code                      |
+---------------------------+----------+-----+-----------------------------------+
| pymCdName                 | string   | M   | Payment Code Name                 |
|                           |          |     |                                   |
+---------------------------+----------+-----+-----------------------------------+
| amount                    | double   | M   | Charge Amount                     |
+---------------------------+----------+-----+-----------------------------------+
| vat                       | double   | M   | VAT rates                         |
+---------------------------+----------+-----+-----------------------------------+
| chargeId                  | integer  | O   | Charge ID                         |
+---------------------------+----------+-----+-----------------------------------+

   |br|

.. _model-billing-charge-info-payment:

Charge Information for Payment
-------------------------------------

.. rst-class:: text-align-justify

**Example**:

.. code-block:: json

   {
       "reqAmt": 1000,
       "reqVat" : 100,
       "pymCd": "314",
       "chargeId" : 314,
       "paid": true
   }

**Definition**

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+---------------------------+----------+-----+-----------------------------------+
| Key                       | Type     | M/O | Description                       |
+===========================+==========+=====+===================================+
| reqAmt                    | double   | M   | Requested Amount                  |
+---------------------------+----------+-----+-----------------------------------+
| reqVat                    | double   | M   | Requested VAT                     |
+---------------------------+----------+-----+-----------------------------------+
| pymCd                     | string   | M   | Payment Code                      |
+---------------------------+----------+-----+-----------------------------------+
| chargeId                  | integer  | M   | Charge ID                         |
+---------------------------+----------+-----+-----------------------------------+
| paid                      | boolean  | M   | Paid or not                       |
+---------------------------+----------+-----+-----------------------------------+

  |br|

.. _model-billing-payment-info:

Payment Information
-------------------------------------

.. rst-class:: text-align-justify

**Example**:

.. code-block:: json

    {
        "pymMtd": "CSH",
        "amt": 5000,
        "bank": "A-Bank",
        "desc": "received by cash"
    }

**Definition**

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+---------------------------+----------+-----+-----------------------------------+
| Key                       | Type     | M/O | Description                       |
+===========================+==========+=====+===================================+
| pymMtd                    | string   | M   | Payment Method                    |
|                           |          |     |                                   |
|                           |          |     | +-----+-----------------+         |
|                           |          |     | | Val | Description     |         |
|                           |          |     | +=====+=================+         |
|                           |          |     | | CSH | Cash            |         |
|                           |          |     | +-----+-----------------+         |
|                           |          |     | | POS | POS             |         |
|                           |          |     | +-----+-----------------+         |
|                           |          |     | | BNK | Bank            |         |
|                           |          |     | +-----+-----------------+         |
|                           |          |     | | CHK | Check Card      |         |
|                           |          |     | +-----+-----------------+         |
|                           |          |     |                                   |
+---------------------------+----------+-----+-----------------------------------+
| amt                       | double   | M   | Received Amount                   |
+---------------------------+----------+-----+-----------------------------------+
| bank                      | string   | O   | Bank Name                         |
+---------------------------+----------+-----+-----------------------------------+
| desc                      | string   | O   | Memo                              |
+---------------------------+----------+-----+-----------------------------------+

  |br|
