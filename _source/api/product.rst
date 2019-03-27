.. |br| raw:: html

   <br />

.. _api-product:

*******************
Product
*******************

.. contents:: Table of Contents

Attribute
===========

.. _address-get:

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
