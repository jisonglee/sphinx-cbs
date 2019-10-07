.. |br| raw:: html

   <br />

.. _api-subscriber:

*******************
Subscriber
*******************

.. contents:: Table of Contents

.. _api-address:

Address
===========

.. _address-get:

Get Address
------------------

.. rst-class:: text-align-justify

.. http:get:: /api/v1/subs/address/(long:addrId)

  **Example request**:

  .. sourcecode:: http

    GET /api/v1/subs/address/582 HTTP/1.1
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
              "addrId": 582,
              "addrType": "2",
              "addNum": 10783,
              "custId": 10000641,
              "doorNumber": "1",
              "zipCode": "18190",
              "standardAddress": "УБ СОНГИНОХАЙРХАН 1 БАЯНГОЛЫН АМ-5 АМИНЫ ОРОН СУУЦ 43/3",
              "postAddress": "abc",
              "additionalInfo": "for test"
          }
      ]
    } 


  :param long addrId: Address ID

  :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request

  :>json object result: :ref:`API Result<model-common-result>`
  :>json array objects: Array of :ref:`Addresss<model-address-entity>`

     |br|

.. _address-get-extension:

Get Address (Extension)
----------------------------

.. rst-class:: text-align-justify

It provides additional information related to the address as well as basic address information.

|br|
|br|

.. http:get:: /api/v1/subs/address/(long:addrId)/extension

  **Example request**:

  .. sourcecode:: http

    GET /api/v1/subs/address/582/extension HTTP/1.1
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
              "addrId": 582,
              "addrType": "2",
              "addNum": 10783,
              "custId": 10000641,
              "doorNumber": "1",
              "zipCode": "18190",
              "standardAddress": "УБ СОНГИНОХАЙРХАН 1 БАЯНГОЛЫН АМ-5 АМИНЫ ОРОН СУУЦ 43/3",
              "postAddress": "abc",
              "additionalInfo": "for test",
              "fullAddress": "УБ СОНГИНОХАЙРХАН 1 БАЯНГОЛЫН АМ-5 АМИНЫ ОРОН СУУЦ 43/3 abc",
              "correspBranch": "100",
              "correspExchange": "200"
          }
      ]
    } 

  :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request

  :>json object result: :ref:`API Result<model-common-result>`
  :>json array objects: Array of :ref:`Address (Extension)<model-address-extension>`

     |br|

Customer
===========

.. _customer-search:

Search Customer
------------------

.. rst-class:: text-align-justify

.. http:get:: /api/v1/subs/customer

  **Example request**:

  .. sourcecode:: http

    GET /api/v1/subs/customer?userId=70609005&incTerm=false HTTP/1.1
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
              "custId": 10001363,
              "custName": "Х Х НАНСАА",
              "contactNum1": "88445544",
              "custType": "PSN",
              "custLevel": "BAS",
              "personalId": "ДЮ88112864",
              "userId": "70609005",
              "address": "УБ ЧИНГЭЛТЭЙ 1 БАГА ТОЙРУУ-3 ҮНДЭСНИЙ ҮНЭТ ЦААСНЫ БАЙР",
              "status": "A"
          }
      ],
      "pagination": {
          "page": 1,
          "nitem": 10
      }
    } 

  :query addrNum: Address Number
  :query custId: Customer ID
  :query custType: Customer Type. ex) Residentail = PSN, etc.
  :query custName: Customer Name; *partial match allowed*
  :query contactNum1: Contact Number 1
  :query filter: Data that matches any of these; Customer ID, Customer Name *(partial match)*, Contact Number 1, Subscriber ID *(partial match)* or User ID *(partial match)*
  :query incTerm: Include terminated subscriber or not. Default value is **false**
  :query personalId: Personal ID; *partial match allowed*
  :query subsId: Subscriber ID
  :query taxId: TAX ID; *partial match allowed*
  :query userId: User ID; *partial match allowed*

  :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request

  :>json object result: :ref:`API Result<model-common-result>`
  :>json array objects: Array of :ref:`Customer Search<model-customer-search>`
  :>json object pagination: :ref:`Pagination Information<model-common-pagination>`

     |br|

Subscriber
===========

.. _subscriber-search:

Search Subscriber
------------------

.. rst-class:: text-align-justify

.. http:get:: /api/v1/subs/subscriber

  **Example request**:

  .. sourcecode:: http

    GET /api/v1/subs/subscriber HTTP/1.1
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
                "subs": {
                    "subsId": 454050,
                    "subsType": "S",
                    "svcDomain": 5,
                    "subDomain": 501,
                    "custId": 152261,
                    "billAcntId": 189189,
                    "billType": "PST",
                    "status": "A",
                    "aceno": 1000347862,
                    "createdAt": "2018-12-18T14:23:30+0900",
                    "updatedAt": "2018-12-18T14:23:30+0900"
                }
            }
        ],
        "pagination": {
            "page": 1,
            "nitem": 1
        }
    }

  :query custId: Customer ID
  :query subsId: Subscriber ID
  :query userId: User ID
  :query svcDomain: Service domain code. ex) CableTV = 3, Internet = 4, etc
  :query subDomain: SubDomain code. ex) CableTV = 301, ADSL = 401, etc
  :query filter: Search subscribers that match either customer ID, subscriber ID, or user ID
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
  :>json array objects: Array of :ref:`Subscriber Search<model-subscriber-search>`
  :>json object pagination: :ref:`Pagination Information<model-common-pagination>`

     |br|

