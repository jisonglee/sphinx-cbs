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

.. _model-billing-charge-hist:

Charge History
-------------------------------------

.. rst-class:: text-align-justify

**Example**:

.. code-block:: json

    {
        "chargedMonth": "201903",
        "chargeId": 1000002568,
        "chargedAmt": 248.38,
        "positiveAdj": 0,
        "negativeAdj": 0,
        "total": 248.38,
        "receivedAmt": 0,
        "overpym": 0,
        "unpaidAmt": 248.38
    }

**Definition**

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+---------------------------+-----------+-----+-----------------------------------+
| Key                       | Type      | M/O | Description                       |
+===========================+===========+=====+===================================+
| chargedMonth              | string    | M   | Charged Date. Format is YYYYMM    |
+---------------------------+-----------+-----+-----------------------------------+
| chargeId                  | integer   | M   | Charge ID                         |
+---------------------------+-----------+-----+-----------------------------------+
| chargedAmt                | double    | M   | Charged Amount                    |
+---------------------------+-----------+-----+-----------------------------------+
| positiveAdj               | double    | M   |                                   |
+---------------------------+-----------+-----+-----------------------------------+
| negativeAdj               | double    | M   |                                   |
+---------------------------+-----------+-----+-----------------------------------+
| total                     | double    | M   | Total Amount                      |
+---------------------------+-----------+-----+-----------------------------------+
| receivedAmt               | double    | M   | Received Amount                   |
+---------------------------+-----------+-----+-----------------------------------+
| overpym                   | double    | M   | Over Payment Amount               |
+---------------------------+-----------+-----+-----------------------------------+
| unpaidAmt                 | double    | M   | Unpaid Amount                     |
+---------------------------+-----------+-----+-----------------------------------+
| rtnMsg                    | string    | O   | Message                           |
+---------------------------+-----------+-----+-----------------------------------+

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

.. _model-billing-payment-hist:

Payment History
-------------------------------------

.. rst-class:: text-align-justify

**Example**:

.. code-block:: json

    {
        "pymSeqno": 1000002780,
        "paidAt": "2019-03-25T15:43:35+0800",
        "subsId": 4001742,
        "receiveType": "Cash",
        "paidAmt": 33000,
        "operatorId": "MTUB007040",
        "description": "None",
        "taxResult": "S",
        "pymSttsCd": "Y"
    }

**Definition**

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+---------------------------+-----------+-----+-----------------------------------+
| Key                       | Type      | M/O | Description                       |
+===========================+===========+=====+===================================+
| pymSeqno                  | integer   | M   | Payment Sequence Number           |
+---------------------------+-----------+-----+-----------------------------------+
| paidAt                    | date-time | M   | Payment Date                      |
+---------------------------+-----------+-----+-----------------------------------+
| subsId                    | integer   | M   | Subscriber ID                     |
+---------------------------+-----------+-----+-----------------------------------+
| receiveType               | string    | M   | Receive Type                      |
+---------------------------+-----------+-----+-----------------------------------+
| paidAmt                   | double    | M   | Payment Amount                    |
+---------------------------+-----------+-----+-----------------------------------+
| operatorId                | string    | O   | Staff ID                          |
+---------------------------+-----------+-----+-----------------------------------+
| description               | string    | O   | Description                       |
+---------------------------+-----------+-----+-----------------------------------+
| taxResult                 | string    | O   | TAX Result                        |
|                           |           |     |                                   |
|                           |           |     | +-----+-----------------+         |
|                           |           |     | | Val | Description     |         |
|                           |           |     | +=====+=================+         |
|                           |           |     | | S   | Success         |         |
|                           |           |     | +-----+-----------------+         |
|                           |           |     | | F   | Failure         |         |
|                           |           |     | +-----+-----------------+         |
+---------------------------+-----------+-----+-----------------------------------+
| pymSttsCd                 | string    | O   | Payment Status                    |
|                           |           |     |                                   |
|                           |           |     | +-----+-----------------+         |
|                           |           |     | | Val | Description     |         |
|                           |           |     | +=====+=================+         |
|                           |           |     | | Y   | Success         |         |
|                           |           |     | +-----+-----------------+         |
|                           |           |     | | C   | Canceled        |         |
|                           |           |     | +-----+-----------------+         |
+---------------------------+-----------+-----+-----------------------------------+

  |br|
