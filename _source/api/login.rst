.. |br| raw:: html

   <br />

*******************
Login
*******************

.. contents:: Table of Contents

.. _api-login:

Login
==========

.. _login-login:

Login
--------

.. rst-class:: text-align-justify

.. http:post:: /api/v1/auth/login

  **Example request**:

  .. sourcecode:: http

    POST /api/v1/auth/login HTTP/1.1
    Accept: application/json

    {
      "user":"testuser",
      "password":"111111"
    }

  **Example response**:

  .. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
      "code": 0,
      "result": {
        "token_type": "Bearer",
        "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiO...",
        "access_token_expires_in": 1800,
        "refresh_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE1NDQxNzcxOTAsI...",
        "refresh_token_expires_in": 14400
      },
      "redirect": "pw/reset"
    }



  :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header

  :<json string user: ID
  :<json string password: Password

  :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request

  :>json integer code: Result code (0:OK)
  :>json object result: :ref:`Login Result<login-login-result-model>`
  :>json string redirect: Redirect Value

.. _login-login-result-model:

  **Result Model**

  .. rst-class:: table-width-fix
  .. rst-class:: table-width-full
  .. rst-class:: text-align-justify

  +---------------------------+----------+-----+-----------------------------------+
  | Key                       | Type     | M/O | Description                       |
  +===========================+==========+=====+===================================+
  | token_type                | string   | M   | Token Type                        |
  +---------------------------+----------+-----+-----------------------------------+
  | access_token              | string   | M   | Token Value                       |
  +---------------------------+----------+-----+-----------------------------------+
  | access_token_expires_in   | integer  | M   | Token Expiration Time             |
  +---------------------------+----------+-----+-----------------------------------+
  | refresh_token             | string   | M   | Refresh Token Value               |
  +---------------------------+----------+-----+-----------------------------------+
  | refresh_token_expires_in  | integer  | M   | Refresh Token Expiration Time     |
  +---------------------------+----------+-----+-----------------------------------+

     |br|

.. _login-refresh-token:

Refresh Token
----------------

.. rst-class:: text-align-justify

.. http:post:: /api/v1/auth/refresh

  **Example request**:

  .. sourcecode:: http

    POST /api/v1/auth/login HTTP/1.1
    Accept: application/json
    Athorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9..

    {
      "refresh_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE1NDQxNzcxOTAsI..."
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

  :<json string refresh_token: Refresh Token

  :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request

  :>json integer code: Result code (0:OK)
  :>json object result: :ref:`API Result<model-common-result>`
  :>json string redirect: Redirect Value

     |br|
