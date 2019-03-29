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
|                           |           |     | | ALL | ALL             |             |
|                           |           |     | +-----+-----------------+             |
+---------------------------+-----------+-----+---------------------------------------+
| stateId                   | string    | M   | State ID for order management         |
+---------------------------+-----------+-----+---------------------------------------+
| operationId               | string    | O   | Operation ID                          |
+---------------------------+-----------+-----+---------------------------------------+
| defValue                  | string    | M   | Default Value |br| |br|               |
|                           |           |     | If the attr_type is radio, checkbox,  |                                  
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

.. _model-deposit-entity:

Deposit
------------------

.. rst-class:: text-align-justify

**Example**:

.. code-block:: json

      {  
            "deposit":{  
                  "setId":"665216",
                  "id":"666154",
                  "name":"PSTN International call",
                  "amount":0,
                  "unit":"Money"
            },
            "custType":"PSN",
            "threshold":{  
                  "min":100000,
                  "max":200000,
                  "default":200000
            }
      }

**Definition**

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+---------------------------+-----------+-----+------------------------------------------------+
| Key                       | Type      | M/O | Description                                    |
+===========================+===========+=====+================================================+
| deposit                   | object    | M   | :ref:`Deposit Information<model-deposit-info>` |
+---------------------------+-----------+-----+------------------------------------------------+
| custType                  | string    | O   | Customer Type                                  |
|                           |           |     |                                                |
|                           |           |     | +-----+-----------------+                      |
|                           |           |     | | Val | Description     |                      |
|                           |           |     | +=====+=================+                      |
|                           |           |     | | MAN | Main            |                      |
|                           |           |     | +-----+-----------------+                      |
|                           |           |     | | VAS | VAS             |                      |
|                           |           |     | +-----+-----------------+                      |
|                           |           |     | | ALL | ALL             |                      |
|                           |           |     | +-----+-----------------+                      |
+---------------------------+-----------+-----+------------------------------------------------+
| threshold                 | object    | M   | :ref:`Threshold<model-product-threshold>`      |
+---------------------------+-----------+-----+------------------------------------------------+

   |br|

.. _model-deposit-info:

Deposit Information
--------------------

.. rst-class:: text-align-justify

**Example**:

.. code-block:: json

      {  
            "setId":"665216",
            "id":"666154",
            "name":"PSTN International call",
            "amount":0,
            "unit":"Money"
      }

**Definition**

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+---------------------------+-----------+-----+-------------------------------------------+
| Key                       | Type      | M/O | Description                               |
+===========================+===========+=====+===========================================+
| setId                     | string    | M   | Deposit Set ID                            |
+---------------------------+-----------+-----+-------------------------------------------+
| id                        | string    | M   | Deposit ID                                |
+---------------------------+-----------+-----+-------------------------------------------+
| name                      | string    | O   | Deposit Name                              |
+---------------------------+-----------+-----+-------------------------------------------+
| amount                    | double    | M   | Deposit Amount                            |
+---------------------------+-----------+-----+-------------------------------------------+
| unit                      | string    | O   | Unit                                      |
+---------------------------+-----------+-----+-------------------------------------------+

   |br|

.. _model-monthlyfee-entity:

Monthly Fee
--------------------

.. rst-class:: text-align-justify

**Example**:

.. code-block:: json

      {  
            "min":10000,
            "max":20000
      }

**Definition**

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+---------------------------+-----------+-----+-------------------------------------------+
| Key                       | Type      | M/O | Description                               |
+===========================+===========+=====+===========================================+
| min                       | double    | O   | Monthly Fee Min                           |
+---------------------------+-----------+-----+-------------------------------------------+
| max                       | double    | O   | Monthly Fee Max                           |
+---------------------------+-----------+-----+-------------------------------------------+

   |br|

.. _model-product-product:

Product
-----------------

.. rst-class:: text-align-justify

**Example**:

.. code-block:: json

      {  
            "prodId":"ub_ngn_p_3500",
            "name":"UB NGN Personal - 3500",
            "mrktCd":"1",
            "domain":"5",
            "billType":"PST",
            "prodKdCd":"MAN",
            "allowedCustType":"PSN",
            "validStartDt":"2018-07-31T14:00:00+0800",
            "validEndDt":"9999-12-31T23:59:59+0800",
            "detail":{  
               "desc":"UB NGN Personal - 3500",
               "useCustomRate":false
            },
            "treatment":{}
      }