.. _subscriber-product-get:

Get Subscription Product
--------------------------

.. rst-class:: text-align-justify

.. http:get:: /api/v1/subs/subscriber/(long:subsId)/product

  **Example request**:

  .. sourcecode:: http

    GET /api/v1/subs/subscriber/4001742/product HTTP/1.1
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
              "subsProdId":189021,
              "subsId":4001742,
              "svcDomain":5,
              "subDomain":501,
              "prodName":"UB NGN Personal - 3500",
              "prodCd":"ub_ngn_p_3500",
              "prodKdCd":"MAN",
              "status":"A",
              "monthlyFee":3500,
              "thresholdYn":"Y",
              "svcStrtAt":"2019-03-25T15:42:13+0800",
              "svcEndAt":"9999-12-31T23:59:59+0800",
              "thresholdInfo":[  
                  {  
                      "subsProdId":189021,
                      "subsThresholdId":1842,
                      "depositId":"665217",
                      "threshold":200000,
                      "thresholdSttsCd":"A",
                      "subsId":4001742
                  },
                  {  
                      "subsProdId":189021,
                      "subsThresholdId":1841,
                      "depositId":"666154",
                      "threshold":200000,
                      "thresholdSttsCd":"A",
                      "subsId":4001742
                  }
              ],
              "optionalInfo":{  
                  "icnc_tech_box":"33",
                  "icnc_tech_branch":"2"
              }
          }
      ]
    }

  :param long subsId: Subscriber ID

  :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request

  :>json object result: :ref:`API Result<model-common-result>`
  :>json array objects: Array of :ref:`Subscription Product<model-subscription-product>`

     |br|

.. _subscriber-product-change:

Change Main Product
--------------------------

.. rst-class:: text-align-justify

.. http:put:: /api/v1/subs/subscriber/(long:subsId)/product/main

  **Example request**:

  .. sourcecode:: http

    PUT /api/v1/subs/subscriber/4001887/product/main HTTP/1.1
    Accept: application/json
    Athorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9..

    {  
      "subsInfo":{  
          "subsId":4001887,
          "password":"112864",
          "custId":10001501,
          "billAcntId":1000190243
      },
      "prodInfo":{  
          "subsId":4001887,
          "svcDomain":5,
          "subDomain":501,
          "prodCd":"ngn_intl_ngo_9700",
          "prodKdCd":"MAN",
          "status":"A",
          "monthlyFee":9700,
          "thresholdYn":"Y",
          "thresholdInfo":[  
            {  
                "depositId":"666154",
                "threshold":200000
            },
            {  
                "depositId":"665217",
                "threshold":200000
            }
          ],
          "optionalInfo":{}
      }
    }

  **Example response**:

  .. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
      "result":{
          "code":0,
          "desc":"Ok"
      }
    }

  :param long subsId: Subscriber ID

  :<json object subsInfo: :ref:`Subscriber Information<model-subscriber-entity>`. *Mendatory*
  :<json object prodInfo: :ref:`New Subscription Product<model-subscription-product>`. *Mendatory*

  :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request

  :>json object result: :ref:`API Result<model-common-result>`

     |br|

.. _subscriber-product-add:

Add VAS Product
--------------------------

.. rst-class:: text-align-justify

.. http:post:: /api/v1/subs/subscriber/(long:subsId)/product/vas

  **Example request**:

  .. sourcecode:: http

    POST /api/v1/subs/subscriber/4001887/product/vas HTTP/1.1
    Accept: application/json
    Athorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9..

    {  
      "prod":{  
          "subsId":4001887,
          "svcDomain":5,
          "subDomain":501,
          "prodCd":"ip_center",
          "prodKdCd":"VAS",
          "status":"A",
          "monthlyFee":2000,
          "thresholdYn":"N",
          "svcEndAt":"9999-12-31T23:59:59+0800",
          "optionalInfo":{  
            "cxg":"",
            "cxsg":"",
            "cxd":""
          }
      },
      "password":"test"
    }

  **Example response**:

  .. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
      "result":{
          "code":0,
          "desc":"Ok"
      }
    }

  :param long subsId: Subscriber ID

  :<json object prod: :ref:`New Subscription Product<model-subscription-product>`. *Mendatory*
  :<json object password: Customer Password (Not currently used)

  :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request

  :>json object result: :ref:`API Result<model-common-result>`

     |br|

.. _subscriber-product-delete:

Delete VAS Product
------------------------

.. rst-class:: text-align-justify

.. http:delete:: /api/v1/subs/subscriber/(long:subsId)/product/(long:subsProdId)

  **Example request**:

  .. sourcecode:: http

    DELETE /api/v1/subs/subscriber/4001887/product/189201 HTTP/1.1
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
      }
    }

  :param long subsId: Subscriber ID
  :param long subsProdId: Subscription Product ID

  :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request

  :>json object result: :ref:`API Result<model-common-result>`

     |br|

Terminate Subscription
------------------------

.. rst-class:: text-align-justify

.. http:delete:: /api/v1/subs/subscriber/(long:subsId)

  **Example request**:

  .. sourcecode:: http

    DELETE /api/v1/subs/subscriber/4001887 HTTP/1.1
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
      }
    }

  :param long subsId: Subscriber ID

  :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request

  :>json object result: :ref:`API Result<model-common-result>`

     |br|
