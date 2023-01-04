
## Pathfinder2 Firmware Restful API 정의서

이 서비스는 [Firebase RealtimeDatabase](https://firebase.google.com/docs/database?hl=ko&authuser=0)를 기반으로 Pathfinder2 Firmware Restful API를 구현하였습니다.

https 프로토콜 요청을 통해 제어하는 관련 기능 및 기술을 얻을 수 있도록 제작되었습니다.



- **개정이력**

|     작성일     |    버전     |       설명        | 비고 |
| :------------: | :---------: | :---------------: | :--: |
| **2022-10-07** | **API 1.0** | **API 최초 작성** |      |



- 목차

[TOC]







## FirmWare API



### 모든 FirmWare 정보 가져오기



##### Request

```http
GET /FirmWare.json?print=pretty HTTP/1.1
Host: pathfinder2-99477-default-rtdb.firebaseio.com
Protocol: Https
Url: https://pathfinder2-99477-default-rtdb.firebaseio.com/FirmWare.json?print=pretty
```

##### <u>하위 PATH 요청 가능</u>

/FirmWare/FirmWareCountry.json

/FirmWare/FirmWareCountry/CA.json

/FirmWare/FirmWareType.json

/FirmWare/FirmWareType/Connector.json

/FirmWare/list.json

/FirmWare/list/0.json



##### Parameter

```json
//no body
```

| Name         | Type     | Description                                    | Required |
| :----------- | :------- | :--------------------------------------------- | -------- |
| print=pretty | `String` | 데이터가 사람이 읽을 수 있는 형태로 반환됩니다 | X        |



##### Response Body

```json
{
    "FirmWareCountry": {
        "CA": 2,
        "EU": 1,
        "USA": 0
    },
    "FirmWareType": {
        "Connector": 0,
        "MINI": 3,
        "MINI TRX": 4,
        "Receiver": 1,
        "TRX": 2
    },
    "list": [
        {
            "countryIdx": 0,
            "countryName": "USA",
            "typeIdx": 0,
            "typeName": "Connector",
            "url": "https://storage.googleapis.com/pathfinder2-99477.appspot.com/FirmWare/USA/4008/connector2_dfu_package.zip",
            "versionCode": 4008,
            "versionName": "V4.0.08"
        },
        {
            "countryIdx": 0,
            "countryName": "USA",
            "typeIdx": 1,
            "typeName": "Receiver",
            "url": "https://storage.googleapis.com/pathfinder2-99477.appspot.com/FirmWare/USA/4008/receiver2_dfu_package.zip",
            "versionCode": 4008,
            "versionName": "V4.0.08"
        },
        {
            "countryIdx": 0,
            "countryName": "USA",
            "typeIdx": 2,
            "typeName": "TRX",
            "url": "https://storage.googleapis.com/pathfinder2-99477.appspot.com/FirmWare/USA/4008/receiver2_dfu_package.zip",
            "versionCode": 4008,
            "versionName": "V4.0.08"
        },
        {
            "countryIdx": 0,
            "countryName": "USA",
            "typeIdx": 3,
            "typeName": "MINI",
            "url": "https://storage.googleapis.com/pathfinder2-99477.appspot.com/FirmWare/USA/4008/receiver2_mini_dfu_package.zip",
            "versionCode": 4008,
            "versionName": "V4.0.08"
        },
        {
            "countryIdx": 0,
            "countryName": "USA",
            "typeIdx": 4,
            "typeName": "MINI TRX",
            "url": "https://storage.googleapis.com/pathfinder2-99477.appspot.com/FirmWare/USA/4008/receiver2_mini_dfu_package.zip",
            "versionCode": 4008,
            "versionName": "V4.0.08"
        },
        {
            "countryIdx": 1,
            "countryName": "EU",
            "typeIdx": 0,
            "typeName": "Connector",
            "url": "https://storage.googleapis.com/pathfinder2-99477.appspot.com/FirmWare/EU/2105/connector2_EU_dfu_package.zip",
            "versionCode": 2105,
            "versionName": "V2.1.05"
        },
        {
            "countryIdx": 1,
            "countryName": "EU",
            "typeIdx": 1,
            "typeName": "Receiver",
            "url": "https://storage.googleapis.com/pathfinder2-99477.appspot.com/FirmWare/EU/2105/receiver2_EU_dfu_package.zip",
            "versionCode": 2105,
            "versionName": "V2.1.05"
        },
        {
            "countryIdx": 1,
            "countryName": "EU",
            "typeIdx": 2,
            "typeName": "TRX",
            "url": "https://storage.googleapis.com/pathfinder2-99477.appspot.com/FirmWare/EU/2105/receiver2_EU_dfu_package.zip",
            "versionCode": 2105,
            "versionName": "V2.1.05"
        }
    ]
}
```

| Name            | Type         | Description                |
| :-------------- | :----------- | :------------------------- |
| FirmWareCountry | `JsonObject` | FirmWareCountry Index 정의 |
| FirmWareType    | `JsonObject` | FirmWareType Index 정의    |
| list            | `JsonArray`  | 펌웨어 리스트              |



##### Response Body - FirmWareCountry

FirmWareCountry Index 정의

| Name | Value | Type      | Description |
| ---- | ----- | :-------- | ----------- |
| USA  | 0     | `Integer` | 미국        |
| EU   | 1     | `Integer` | 유럽        |
| CA   | 2     | `Integer` | 캐나다      |

##### Response Body - FirmWareType

FirmWareType Index 정의

| Name      | Value | Type      | Description |
| --------- | ----- | --------- | ----------- |
| Connector | 0     | `Integer` | 커넥터      |
| Receiver  | 1     | `Integer` | 리시버      |
| TRX       | 2     | `Integer` | 리시버 TRX  |
| MINI      | 3     | `Integer` | 미니        |
| MINI TRX  | 4     | `Integer` | 미니 TRX    |

##### Response Body - list

| Name        | Type      | Description                   |
| ----------- | --------- | ----------------------------- |
| countryIdx  | `Integer` | FirmWareCountry.Value (Index) |
| countryName | `String`  | FirmWareCountry.Name          |
| typeIdx     | `Integer` | FirmWareType.Value  (Index)   |
| typeName    | `String`  | FirmWareType.Name             |
| url         | `String`  | 다운로드 URL                  |
| versionCode | `Integer` | 다운로드 버전 코드            |
| versionName | `String`  | 다운로드 현재 버전 이름       |





### Firebase Database REST API는 다음 오류 코드를 반환할 수 있습니다.

| HTTP  코드 | HTTP 상태        | Description                                                  |
| :--------- | ---------------- | ------------------------------------------------------------ |
| **400**    | 잘못된 요청      | 다음 오류 조건 중 하나:`PUT` 또는 `POST` 데이터를 구문 분석할 수 없습니다.`PUT` 또는 `POST` 데이터가 없습니다.<br />요청이 너무 큰 `PUT` 또는 `POST` 데이터를 시도합니다.<br />REST API 호출에 경로의 일부로 잘못된 하위 이름이 포함되어 있습니다.<br />REST API 호출 경로가 너무 깁니다.요청에 인식할 수 없는 서버 값이 있습니다.<br />쿼리 색인이 [Firebase 실시간 데이터베이스 규칙](https://firebase.google.com/docs/database/security#section-defining-indexes) 에 정의되어 있지 않습니다.<br />요청이 지정된 쿼리 매개변수 중 하나를 지원하지 않습니다.요청은 얕은 `GET` 요청과 쿼리 매개변수를 혼합합니다. |
| **401**    | 권한 없음        | 다음 오류 조건 중 하나:인증 토큰이 만료되었습니다.<br />요청에 사용된 인증 토큰이 잘못되었습니다.<br />access_token으로 인증하지 못했습니다.<br />요청이 [Firebase 실시간 데이터베이스 규칙을 위반합니다.](https://firebase.google.com/docs/database/security) |
| **404**    | 찾을 수 없음     | 지정된 실시간 데이터베이스를 찾을 수 없습니다.               |
| **500**    | 내부 서버 오류   | 서버에서 오류를 반환했습니다. 자세한 내용은 오류 메시지를 참조하십시오. |
| **503**    | 서비스 이용 불가 | 지정된 Firebase 실시간 데이터베이스를 일시적으로 사용할 수 없습니다. 이는 요청이 시도되지 않았음을 의미합니다. |
| **412**    | 전제 조건 실패   | if-match 헤더에 있는 요청의 지정된 ETag 값이 서버의 값과 일치하지 않습니다. |

##### Response Body

```json
{
    "error": "HTTP상태 메시지"
}
```