**Definition**

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+---------------------------+-----------+-----+-------------------------------------------+
| Key                       | Type      | M/O | Description                               |
+===========================+===========+=====+===========================================+
| prodId                    | string    | M   | Product Code                              |
+---------------------------+-----------+-----+-------------------------------------------+
| name                      | string    | O   | Product Name                              |
+---------------------------+-----------+-----+-------------------------------------------+
| mrktCd                    | string    | M   | Market Code                               |
|                           |           |     |                                           |
|                           |           |     | +-----+-----------------+                 |
|                           |           |     | | Val | Description     |                 |
|                           |           |     | +=====+=================+                 |
|                           |           |     | | 1   | MTC             |                 |
|                           |           |     | +-----+-----------------+                 |
+---------------------------+-----------+-----+-------------------------------------------+
| domain                    | string    | O   | Service Domain                            |
|                           |           |     |                                           |
|                           |           |     | +-----+-----------------+                 |
|                           |           |     | | Val | Description     |                 |
|                           |           |     | +=====+=================+                 |
|                           |           |     | | 1   | Bundle          |                 |
|                           |           |     | +-----+-----------------+                 |
|                           |           |     | | 3   | Cable TV        |                 |
|                           |           |     | +-----+-----------------+                 |
|                           |           |     | | 4   | Internet        |                 |
|                           |           |     | +-----+-----------------+                 |
|                           |           |     | | 5   | Telephony       |                 |
|                           |           |     | +-----+-----------------+                 |
+---------------------------+-----------+-----+-------------------------------------------+
| billType                  | string    | O   | Billing Type                              |
|                           |           |     |                                           |
|                           |           |     | +-----+-----------------+                 |
|                           |           |     | | Val | Description     |                 |
|                           |           |     | +=====+=================+                 |
|                           |           |     | | PPD | Prepaid         |                 |
|                           |           |     | +-----+-----------------+                 |
|                           |           |     | | PST | Cable TV        |                 |
|                           |           |     | +-----+-----------------+                 |
+---------------------------+-----------+-----+-------------------------------------------+
| prodKdCd                  | string    | O   | Product Type                              |
|                           |           |     |                                           |
|                           |           |     | +-----+-----------------+                 |
|                           |           |     | | Val | Description     |                 |
|                           |           |     | +=====+=================+                 |
|                           |           |     | | MAN | Main            |                 |
|                           |           |     | +-----+-----------------+                 |
|                           |           |     | | VAS | VAS             |                 |
|                           |           |     | +-----+-----------------+                 |
+---------------------------+-----------+-----+-------------------------------------------+
| allowedCustType           | string    | O   | Customer Type                             |
|                           |           |     |                                           |
|                           |           |     | +-----+-----------------+                 |
|                           |           |     | | Val | Description     |                 |
|                           |           |     | +=====+=================+                 |
|                           |           |     | | MAN | Main            |                 |
|                           |           |     | +-----+-----------------+                 |
|                           |           |     | | VAS | VAS             |                 |
|                           |           |     | +-----+-----------------+                 |
|                           |           |     | | ALL | ALL             |                 |
|                           |           |     | +-----+-----------------+                 |
+---------------------------+-----------+-----+-------------------------------------------+
| validStartDt              | date-time | O   | Valid Start Date                          |
+---------------------------+-----------+-----+-------------------------------------------+
| detail                    | object    | M   | :ref:`Detail<model-product-detail>`       |
+---------------------------+-----------+-----+-------------------------------------------+
| treatment                 | object    | M   | :ref:`Treatment<model-product-treatment>` |
+---------------------------+-----------+-----+-------------------------------------------+

   |br|

.. _model-product-detail:

Product Detail
-----------------

.. rst-class:: text-align-justify

**Example**:

.. code-block:: json

      {  
            "desc":"UB NGN Personal - 3500",
            "useCustomRate":false
      }

**Definition**

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+---------------------------+-----------+-----+---------------------------------------+
| Key                       | Type      | M/O | Description                           |
+===========================+===========+=====+=======================================+
| desc                      | string    | O   | Description                           |
+---------------------------+-----------+-----+---------------------------------------+
| discountDesc              | string    | O   | Discount Description                  |
+---------------------------+-----------+-----+---------------------------------------+
| bonusDesc                 | string    | O   | Bonus Description                     |
+---------------------------+-----------+-----+---------------------------------------+
| recommendedVas            | string    | O   | Recommended VAS                       |
+---------------------------+-----------+-----+---------------------------------------+
| minContractPeriod         | string    | O   | Contract Period                       |
+---------------------------+-----------+-----+---------------------------------------+
| useCustomRate             | boolean   | M   | Use Custom Rate or Not                |
+---------------------------+-----------+-----+---------------------------------------+

   |br|

.. _model-product-info:

Product Information
---------------------

.. rst-class:: text-align-justify

**Example**:

