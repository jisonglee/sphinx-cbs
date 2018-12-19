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

      GET /api/v1/bs/charge/svcsv/subscriber/454050 HTTP/1.1
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
                  "pymCd": "0015",
                  "pymCdName": "Service Saving",
                  "amount": 4000,
                  "vat": 0.1,
                  "chargeId": 1000002495
              }
          ]
      }


  :query from: Start date for the selected operation
  :query to: Due date for the selected operation
  :query num: Operation target phone number
  :query refund: Refund Charge ID
  :query orderId: Order ID
  :query orderSeqno: The unique sequence number of Sub-order

  :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request

  :>json object result: :ref:`API 결과<model-common-result>`
  :>json array objects: Array of :ref:`Charge Information<model-billing-charge-info>`

  :param operationId: Operation ID
  :param entityType: Select an entity, either 'subscriber' or 'customer'
  :param id: The unique ID of the selected entityType.
  :type id: long

     |br|

.. _charge-newcn:

Get Charge for New Connection
-------------------------------

.. rst-class:: text-align-justify

.. http:get:: /api/v1/bs/charge/(long:orderId)/(long:orderSeqno)

  **Example request**:

    .. sourcecode:: http

      GET /api/v1/bs/charge/1215/subscriber/454050 HTTP/1.1
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
                    "pymCd": "0001",
                    "pymCdName": "Installation Fee",
                    "amount": 30000,
                    "vat": 0.1,
                    "chargeId": 1000002502
              }
         ]
      }


  :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :resheader Content-Type: this depends on :mailheader:`Accept`
                            of request

  :>json object result: :ref:`API 결과<model-common-result>`
  :>json array objects: Array of :ref:`Charge Information<model-billing-charge-info>`

  :param orderId: New Connection Order ID
  :param orderSeqno: The unique sequence number of Sub-order. If subscription type is bundle, then orderSeqno must be 0
  :type orderId: long
  :type orderSeqno: long

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

  :>json object result: :ref:`API 결과<model-common-result>`
  :>json array objects: Array of :ref:`Charge Information<model-billing-charge-info>`
  :>json object pagination: :ref:`Pagination Information<model-common-pagination>`

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

      POST /api/v1/bs/pym/svcsv/subscriber/454050 HTTP/1.1
      Accept: application/json
      Athorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9..

      {
          "charge": [
              {
                  "reqAmt": 1000,
                  "reqVat" : 100,
                  "pymCd": "314",
                  "chargeId" : 314,
                  "paid": true
              }
          ],
          "payment": [
              {
                  "pymMtd": "CSH",
                  "amt": 5000,
                  "bank": "A-Bank",
                  "desc": "received by cash"
              }
          ],
          "remark" : "Text"
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


  :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :<json array charge: Array of :ref:`Charge Information for Payment<model-billing-charge-info-payment>`
  :<json array payment: Array of :ref:`Payment Information<model-billing-payment-info>`
  :<json string remark: Remark

  :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request

  :>json object result: :ref:`API 결과<model-common-result>`

  :param operationId: Operation ID
  :param entityType: Select an entity, either 'subscriber' or 'customer'
  :param id: The unique ID of the selected entityType.
  :type id: long




     |br|
