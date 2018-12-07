.. |br| raw:: html

   <br />

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

  :<json string user: 계정 아이디
  :<json string password: 계정 패스워드

  :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request

  :>json integer code: Result code (0:OK)
  :>json object result: :ref:`로그인 결과<login-login-result-model>`
  :>json string redirect: Redirect 값

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
  | access_token              | string   | M   | Token 값                          |
  +---------------------------+----------+-----+-----------------------------------+
  | access_token_expires_in   | integer  | M   | Token 만료 시간                   |
  +---------------------------+----------+-----+-----------------------------------+
  | refresh_token             | string   | M   | Refresh Token 값                  |
  +---------------------------+----------+-----+-----------------------------------+
  | refresh_token_expires_in  | integer  | M   | Refresh Token 만료 시간           |
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
  :>json object result: :ref:`로그인 결과<login-refresh-token-result-model>`
  :>json string redirect: Redirect 값

.. _login-refresh-token-result-model:

  **Result Model**

  .. rst-class:: table-width-fix
  .. rst-class:: table-width-full
  .. rst-class:: text-align-justify

  +---------------------------+----------+-----+-----------------------------------+
  | Key                       | Type     | M/O | Description                       |
  +===========================+==========+=====+===================================+
  | code                      | integer  | M   | Result Code (0:Success)           |
  +---------------------------+----------+-----+-----------------------------------+
  | error                     | string   | O   | Error                             |
  +---------------------------+----------+-----+-----------------------------------+
  | desc                      | string   | M   | Description                       |
  +---------------------------+----------+-----+-----------------------------------+

     |br|
