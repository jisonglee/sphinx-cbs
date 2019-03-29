.. |br| raw:: html

   <br />

.. _api-resource:

*******************
Resource
*******************

.. contents:: Table of Contents

.. _api-number:

Number
==========


.. _number-search:

Search Number
------------------

.. rst-class:: text-align-justify

.. http:get:: /api/v1/rsc/num

  **Example request**:

  .. sourcecode:: http

    GET /api/v1/rsc/num?status=T&pattern=*75 HTTP/1.1
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
                "num": "135271675",
                "status": "T",
                "grade": "N"
            },
            {
                "num": "135271775",
                "status": "T",
                "grade": "N"
            },
            {
                "num": "135272075",
                "status": "T",
                "grade": "N"
            },
            {
                "num": "135271875",
                "status": "T",
                "grade": "N"
            },
            {
                "num": "135271975",
                "status": "T",
                "grade": "N"
            }
        ],
        "pagination": {
            "page": 1,
            "nitem": 10
        }
    }

  :query grade: Number Grade. ex) N = Normal, C = Copper, etc
  :query status: Status. ex) T = Temporary, A = Active, etc
  :query from: Specify the starting range of number
  :query to: Specify the ending range of number
  :query number: Specify Number
  :query custId: Customer ID (use when searching for reservation number)
  :query pattern: Number Pattern. ex) 7010* (=All numbers starting with 7010)
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
  :>json array objects: Array of :ref:`Number<model-resource-number>`
  :>json object pagination: :ref:`Pagination Information<model-common-pagination>`

     |br|



.. _number-get:

Get Number
---------------

.. rst-class:: text-align-justify

.. http:get:: /api/v1/rsc/num/(num)

  **Example request**:

  .. sourcecode:: http

    GET /api/v1/rsc/num/135271675 HTTP/1.1
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
                "num": "135271675",
                "status": "T",
                "grade": "N"
            }
        ]
    }

  :param string num: Phone Number

  :reqheader Accept: the response content type depends on
                    :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :resheader Content-Type: this depends on :mailheader:`Accept`
                        header of request

  :>json object result: :ref:`API Result<model-common-result>`
  :>json array objects: Array of :ref:`Number<model-resource-number>`

    |br|



.. _number-update:

Update Number
------------------

.. rst-class:: text-align-justify

Update the status and grade of the number.

|br|
|br|

.. http:put:: /api/v1/rsc/num/(num)

  **Example request**:

  .. sourcecode:: http

    PUT /api/v1/rsc/num/135271675 HTTP/1.1
    Accept: application/json
    Athorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9..

    {
        "status":"C",
        "grade":"N"
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

  :param string num: Phone Number

  :reqheader Accept: the response content type depends on
                    :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :<json string status: Status. ex) T = Temporary, A = Active, etc
  :<json string grade: Number Grade. ex) N = Normal, C = Copper, etc

  :resheader Content-Type: this depends on :mailheader:`Accept`
                        header of request

  :>json object result: :ref:`API Result<model-common-result>`

    |br|



.. _number-reserve:

Reserve Number
------------------

.. rst-class:: text-align-justify

Update the status of the number to *Reserved*. |br|
The 'temp' mode is used to prevent other users from selecting that number. After one hour, the status automatically changes to *Temporary*.

|br|
|br|

.. http:post:: /api/v1/rsc/num/(num)/reserv

  **Example request**:

  .. sourcecode:: http

    POST /api/v1/rsc/num/135271681/reserv HTTP/1.1
    Accept: application/json
    Athorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9..

    {  
        "mode":"new",
        "custId":10001381,
        "until":"20190531",
        "techData":"",
        "chargeId":1000002766
    }

  **Example response**:

  .. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
        "result": {
            "code": 0,
            "desc": "Ok"
        },
        "id": 2662
    }

  :param string num: Phone Number

  :reqheader Accept: the response content type depends on
                    :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :<json string mode: 2 reservation modes are supported. ex) new = Rerservation, temp = Temporary reservation for one hour.
  :<json integer custId: Customer ID
  :<json string mode: Reservation end date. Date format is YYYYMMDD. (Use only if mode is 'new')
  :<json strig techData: Technical Data. (Not currently used)
  :<json integer chargeId: Charge ID (Use only if mode is 'new')

  :resheader Content-Type: this depends on :mailheader:`Accept`
                        header of request

  :>json object result: :ref:`API Result<model-common-result>`
  :>json integer id: Order ID for reserving phone number

    |br|



.. _number-cancel:

Cancel Reservation
-------------------

Update the status of the number to *Temporary*. 

|br|
|br|

.. rst-class:: text-align-justify

.. http:delete:: /api/v1/rsc/num/(num)/reserv

  **Example request**:

  .. sourcecode:: http

    DELETE /api/v1/rsc/num/135271681/reserv HTTP/1.1
    Accept: application/json
    Athorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9..

    {  
        "mode":"cancel",
        "custId":10001381
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

  :param string num: Phone Number

  :reqheader Accept: the response content type depends on
                    :mailheader:`Accept` header
  :reqheader Authorization: Auth token to authenticate

  :<json string mode: 2 cancel modes are supported. ex) cancel = Cancel Rerservation, temp = Cancel Temporary reservation.
  :<json integer custId: Customer ID

  :resheader Content-Type: this depends on :mailheader:`Accept`
                        header of request

  :>json object result: :ref:`API Result<model-common-result>`

    |br|