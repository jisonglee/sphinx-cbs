.. |br| raw:: html

   <br />

*******************
Billing
*******************

.. contents::
   :local:
   :depth: 2

.. _scenario-billing-invoice-payment:

Payment
=================

Invoice Payment
-----------------

This topic shows how to pay invoice.
|br| 
|br|

1. Login
~~~~~~~~~~~

Cf. :ref:`Login API<login-login>`
|br| 
|br| 

**Request**

.. sourcecode:: http

    POST /api/v1/auth/login HTTP/1.1
    Accept: application/json

**Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
        "code" : 0,
        "result" : {
            "token_type" : "Bearer",
            "access_token" : "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE1NTM2NTk3NDQsImlhdCI6MTU1MzY1NDM0NCwiaWRlbnRpZmllciI6IndvcmtlcjAwMSIsImF0dHJpYnV0ZXMiOnsicm9sZSI6IjEwMCwxMDEifX0.6DsOCiT5OjDxrOPU-DIOXd684Nw7PDDwUbuHNMDgb_0",
            "access_token_expires_in" : 5400,
            "refresh_token" : "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE1NTM2Njg3NDQsImlhdCI6MTU1MzY1NDM0NCwiaWRlbnRpZmllciI6IndvcmtlcjAwMSIsImF0dHJpYnV0ZXMiOnt9fQ.fZJnLwZdCBGMT44eSgNXg21DKvIasmBPIBZK5slv4wM",
            "refresh_token_expires_in" : 14400
        }
    }

.. warning::

    The client must send an access token in the Authorization header when making requests except Login API. |br|
    Authorization: <token_type> <access_token>

2. Search Subscriber
~~~~~~~~~~~~~~~~~~~~~~

Choose Subscriber ID whose status is Active. 
|br|

Cf. :ref:`Search Subscriber API<subscriber-search>`
|br| 
|br| 

**Request**

.. sourcecode:: http

    GET /api/v1/subs/subscriber HTTP/1.1
    Accept: application/json
    Athorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE1NTM2NTk3NDQsImlhdCI6MTU1MzY1NDM0NCwiaWRlbnRpZmllciI6IndvcmtlcjAwMSIsImF0dHJpYnV0ZXMiOnsicm9sZSI6IjEwMCwxMDEifX0.6DsOCiT5OjDxrOPU-DIOXd684Nw7PDDwUbuHNMDgb_0

**Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    {  
        "result":{  
            "code":0,
            "desc":"Ok"
        },
        "objects":[  
            {  
                "subs":{  
                    "subsId":4001439,
                    "subsType":"S",
                    "svcDomain":3,
                    "subDomain":301,
                    "imsiNo":"428880300000151",
                    "custId":44,
                    "userId":"CA-4001439",
                    "billAcntId":1000190199,
                    "billType":"PST",
                    "password":"112607",
                    "status":"A",
                    "addrId":306,
                    "aceno":1000195405,
                    "createdAt":"2019-03-04T12:40:03+0800",
                    "updatedAt":"2019-03-04T14:05:38+0800",
                    "prodName":"UB CaTV 7000 (Basic)"
                }
            }
        ],
        "pagination":{  
            "page":1,
            "nitem":10
        }
    }

3. Get Charge History
~~~~~~~~~~~~~~~~~~~~~~~

Choose Charge Information whose unpaidAmt is not 0.
|br|

Cf. :ref:`Get Charge History API<charge-history>`
|br| 
|br| 

**Request**

.. sourcecode:: http

    GET /api/v1/bs/charge/hist/subscriber/4001439?from=20190227&until=20190327 HTTP/1.1
    Accept: application/json
    Athorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE1NTM2NTk3NDQsImlhdCI6MTU1MzY1NDM0NCwiaWRlbnRpZmllciI6IndvcmtlcjAwMSIsImF0dHJpYnV0ZXMiOnsicm9sZSI6IjEwMCwxMDEifX0.6DsOCiT5OjDxrOPU-DIOXd684Nw7PDDwUbuHNMDgb_0

**Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
        "result": {
            "code": 0,
            "desc": "Ok"
        },
        "objects": [
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
        ],
        "pagination": {
            "page": 1,
            "nitem": 10
        }
    }

4. Get Charge Information for Invoice Payment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Cf. :ref:`Get Charge By Operation API<charge-by-op>`
|br| 
|br| 

**Request**

.. sourcecode:: http

    GET /api/v1/bs/charge/invpym/subscriber/4001439?chargeId=1000002568&chargedMonth=201903 HTTP/1.1
    Accept: application/json
    Athorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE1NTM2NTk3NDQsImlhdCI6MTU1MzY1NDM0NCwiaWRlbnRpZmllciI6IndvcmtlcjAwMSIsImF0dHJpYnV0ZXMiOnsicm9sZSI6IjEwMCwxMDEifX0.6DsOCiT5OjDxrOPU-DIOXd684Nw7PDDwUbuHNMDgb_0

**Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    {  
        "result":{  
            "code":0,
            "desc":"Ok"
        },
        "objects":{  
            "charge":[  
                {  
                    "pymType":"INV",
                    "pymCd":"9000",
                    "pymCdName":"CaTv VAS",
                    "amount":225.8,
                    "vat":0.1,
                    "chargeId":1000002812
                }
            ],
            "custId":44,
            "custType":"PSN"
        }
    }

5. Invoice Payment
~~~~~~~~~~~~~~~~~~~~~~~~~

Cf. :ref:`Payment API<api-payment>`
|br| 
|br| 

**Request**

.. sourcecode:: http

    POST /api/v1/bs/pym/invpym/subscriber/4001439 HTTP/1.1
    Accept: application/json
    Athorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE1NTM2NTk3NDQsImlhdCI6MTU1MzY1NDM0NCwiaWRlbnRpZmllciI6IndvcmtlcjAwMSIsImF0dHJpYnV0ZXMiOnsicm9sZSI6IjEwMCwxMDEifX0.6DsOCiT5OjDxrOPU-DIOXd684Nw7PDDwUbuHNMDgb_0

    {  
        "charge":[  
            {  
                "reqAmt":225.8,
                "reqVat":22.58,
                "chargeId":1000002812,
                "pymCd":"9000",
                "name":"CaTv VAS",
                "qty":1,
                "unitPrice":225.8,
                "paid":true
            }
        ],
        "payment":[  
            {  
                "pymMtd":"CSH",
                "amt":248.38,
                "desc":"None"
            }
        ],
        "subsId":4001439,
        "taxId":""
    }

* Payload
    * ``charge`` : Charge Information
        * ``reqAmt`` : same as amount
        * ``reqVat`` : amount * vat ex) 225.8 * 0.1
        * ``chargeId`` : same as chargeId in Get Invoice Payment API
        * ``pymCd`` : same as pymCd
        * ``name`` : same as pymCdName
        * ``qty`` : 1
        * ``unitPrice`` : same as amount
        * ``paid`` : true
    * ``payment`` : Payment Information
        * ``pymMtd`` : payment method
        * ``amt`` : amount + amount * vat ex) 225.8 + 225.8 * 0.1
        * ``desc`` : description
    * ``subsId`` : Subscriber ID
    * ``taxId`` : Tax ID

**Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    {  
        "result":{  
            "code":0,
            "desc":"Success"
        },
        "id":1000002812
    }