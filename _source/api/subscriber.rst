.. |br| raw:: html

   <br />

.. _api-subscriber:

*******************
Subscriber
*******************

.. contents:: Table of Contents

Subscriber
==========

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

  :>json object result: :ref:`API 결과<model-common-result>`
  :>json array objects: Array of :ref:`Subscriber List<subscriber-search-list-model>`
  :>json object pagination: :ref:`Pagination Information<model-common-pagination>`

.. _subscriber-search-list-model:

  **Subscriber List Model**

  .. rst-class:: table-width-fix
  .. rst-class:: table-width-full
  .. rst-class:: text-align-justify

  +---------------------------+----------+-----+------------------------------------------------------------+
  | Key                       | Type     | M/O | Description                                                |
  +===========================+==========+=====+============================================================+
  | subs                      | object   | M   | :ref:`Subscriber Information<model-subscriber-entity>`     |
  +---------------------------+----------+-----+------------------------------------------------------------+
  | cnvgId                    | integer  | O   | Convergence ID |br|                                        |
  |                           |          |     | Only use for a subscriber whose service domain is 'Bundle' |
  +---------------------------+----------+-----+------------------------------------------------------------+
  | upperId                   | integer  | O   | Convergence ID |br|                                        |
  |                           |          |     | Only use for a subscriber included in the bundle           |
  +---------------------------+----------+-----+------------------------------------------------------------+

     |br|
