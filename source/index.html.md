---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# SASEUL

Welcome to the SASEUL API! You can use our API to access SASEUL API endpoints, 
which can get information on various info in SASEUL.

We have language bindings in JavaScript! You can view code examples in the dark area to the right.

This example API documentation page was created with [Slate](https://github.com/lord/slate). Feel free to edit it and use it as a base for your own API's documentation.

## 계정 생성

새로운 계정을 생성합니다.

### HTTP Request
`GET http://example.com/request/createaddress`

```javascript
async createAccount(param) {
  const URL = 'http://example.com/request/createaddress';
  const params = {};

  try {
    const response = await axios.get(URL, {params});
    return response.data.data;
  } catch (e) {
    return e;
  }
}
```

### URL Parameters
* 요청

| 필드                     | 타입   | 설명                                   |
|--------------------------|--------|-------------------------------------|
| -                        | -      |              -                      |

* 응답

| 필드                     | 타입   | 설명                                |
|---|---|---|
| private_key              | string | 비밀키 입니다. |
| public_key               | string | 공개키 입니다. |
| address                  | string | 주소 입니다. |

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
```

> The above command returns JSON structured like this:

````json
[
  {
    "private_key": "429cdafbc4214fbb57330195be16ebcd17409082c080f00c0005833e1ec279fc",
    "public_key": "f4f3244caba576d98d566da1f359e1646ec85fa61e5a4d320c4bce97da1a15c1",
    "address": "0x6faea1e865dc2a42c3c0ec94bb554a03a95bafa7d4f2e7"
  }
]

````


## 잔고 조회

계정의 금액 정보를 조회 합니다.

### HTTP Request
`GET http://example.com/request/getbalancetest`

```javascript
async getBalance(param) {
  const URL = 'http://example.com/request/getbalancetest';
  const params = {};
  param.url = URL;
  param.priKey = PC_PRI_KEY;
  param.pubKey = PC_PUB_KEY;
  
  try {
    const response = await axios.get(URL, {params});
    return response.data.data;
  } catch (e) {
    return e;
  }
}
```

### URL Parameters

* 요청

| 필드        | 타입   | 설명    |
|-------------|--------|---------|
| private_key | string | 개인 키 |
| public_key  | string | 공개 키 |

* 응답

| 필드                     | 타입   | 설명                                |
|--------------------------|--------|-------------------------------------|
| address                  | string | 계정의 주소                         |
| balance                  | object | 잔고 객체                           |
| balance.precommit        | number | 확정되지 않은 잔고                  |
| balance.committed        | number | 확정된 잔고                         |
| deposit                  | object | deposit 객체                        |
| deposit.precommit        | number | 확정되지 않은 deposit               |
| deposit.committed        | number | 확정된 deposit                      |
| lbt_amount               | number | ?                                   |
| r_transaction            | object | 리스폰스 트랜잭션 정보?             |
| r_transaction.version    | string | 사슬의 버전                         |
| r_transaction.type       | string | 요청 타입?                          |
| r_transaction.public_key | string | 공개 키                             |
| r_transaction.from       | string | 주소                                |
| r_transaction.timestamp  | number | 트랜잭션이 발생했을 때의 타임스탬프 |


```shell
# With shell, you can just pass the correct header with each request
curl "http://example.com//request/getbalancetest"
```

> The above command returns JSON structured like this:

```json
[
  {
      "address": "0x6f085df4022b83c80e6c61caf5ccbe128755cf874a28c2",
      "balance":
      {
          "precommit": 0,
          "committed": 109988631
      },
      "deposit":
      {
          "precommit": 0,
          "committed": 0
      },
      "lbt_amount": 5995745,
      "r_transaction":
      {
          "version": "0.2",
          "type": "GetBalance",
          "public_key": "82df74db81fd0c1072aa0a6679a9ad34b36899044512c68b13edc0d91dcbee7d",
          "from": "0x6f085df4022b83c80e6c61caf5ccbe128755cf874a28c2",
          "timestamp": 1551677386249446
      }
  }
]
```
