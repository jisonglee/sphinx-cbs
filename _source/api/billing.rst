.. |br| raw:: html

   <br />

*******************
Billing
*******************

.. contents:: Table of Contents

.. _api-charge:

Charge
==========

.. _charge-by-op:

Get Charge By Operation
------------------------

.. rst-class:: text-align-justify

.. http:get:: /api/v1/bs/charge/(operationId)/(entityType)/(long:id)

  **Example request**:

    .. sourcecode:: http

      GET /api/v1/bs/charge/svcsv/subscriber/4000123?until=20190531 HTTP/1.1
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
          "objects": {
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
      }

  :param string operationId: Operation ID
  :param string entityType: Select an entity, either 'subscriber' or 'customer'
  :param long id: The unique ID of the selected entityType.

  :query from: Start date for the selected operation
  :query to: Due date for the selected operation
  :query num: Operation target phone number
  :query refund: Refund Charge ID
  :query orderId: Order ID
  :query orderSeqno: The unique sequence number of Sub-order
  :query isFamily: Family member or not
  :query chargeId: Charge ID
  :query chargedMonth: Charged Date. YYYYMM.

  :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request

  :>json object result: :ref:`API Result<model-common-result>`
  :>json object objects: Object of :ref:`Charge Information for Customer<model-billing-charge-info-cust>`

     |br|

.. _charge-newcn:

Get Charge for New Connection
-------------------------------

.. rst-class:: text-align-justify

.. http:get:: /api/v1/bs/charge/(long:orderId)/(long:orderSeqno)

  **Example request**:

    .. sourcecode:: http

        GET /api/v1/bs/charge/1082/842 HTTP/1.1
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
            "objects":{  
                "charge":[  
                    {  
                        "pymType":"OTP",
                        "pymCd":"0001",
                        "pymCdName":"Installation Fee",
                        "amount":15000,
                        "vat":0.1,
                        "chargeId":1000001473
                    },
                    {  
                        "pymType":"OTP",
                        "pymCd":"1501",
                        "pymCdName":"Normal Number Fee",
                        "amount":30000,
                        "vat":0.1,
                        "chargeId":1000001473
                    }
                ],
                "custId":4,
                "custType":"GRP"
            }
        }

  :param long orderId: New Connection Order ID
  :param long orderSeqno: The unique sequence number of Sub-order. If subscription type is bundle, then orderSeqno must be 0

  :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :resheader Content-Type: this depends on :mailheader:`Accept`
                            of request

  :>json object result: :ref:`API Result<model-common-result>`
  :>json object objects: Object of :ref:`Charge Information for Customer<model-billing-charge-info-cust>`

    |br|

.. _charge-otherpym:

Get Charge for Other Payment
-------------------------------

.. rst-class:: text-align-justify

.. http:get:: /api/v1/bs/charge/otherpym

  **Example request**:

    .. sourcecode:: http

      GET /api/v1/bs/charge/otherpym HTTP/1.1
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
                  "pymType": "OTP",
                  "pymCd": "5002",
                  "pymCdName": "Rental",
                  "amount": 2000,
                  "vat": 0.1,
                  "chargeId": 0
              }
          ],
          "pagination": {
              "page": 1,
              "nitem": 10
          }
      }


  :query lang: Language. default is 'en'(English)
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
  :>json array objects: Array of :ref:`Charge Information<model-billing-charge-info>`
  :>json object pagination: :ref:`Pagination Information<model-common-pagination>`

  |br|

.. _charge-history:

Get Charge History
------------------------

.. rst-class:: text-align-justify

.. http:get:: /api/v1/bs/charge/hist/subscriber/(long:subsId)

  **Example request**:

    .. sourcecode:: http

        GET /api/v1/bs/charge/hist/subscriber/4001439?from=20190227&until=20190327 HTTP/1.1
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

  :param long subsId: Subscriber ID

  :query from: Specify start date
  :query until: Specify end date
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
  :>json object objects: Object of :ref:`Charge History<model-billing-charge-hist>`

     |br|

.. _api-payment:

Payment
==========

.. _payment-add:

Payment
------------------------

