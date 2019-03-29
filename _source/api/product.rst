.. |br| raw:: html

   <br />

.. _api-product:

*******************
Product
*******************

.. contents:: Table of Contents

.. _api-product-attribute:

Attribute
===========

.. _attribute-get:

Get Attribute
------------------

.. rst-class:: text-align-justify

Returns UI attribute information for each data in the product optional information.

|br|
|br|

.. http:get:: /api/v1/prod/attrInfo/scheme

  **Example request**:

  .. sourcecode:: http

    GET /api/v1/prod/attrInfo/scheme?operationId=newcn&billType=PPD&stateId=cs&subDomain=301 HTTP/1.1
    Accept: application/json
    Athorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9..

  **Example response**:

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
                "attrId": "cs_div_1",
                "attrName": "CS-Remark",
                "attrType": "divider",
                "billType": "ALL",
                "custType": "ALL",
                "stateId": "cs",
                "operationId": "newcn",
                "defValue": "",
                "subDomain": "ALL"
            },
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
        ]
    }


  :query billType: Billing Type. ex) Prepaid service = PPD, etc
  :query custType: Customer Type. ex) Residentail = PSN, etc.
  :query operationId: Operation ID
  :query prodCd: Product Code
  :query stateId: State ID for order management. ex) Statistic = statistic, etc.
  :query subDomain: SubDomain code. ex) CableTV = 301, ADSL = 401, etc

  :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request

  :>json object result: :ref:`API Result<model-common-result>`
  :>json array objects: Array of :ref:`Product Attribute<model-product-attribute>`

     |br|

.. _api-product-product:

Product
===========

.. _product-search:

Search Product
------------------

.. rst-class:: text-align-justify

.. http:get:: /api/v1/rsc/prod

  **Example request**:

  .. sourcecode:: http

    GET /api/v1/rsc/prod?prodKdCd=MAN&allowedCustType=PSN&exclBySubsId=4001887&domain=5&subDomain=501&billType=PST HTTP/1.1
    Accept: application/json
    Athorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9..

  **Example response**:

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
      ],
      "pagination":{  
          "page":1,
          "nitem":10
      }
    }

  :query allowedCustType: Customer Type. ex) Residentail = PSN, etc.
  :query billType: Billing Type. ex) Prepaid service = PPD, etc
  :query bundleProdCd: Bundle Product Code
  :query domain: Service Domain. ex) CableTV = 3, Internet = 4, etc
  :query exclBySubsId: Subscriber ID. Search for non-subscribed products
  :query prodCd: Product Code
  :query prodName: Product Name; *partial match allowed*
  :query prodKdCd: Product Type. ex) Main = MAN, VAS = VAS
  :query subsId: Subscriber ID. Search for subscribed products
  :query subDomain: SubDomain code. ex) CableTV = 301, ADSL = 401, etc
  :query nitem: Number of items in a page. default is 10
  :query page: Current page number. default is 1
  :query total: Return total number of items
  :query all: No pagination. Return all items

  :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request

  :>json object result: :ref:`API Result<model-common-result>`
  :>json array objects: Array of :ref:`Product With Info<model-product-with-info>`

     |br|