.. code-block:: json

      {  
            "rate":3500,
            "customRate":{},
            "depositSet":"Postpaid Telephony Deposit",
            "depositInfo":[  
                  {  
                        "deposit":{  
                              "setId":"665216",
                              "id":"666154",
                              "name":"PSTN International call",
                              "amount":0,
                              "unit":"Money"
                        },
                        "custType":"PSN",
                        "threshold":{  
                           "min":100000,
                           "max":200000,
                           "default":200000
                        }
                  },
                  {  
                        "deposit":{  
                              "setId":"665216",
                              "id":"665217",
                              "name":"TOTAL",
                              "amount":0,
                              "unit":"Money"
                        },
                        "custType":"PSN",
                        "threshold":{  
                              "min":100000,
                              "max":200000,
                              "default":200000
                        }
                  }
            ]
      }

**Definition**

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+---------------------------+-----------+-----+-----------------------------------------------+
| Key                       | Type      | M/O | Description                                   |
+===========================+===========+=====+===============================================+
| rate                      | double    | O   | Rate                                          |
+---------------------------+-----------+-----+-----------------------------------------------+
| customRate                | object    | M   | :ref:`Monthly Fee<model-monthlyfee-entity>`   |
+---------------------------+-----------+-----+-----------------------------------------------+
| depositSet                | string    | O   | Deposit Set                                   |
+---------------------------+-----------+-----+-----------------------------------------------+
| depositInfo               | array     | M   | Array of :ref:`Deposit<model-deposit-entity>` | 
+---------------------------+-----------+-----+-----------------------------------------------+

   |br|

.. _model-product-with-info:

Product With Info
------------------

.. rst-class:: text-align-justify

**Example**:

.. code-block:: json

   {  
         "product":{  
               "prodId":"ub_ngn_p_3500",
               "name":"UB NGN Personal - 3500",
               "mrktCd":"1",
               "domain":"5",
               "billType":"PST",
               "prodKdCd":"MAN",
               "allowedCustType":"PSN",
               "validStartDt":"2018-07-31T14:00:00+0800",
               "validEndDt":"9999-12-31T23:59:59+0800",
               "detail":{  
                     "desc":"UB NGN Personal - 3500",
                     "useCustomRate":false
               },
               "treatment":{}
         },
         "info":{  
               "rate":3500,
               "customRate":{},
               "depositSet":"Postpaid Telephony Deposit",
               "depositInfo":[  
                     {  
                           "deposit":{  
                                 "setId":"665216",
                                 "id":"666154",
                                 "name":"PSTN International call",
                                 "amount":0,
                                 "unit":"Money"
                           },
                           "custType":"PSN",
                           "threshold":{  
                                 "min":100000,
                                 "max":200000,
                                 "default":200000
                           }
                     },
                     {  
                           "deposit":{  
                                 "setId":"665216",
                                 "id":"665217",
                                 "name":"TOTAL",
                                 "amount":0,
                                 "unit":"Money"
                           },
                           "custType":"PSN",
                           "threshold":{  
                                 "min":100000,
                                 "max":200000,
                                 "default":200000
                           }
                     }
               ]
         },
         "featureCode":[  
               "POST_NGN"
         ]
   }

**Definition**

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+---------------------------+-----------+-----+---------------------------------------+
| Key                       | Type      | M/O | Description                           |
+===========================+===========+=====+=======================================+
| product                   | object    | M   | :ref:`Product<model-product-product>` |
+---------------------------+-----------+-----+---------------------------------------+
| info                      | object    | M   | `Product Additional Info<>__`         |
+---------------------------+-----------+-----+---------------------------------------+
| featureCode               | array     | M   | Feature Code List                     |
+---------------------------+-----------+-----+---------------------------------------+

   |br|

.. _model-product-threshold:

Threshold
-----------------

.. rst-class:: text-align-justify

**Example**:

.. code-block:: json

      {  
            "min":100000,
            "max":200000,
            "default":200000
      }

**Definition**

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+---------------------------+-----------+-----+---------------------------------------+
| Key                       | Type      | M/O | Description                           |
+===========================+===========+=====+=======================================+
| min                       | double    | M   | Treshold Min                          |
+---------------------------+-----------+-----+---------------------------------------+
| max                       | double    | O   | Treshold Max                          |
+---------------------------+-----------+-----+---------------------------------------+
| default                   | double    | M   | Threshold Default Value               |
+---------------------------+-----------+-----+---------------------------------------+

   |br|


.. _model-product-treatment:

Treatment
-----------------

.. rst-class:: text-align-justify

**Example**:

.. code-block:: json

      {  
            "price":1000,
            "day":20
      }

**Definition**

.. rst-class:: table-width-fix
.. rst-class:: table-width-full
.. rst-class:: text-align-justify

+---------------------------+-----------+-----+---------------------------------------+
| Key                       | Type      | M/O | Description                           |
+===========================+===========+=====+=======================================+
| price                     | double    | O   | Price                                 |
+---------------------------+-----------+-----+---------------------------------------+
| day                       | integer   | O   | Day                                   |
+---------------------------+-----------+-----+---------------------------------------+

   |br|