.. rst-class:: text-align-justify

.. http:post:: /api/v1/bs/pym/(operationId)/(entityType)/(long:id)

  **Example request**:

    .. sourcecode:: http

        POST /api/v1/bs/pym/newcn/subscriber/684 HTTP/1.1
        Accept: application/json
        Athorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9..

        {
            "charge":[
                {
                    "reqAmt":15000,
                    "reqVat":1500,
                    "chargeId":1000001473,
                    "pymCd":"0001",
                    "name":"Installation Fee",
                    "qty":1,
                    "unitPrice":15000,
                    "paid":true
                },
                {
                    "reqAmt":30000,
                    "reqVat":3000,
                    "chargeId":1000001473,
                    "pymCd":"1501",
                    "name":"Normal Number Fee",
                    "qty":1,
                    "unitPrice":30000,
                    "paid":true
                }
            ],
            "payment":[
                {
                    "pymMtd":"CSH",
                    "amt":49500,
                    "desc":"None"
                }
            ],
            "subsId":684,
            "taxId":""
        }

  **Example response**:

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: application/json

        {
            "result": {
                "code": 0,
                "desc": "Ok"
            }
        }

  :param string operationId: Operation ID
  :param string entityType: Select an entity, either 'subscriber' or 'customer'
  :param long id: The unique ID of the selected entityType.

  :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :<json array charge: Array of :ref:`Charge Information for Payment<model-billing-charge-info-payment>`
  :<json array payment: Array of :ref:`Payment Information<model-billing-payment-info>`
  :<json integer subsId: Subcriber ID
  :<json string taxId: TAX ID for Corporate
  :<json string remark: Remark
  :<json object order: Order Information

  :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request

  :>json object result: :ref:`API Result<model-common-result>`


     |br|


.. _payment-get-hist:

Get Payment History
------------------------

.. rst-class:: text-align-justify

.. http:get:: /api/v1/bs/pym/hist/subscriber/(long:subsId)

  **Example request**:

    .. sourcecode:: http

        GET /api/v1/bs/pym/hist/subscriber/4001742?from=20190226&until=20190326 HTTP/1.1
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
            ],
            "pagination": {
                "page": 1,
                "nitem": 10
            }
        }

  :param long subsId: Subscriber ID

  :query from: Start date
  :query to: Due date
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
  :>json array objects: Array of :ref:`Payment History<model-billing-payment-hist>`
  :>json object pagination: :ref:`Pagination Information<model-common-pagination>`

     |br|

.. _api-rcpt:

Receipt
==========

.. _get-receipt:

Get Receipt
------------------------

.. rst-class:: text-align-justify

.. http:get:: /api/v1/bs/pym/rcpt/(long:chargeId)

  **Example request**:

    .. sourcecode:: http

        GET /api/v1/bs/pym/rcpt/1000001473?lang=mn HTTP/1.1
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
                    "VAT":"4,500.00",
                    "BUYER_TAX_ID":"",
                    "TRX_NO":"1000001473",
                    "BARIMT_AMT":".00",
                    "PAID_AMT":"49,500.00",
                    "TEMPLATE":"1101",
                    "QR":"3351708349654546105....",
                    "LOTTERY":"JO DEMO7611",
                    "TRX_DTTM":"2019-01-25 17:51:47",
                    "OPERATOR_ID":"testuser",
                    "TAX_NO":"000000000038001190114976657137930"
                },{
                    "ITEM_NO":"1000011021",
                    "ITEM_NAME":"Installation Fee",
                    "PRICE":"15000",
                    "DESC":"",
                    "DISCOUNT":"0",
                    "PAYMENT":"16500",
                    "PIECE":"1"
                },{
                    "ITEM_NO":"1000011022",
                    "ITEM_NAME":"Normal Number Fee",
                    "PRICE":"30000",
                    "DESC":"",
                    "DISCOUNT":"0",
                    "PAYMENT":"33000",
                    "PIECE":"1"
                }
            ]
        }


  :param long chargeId: The unique ID for Charge

  :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request

  :>json object result: :ref:`API Result<model-common-result>`
  :>json array objects: Array of Receipt

     |br|
