---
description: Group Management API
---

# Group

{% api-method method="get" host="http://example.com" path="/api/v1/auth/group" %}
{% api-method-summary %}
Get Groups
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=false %}
Authorization token
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="tree" type="number" required=false %}
Upper group ID
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=false %}
Group name
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
  "result": {
    "code": 0,
    "desc": "Ok"
  },
  "objects": [
    {
      "level": 1,
      "grpId": 1,
      "grpName": "UANGEL Corporation",
      "upperGrpId": 0
    },
    {
      "level": 2,
      "grpId": 7,
      "grpName": "Global Business Division",
      "upperGrpId": 1
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="http://example.com" path="/api/v1/auth/group" %}
{% api-method-summary %}
Add a new Group
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Authorization token
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="grpName" type="string" required=true %}
Group name
{% endapi-method-parameter %}

{% api-method-parameter name="status" type="string" required=false %}
Group status
{% endapi-method-parameter %}

{% api-method-parameter name="upperGrpId" type="string" required=false %}
Upper group ID
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

```javascript
{
  "result": {
    "code": 0,
    "desc": "Ok"
  },
  "objects": [
    {
      "grpId": 1201,
      "grpName": "New Group",
      "status": "A",
      "upperGrpId": 12
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://example.com" path="/api/v1/auth/group/:id" %}
{% api-method-summary %}
Get the Group
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=false %}
Group ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=false %}
Authorization token
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "result": {
    "code": 0,
    "desc": "Ok"
  },
  "objects": [
    {
      "grpId": 1202,
      "grpName": "A Group",
      "status": "A",
      "upperGrpId": 12
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="http://example.com" path="/api/v1/auth/group/:id" %}
{% api-method-summary %}
Update the Group
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=false %}
Group ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=false %}
Authorization token
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="grpName" type="string" required=false %}
Group name
{% endapi-method-parameter %}

{% api-method-parameter name="status" type="string" required=false %}
Group status
{% endapi-method-parameter %}

{% api-method-parameter name="upperGrpId" type="string" required=false %}
Upper group ID
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "result": {
    "code": 0,
    "desc": "Ok"
  },
  "objects": [
    {
      "grpId": 1202,
      "grpName": "A Group",
      "status": "A",
      "upperGrpId": 12
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="delete" host="http://example.com" path="/api/v1/auth/group/:id" %}
{% api-method-summary %}
Delete the Group
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="number" required=false %}
Group ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=false %}
Authorization token
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "result": {
    "code": 0,
    "desc": "Ok"
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

