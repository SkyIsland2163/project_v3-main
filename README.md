# API 명세서

## 1. 이벤트 API (Events API)
**기본 URL:** `/events`

### 1.1 일정 생성
- **메서드**: `POST`
- **엔드포인트**: `/`
- **설명**: 새로운 일정을 생성합니다.

**파라미터 (Body)**
| 파라미터명 | 타입 | 필수여부 | 설명 |
| :--- | :--- | :--- | :--- |
| title | String | 필수 | 일정 제목 |
| startDateTime | Date | 필수 | 시작 일시 (ISO 8601) |
| endDateTime | Date | 필수 | 종료 일시 (ISO 8601) |
| description | String | 선택 | 일정 상세 설명 |
| location | String | 선택 | 장소 |
| category | String | 선택 | 카테고리 |

**응답 (Response)**
| 응답 항목 (Response Element) | Depth | 값 구분 (Classification) | 설명 (Description) |
| :--- | :--- | :--- | :--- |
| id | 0 | Integer | 일정 고유 ID |
| title | 0 | String | 일정 제목 |
| description | 0 | String | 일정 상세 설명 |
| startDateTime | 0 | String (Date) | 시작 일시 |
| endDateTime | 0 | String (Date) | 종료 일시 |
| location | 0 | String | 장소 |
| isImportant | 0 | Boolean | 중요 일정 여부 |
| category | 0 | String | 카테고리 |
| importantMemo | 0 | String | 중요 일정 메모 |
| createdAt | 0 | String (Date) | 생성 일시 |
| updatedAt | 0 | String (Date) | 수정 일시 |

**Response Example (JSON)**

**result**:
```json
{
  "id": 1,
  "title": "주일 예배",
  "description": "매주 드리는 청년부 예배",
  "startDateTime": "2025-03-02T02:00:00.000Z",
  "endDateTime": "2025-03-02T03:00:00.000Z",
  "location": "대예배당",
  "category": "예배",
  "isImportant": false,
  "importantMemo": null,
  "createdAt": "2025-03-01T09:00:00.000Z",
  "updatedAt": "2025-03-01T09:00:00.000Z"
}
```

**error**:
```json
{
  "message": "title, startDateTime, endDateTime은 필수입니다."
}
```

---

### 1.2 일정 목록 조회
- **메서드**: `GET`
- **엔드포인트**: `/`
- **설명**: 모든 일정 목록을 조회합니다.

**파라미터 (Query)**
| 파라미터명 | 타입 | 필수여부 | 설명 |
| :--- | :--- | :--- | :--- |
| - | - | - | 별도 필터 파라미터 없음 (전체 조회) |

**응답 (Response)**
| 응답 항목 (Response Element) | Depth | 값 구분 (Classification) | 설명 (Description) |
| :--- | :--- | :--- | :--- |
| - | 0 | Array | 일정 객체 배열 |
| id | 1 | Integer | 일정 고유 ID |
| title | 1 | String | 일정 제목 |
| description | 1 | String | 일정 상세 설명 |
| startDateTime | 1 | String (Date) | 시작 일시 |
| endDateTime | 1 | String (Date) | 종료 일시 |
| location | 1 | String | 장소 |
| isImportant | 1 | Boolean | 중요 일정 여부 |
| category | 1 | String | 카테고리 |
| importantMemo | 1 | String | 중요 일정 메모 |
| createdAt | 1 | String (Date) | 생성 일시 |
| updatedAt | 1 | String (Date) | 수정 일시 |

**Response Example (JSON)**

**result**:
```json
[
  {
    "id": 1,
    "title": "주일 예배",
    "description": "매주 드리는 청년부 예배",
    "startDateTime": "2025-03-02T02:00:00.000Z",
    "endDateTime": "2025-03-02T03:00:00.000Z",
    "location": "대예배당",
    "isImportant": false,
    "category": "예배",
    "importantMemo": null,
    "createdAt": "2025-03-01T09:00:00.000Z",
    "updatedAt": "2025-03-01T09:00:00.000Z"
  },
  {
    "id": 2,
    "title": "팀 주간 회의",
    "description": null,
    "startDateTime": "2025-03-10T05:00:00.000Z",
    "endDateTime": "2025-03-10T06:00:00.000Z",
    "location": "회의실 B",
    "isImportant": false,
    "category": "회의",
    "importantMemo": null,
    "createdAt": "2025-03-08T14:00:00.000Z",
    "updatedAt": "2025-03-08T14:00:00.000Z"
  }
]
```

**error**:
```json
{
  "message": "일정 조회 중 오류가 발생했습니다.",
  "error": "Error details..."
}
```

---

### 1.3 단일 일정 조회
- **메서드**: `GET`
- **엔드포인트**: `/:id`
- **설명**: ID를 이용하여 특정 일정을 조회합니다.

**파라미터 (Path)**
| 파라미터명 | 타입 | 필수여부 | 설명 |
| :--- | :--- | :--- | :--- |
| id | Integer | 필수 | 일정 ID |

**응답 (Response)**
| 응답 항목 (Response Element) | Depth | 값 구분 (Classification) | 설명 (Description) |
| :--- | :--- | :--- | :--- |
| id | 0 | Integer | 일정 고유 ID |
| title | 0 | String | 일정 제목 |
| description | 0 | String | 일정 상세 설명 |
| startDateTime | 0 | String (Date) | 시작 일시 |
| endDateTime | 0 | String (Date) | 종료 일시 |
| location | 0 | String | 장소 |
| isImportant | 0 | Boolean | 중요 일정 여부 |
| category | 0 | String | 카테고리 |
| importantMemo | 0 | String | 중요 일정 메모 |
| createdAt | 0 | String (Date) | 생성 일시 |
| updatedAt | 0 | String (Date) | 수정 일시 |

**Response Example (JSON)**

**result**:
```json
{
  "id": 1,
  "title": "주일 예배",
  "description": "매주 드리는 청년부 예배",
  "startDateTime": "2025-03-02T02:00:00.000Z",
  "endDateTime": "2025-03-02T03:00:00.000Z",
  "location": "대예배당",
  "category": "예배",
  "isImportant": false,
  "importantMemo": null,
  "createdAt": "2025-03-01T09:00:00.000Z",
  "updatedAt": "2025-03-01T09:00:00.000Z"
}
```

**error**:
```json
{
  "message": "일정을 찾을 수 없습니다."
}
```

---

### 1.4 일정 수정
- **메서드**: `PUT`
- **엔드포인트**: `/:id`
- **설명**: 기존 일정을 수정합니다.

**파라미터 (Path)**
| 파라미터명 | 타입 | 필수여부 | 설명 |
| :--- | :--- | :--- | :--- |
| id | Integer | 필수 | 일정 ID |

**파라미터 (Body)**
| 파라미터명 | 타입 | 필수여부 | 설명 |
| :--- | :--- | :--- | :--- |
| title | String | 필수 | 일정 제목 |
| startDateTime | Date | 필수 | 시작 일시 |
| endDateTime | Date | 필수 | 종료 일시 |
| description | String | 선택 | 일정 상세 설명 |
| location | String | 선택 | 장소 |
| category | String | 선택 | 카테고리 |

**응답 (Response)**
| 응답 항목 (Response Element) | Depth | 값 구분 (Classification) | 설명 (Description) |
| :--- | :--- | :--- | :--- |
| id | 0 | Integer | 일정 고유 ID |
| title | 0 | String | 일정 제목 |
| description | 0 | String | 일정 상세 설명 |
| startDateTime | 0 | String (Date) | 시작 일시 |
| endDateTime | 0 | String (Date) | 종료 일시 |
| location | 0 | String | 장소 |
| isImportant | 0 | Boolean | 중요 일정 여부 |
| category | 0 | String | 카테고리 |
| importantMemo | 0 | String | 중요 일정 메모 |
| createdAt | 0 | String (Date) | 생성 일시 |
| updatedAt | 0 | String (Date) | 수정 일시 |

**Response Example (JSON)**

**result**:
```json
{
  "id": 1,
  "title": "주일 예배 (시간 변경)",
  "description": "매주 드리는 청년부 예배",
  "startDateTime": "2025-03-02T02:00:00.000Z",
  "endDateTime": "2025-03-02T03:00:00.000Z",
  "location": "대예배당",
  "category": "예배",
  "isImportant": false,
  "importantMemo": null,
  "createdAt": "2025-03-01T09:00:00.000Z",
  "updatedAt": "2025-03-02T10:00:00.000Z"
}
```

**error**:
```json
{
  "message": "일정을 찾을 수 없습니다."
}
```

---

### 1.5 일정 삭제
- **메서드**: `DELETE`
- **엔드포인트**: `/:id`
- **설명**: 특정 일정을 삭제합니다.

**파라미터 (Path)**
| 파라미터명 | 타입 | 필수여부 | 설명 |
| :--- | :--- | :--- | :--- |
| id | Integer | 필수 | 일정 ID |

**응답 (Response)**
- **Status Code**: `204 No Content`
- **Body**: 없음

**Response Example (JSON)**

**result**:
(No Content)

**error**:
```json
{
  "message": "일정을 찾을 수 없습니다."
}
```

---

## 2. 캘린더 API (Calendar API)
**기본 URL:** `/calendar`

### 2.1 월 단위 일정 조회
- **메서드**: `GET`
- **엔드포인트**: `/month`
- **설명**: 특정 연도와 월에 해당하는 일정을 조회합니다.

**파라미터 (Query)**
| 파라미터명 | 타입 | 필수여부 | 설명 |
| :--- | :--- | :--- | :--- |
| year | Number | 필수 | 조회할 연도 |
| month | Number | 필수 | 조회할 월 |

**응답 (Response)**
| 응답 항목 (Response Element) | Depth | 값 구분 (Classification) | 설명 (Description) |
| :--- | :--- | :--- | :--- |
| - | 0 | Array | 일정 객체 배열 |
| id | 1 | Integer | 일정 고유 ID |
| title | 1 | String | 일정 제목 |
| description | 1 | String | 일정 상세 설명 |
| startDateTime | 1 | String (Date) | 시작 일시 |
| endDateTime | 1 | String (Date) | 종료 일시 |
| location | 1 | String | 장소 |
| isImportant | 1 | Boolean | 중요 일정 여부 |
| category | 1 | String | 카테고리 |
| importantMemo | 1 | String | 중요 일정 메모 |
| createdAt | 1 | String (Date) | 생성 일시 |
| updatedAt | 1 | String (Date) | 수정 일시 |

**Response Example (JSON)**

**result**:
```json
[
  {
    "id": 1,
    "title": "3월 킥오프",
    "description": "3월 프로젝트 시작을 위한 킥오프 미팅",
    "startDateTime": "2025-03-03T09:00:00.000Z",
    "endDateTime": "2025-03-03T10:00:00.000Z",
    "location": "회의실 A",
    "isImportant": true,
    "category": "회의",
    "importantMemo": "필수 참석",
    "createdAt": "2025-02-25T08:00:00.000Z",
    "updatedAt": "2025-02-25T08:00:00.000Z"
  },
  {
    "id": 2,
    "title": "3월 팀 싱크",
    "description": "분기별 팀 싱크",
    "startDateTime": "2025-03-10T05:00:00.000Z",
    "endDateTime": "2025-03-10T06:00:00.000Z",
    "location": "온라인",
    "isImportant": false,
    "category": "회의",
    "importantMemo": null,
    "createdAt": "2025-02-28T11:00:00.000Z",
    "updatedAt": "2025-02-28T11:00:00.000Z"
  },
  {
    "id": 3,
    "title": "3월 마감",
    "description": "월간 보고서 마감일",
    "startDateTime": "2025-03-28T02:00:00.000Z",
    "endDateTime": "2025-03-28T03:00:00.000Z",
    "location": null,
    "isImportant": true,
    "category": "업무",
    "importantMemo": "지연 불가",
    "createdAt": "2025-03-01T09:00:00.000Z",
    "updatedAt": "2025-03-01T09:00:00.000Z"
  }
]
```

**error**:
```json
{
  "message": "year와 month는 필수입니다."
}
```

---

### 2.2 주 단위 일정 조회
- **메서드**: `GET`
- **엔드포인트**: `/week`
- **설명**: 특정 연도, 월, 주차에 해당하는 일정을 조회합니다.

**파라미터 (Query)**
| 파라미터명 | 타입 | 필수여부 | 설명 |
| :--- | :--- | :--- | :--- |
| year | Number | 필수 | 조회할 연도 |
| month | Number | 필수 | 조회할 월 |
| week | Number | 필수 | 조회할 주차 |

**응답 (Response)**
| 응답 항목 (Response Element) | Depth | 값 구분 (Classification) | 설명 (Description) |
| :--- | :--- | :--- | :--- |
| - | 0 | Array | 일정 객체 배열 |
| id | 1 | Integer | 일정 고유 ID |
| title | 1 | String | 일정 제목 |
| description | 1 | String | 일정 상세 설명 |
| startDateTime | 1 | String (Date) | 시작 일시 |
| endDateTime | 1 | String (Date) | 종료 일시 |
| location | 1 | String | 장소 |
| isImportant | 1 | Boolean | 중요 일정 여부 |
| category | 1 | String | 카테고리 |
| importantMemo | 1 | String | 중요 일정 메모 |
| createdAt | 1 | String (Date) | 생성 일시 |
| updatedAt | 1 | String (Date) | 수정 일시 |

**Response Example (JSON)**

**result**:
```json
[
  {
    "id": 2,
    "title": "3월 팀 싱크",
    "description": "분기별 팀 싱크",
    "startDateTime": "2025-03-10T05:00:00.000Z",
    "endDateTime": "2025-03-10T06:00:00.000Z",
    "location": "온라인",
    "isImportant": false,
    "category": "회의",
    "importantMemo": null,
    "createdAt": "2025-02-28T11:00:00.000Z",
    "updatedAt": "2025-02-28T11:00:00.000Z"
  }
]
```

**error**:
```json
{
  "message": "year, month, week는 필수입니다."
}
```

---

### 2.3 일 단위 일정 조회
- **메서드**: `GET`
- **엔드포인트**: `/day`
- **설명**: 특정 날짜의 일정을 조회합니다.

**파라미터 (Query)**
| 파라미터명 | 타입 | 필수여부 | 설명 |
| :--- | :--- | :--- | :--- |
| date | String/Date | 필수 | 조회할 날짜 (YYYY-MM-DD) |

**응답 (Response)**
| 응답 항목 (Response Element) | Depth | 값 구분 (Classification) | 설명 (Description) |
| :--- | :--- | :--- | :--- |
| - | 0 | Array | 일정 객체 배열 |
| id | 1 | Integer | 일정 고유 ID |
| title | 1 | String | 일정 제목 |
| description | 1 | String | 일정 상세 설명 |
| startDateTime | 1 | String (Date) | 시작 일시 |
| endDateTime | 1 | String (Date) | 종료 일시 |
| location | 1 | String | 장소 |
| isImportant | 1 | Boolean | 중요 일정 여부 |
| category | 1 | String | 카테고리 |
| importantMemo | 1 | String | 중요 일정 메모 |
| createdAt | 1 | String (Date) | 생성 일시 |
| updatedAt | 1 | String (Date) | 수정 일시 |

**Response Example (JSON)**

**result**:
```json
[
  {
    "id": 2,
    "title": "3월 팀 싱크",
    "description": "분기별 팀 싱크",
    "startDateTime": "2025-03-10T05:00:00.000Z",
    "endDateTime": "2025-03-10T06:00:00.000Z",
    "location": "온라인",
    "isImportant": false,
    "category": "회의",
    "importantMemo": null,
    "createdAt": "2025-02-28T11:00:00.000Z",
    "updatedAt": "2025-02-28T11:00:00.000Z"
  }
]
```

**error**:
```json
{
  "message": "date 쿼리가 필요합니다."
}
```

---

### 2.4 오늘 일정 조회
- **메서드**: `GET`
- **엔드포인트**: `/today`
- **설명**: 오늘의 일정을 조회합니다.

**파라미터**: 없음

**응답 (Response)**
| 응답 항목 (Response Element) | Depth | 값 구분 (Classification) | 설명 (Description) |
| :--- | :--- | :--- | :--- |
| - | 0 | Array | 일정 객체 배열 |
| id | 1 | Integer | 일정 고유 ID |
| title | 1 | String | 일정 제목 |
| description | 1 | String | 일정 상세 설명 |
| startDateTime | 1 | String (Date) | 시작 일시 |
| endDateTime | 1 | String (Date) | 종료 일시 |
| location | 1 | String | 장소 |
| isImportant | 1 | Boolean | 중요 일정 여부 |
| category | 1 | String | 카테고리 |
| importantMemo | 1 | String | 중요 일정 메모 |
| createdAt | 1 | String (Date) | 생성 일시 |
| updatedAt | 1 | String (Date) | 수정 일시 |

**Response Example (JSON)**

**result**:
```json
[
  {
    "id": 5,
    "title": "오늘의 일정",
    "description": "업무 공유와 금주 일정 안내",
    "startDateTime": "2025-12-07T03:00:00.000Z",
    "endDateTime": "2025-12-07T04:00:00.000Z",
    "location": "회의실 B",
    "isImportant": false,
    "category": "공지",
    "importantMemo": null,
    "createdAt": "2025-12-01T10:00:00.000Z",
    "updatedAt": "2025-12-01T12:00:00.000Z"
  }
]
```

**error**:
```json
{
  "message": "오늘 일정 조회 중 오류가 발생했습니다."
}
```

---

### 2.5 기간 일정 조회
- **메서드**: `GET`
- **엔드포인트**: `/range`
- **설명**: 지정된 기간 내의 일정을 조회합니다.

**파라미터 (Query)**
| 파라미터명 | 타입 | 필수여부 | 설명 |
| :--- | :--- | :--- | :--- |
| startDate | Date | 필수 | 조회 시작일 |
| endDate | Date | 필수 | 조회 종료일 |

**응답 (Response)**
| 응답 항목 (Response Element) | Depth | 값 구분 (Classification) | 설명 (Description) |
| :--- | :--- | :--- | :--- |
| - | 0 | Array | 일정 객체 배열 |
| id | 1 | Integer | 일정 고유 ID |
| title | 1 | String | 일정 제목 |
| description | 1 | String | 일정 상세 설명 |
| startDateTime | 1 | String (Date) | 시작 일시 |
| endDateTime | 1 | String (Date) | 종료 일시 |
| location | 1 | String | 장소 |
| isImportant | 1 | Boolean | 중요 일정 여부 |
| category | 1 | String | 카테고리 |
| importantMemo | 1 | String | 중요 일정 메모 |
| createdAt | 1 | String (Date) | 생성 일시 |
| updatedAt | 1 | String (Date) | 수정 일시 |

**Response Example (JSON)**

**result**:
```json
[
  {
    "id": 1,
    "title": "3월 킥오프",
    "description": "3월 프로젝트 시작을 위한 킥오프 미팅",
    "startDateTime": "2025-03-03T09:00:00.000Z",
    "endDateTime": "2025-03-03T10:00:00.000Z",
    "location": "회의실 A",
    "isImportant": true,
    "category": "회의",
    "importantMemo": "필수 참석",
    "createdAt": "2025-02-25T08:00:00.000Z",
    "updatedAt": "2025-02-25T08:00:00.000Z"
  },
  {
    "id": 2,
    "title": "3월 팀 싱크",
    "description": "분기별 팀 싱크",
    "startDateTime": "2025-03-10T05:00:00.000Z",
    "endDateTime": "2025-03-10T06:00:00.000Z",
    "location": "온라인",
    "isImportant": false,
    "category": "회의",
    "importantMemo": null,
    "createdAt": "2025-02-28T11:00:00.000Z",
    "updatedAt": "2025-02-28T11:00:00.000Z"
  }
]
```

**error**:
```json
{
  "message": "startDate와 endDate가 필요합니다."
}
```

---

## 3. 중요 일정 API (Important API)
**기본 URL:** `/important`

### 3.1 중요 일정 등록
- **메서드**: `POST`
- **엔드포인트**: `/:eventId`
- **설명**: 특정 일정을 중요 일정으로 설정합니다.

**파라미터 (Path)**
| 파라미터명 | 타입 | 필수여부 | 설명 |
| :--- | :--- | :--- | :--- |
| eventId | Integer | 필수 | 일정 ID |

**응답 (Response)**
| 응답 항목 (Response Element) | Depth | 값 구분 (Classification) | 설명 (Description) |
| :--- | :--- | :--- | :--- |
| id | 0 | Integer | 일정 고유 ID |
| title | 0 | String | 일정 제목 |
| description | 0 | String | 일정 상세 설명 |
| startDateTime | 0 | String (Date) | 시작 일시 |
| endDateTime | 0 | String (Date) | 종료 일시 |
| location | 0 | String | 장소 |
| isImportant | 0 | Boolean | 중요 일정 여부 (true) |
| category | 0 | String | 카테고리 |
| importantMemo | 0 | String | 중요 일정 메모 |
| createdAt | 0 | String (Date) | 생성 일시 |
| updatedAt | 0 | String (Date) | 수정 일시 |

**Response Example (JSON)**

**result**:
```json
{
  "id": 1,
  "title": "미래 전략 컨퍼런스",
  "description": "2025년 전략 기획 회의",
  "startDateTime": "2025-04-15T01:00:00.000Z",
  "endDateTime": "2025-04-15T05:00:00.000Z",
  "location": "본사 대회의실",
  "isImportant": true,
  "category": "회의",
  "importantMemo": null,
  "createdAt": "2025-04-01T08:00:00.000Z",
  "updatedAt": "2025-04-10T09:30:00.000Z"
}
```

**error**:
```json
{
  "message": "일정을 찾을 수 없습니다."
}
```

---

### 3.2 중요 일정 해제
- **메서드**: `DELETE`
- **엔드포인트**: `/:eventId`
- **설명**: 중요 일정 설정을 해제합니다.

**파라미터 (Path)**
| 파라미터명 | 타입 | 필수여부 | 설명 |
| :--- | :--- | :--- | :--- |
| eventId | Integer | 필수 | 일정 ID |

**응답 (Response)**
| 응답 항목 (Response Element) | Depth | 값 구분 (Classification) | 설명 (Description) |
| :--- | :--- | :--- | :--- |
| id | 0 | Integer | 일정 고유 ID |
| title | 0 | String | 일정 제목 |
| description | 0 | String | 일정 상세 설명 |
| startDateTime | 0 | String (Date) | 시작 일시 |
| endDateTime | 0 | String (Date) | 종료 일시 |
| location | 0 | String | 장소 |
| isImportant | 0 | Boolean | 중요 일정 여부 (false) |
| category | 0 | String | 카테고리 |
| importantMemo | 0 | String | 중요 일정 메모 |
| createdAt | 0 | String (Date) | 생성 일시 |
| updatedAt | 0 | String (Date) | 수정 일시 |

**Response Example (JSON)**

**result**:
```json
{
  "id": 1,
  "title": "미래 전략 컨퍼런스",
  "description": "2025년 전략 기획 회의",
  "startDateTime": "2025-04-15T01:00:00.000Z",
  "endDateTime": "2025-04-15T05:00:00.000Z",
  "location": "본사 대회의실",
  "isImportant": false,
  "category": "회의",
  "importantMemo": null,
  "createdAt": "2025-04-01T08:00:00.000Z",
  "updatedAt": "2025-04-10T10:00:00.000Z"
}
```

**error**:
```json
{
  "message": "일정을 찾을 수 없습니다."
}
```

---

### 3.3 중요 일정 전체 조회
- **메서드**: `GET`
- **엔드포인트**: `/`
- **설명**: 중요 일정으로 설정된 모든 일정을 조회합니다.

**파라미터**: 없음

**응답 (Response)**
| 응답 항목 (Response Element) | Depth | 값 구분 (Classification) | 설명 (Description) |
| :--- | :--- | :--- | :--- |
| - | 0 | Array | 일정 객체 배열 |
| id | 1 | Integer | 일정 고유 ID |
| title | 1 | String | 일정 제목 |
| description | 1 | String | 일정 상세 설명 |
| startDateTime | 1 | String (Date) | 시작 일시 |
| endDateTime | 1 | String (Date) | 종료 일시 |
| location | 1 | String | 장소 |
| isImportant | 1 | Boolean | 중요 일정 여부 |
| category | 1 | String | 카테고리 |
| importantMemo | 1 | String | 중요 일정 메모 |
| createdAt | 1 | String (Date) | 생성 일시 |
| updatedAt | 1 | String (Date) | 수정 일시 |

**Response Example (JSON)**

**result**:
```json
[
  {
    "id": 1,
    "title": "미래 전략 컨퍼런스",
    "description": "2025년 전략 기획 회의",
    "startDateTime": "2025-04-15T01:00:00.000Z",
    "endDateTime": "2025-04-15T05:00:00.000Z",
    "location": "본사 대회의실",
    "isImportant": true,
    "category": "회의",
    "importantMemo": "발표 자료 준비 필수",
    "createdAt": "2025-04-01T08:00:00.000Z",
    "updatedAt": "2025-04-10T09:30:00.000Z"
  },
  {
    "id": 5,
    "title": "프로젝트 마감",
    "description": "Q1 프로젝트 최종 마감",
    "startDateTime": "2025-03-31T15:00:00.000Z",
    "endDateTime": "2025-03-31T18:00:00.000Z",
    "location": null,
    "isImportant": true,
    "category": "업무",
    "importantMemo": "지연 불가",
    "createdAt": "2025-03-01T10:00:00.000Z",
    "updatedAt": "2025-03-20T11:00:00.000Z"
  }
]
```

**error**:
```json
{
  "message": "중요 일정 조회 중 오류가 발생했습니다."
}
```

---

### 3.4 다가오는 중요 일정 조회
- **메서드**: `GET`
- **엔드포인트**: `/upcoming`
- **설명**: 현재 시점 이후의 중요 일정을 조회합니다.

**파라미터**: 없음

**응답 (Response)**
| 응답 항목 (Response Element) | Depth | 값 구분 (Classification) | 설명 (Description) |
| :--- | :--- | :--- | :--- |
| - | 0 | Array | 일정 객체 배열 |
| id | 1 | Integer | 일정 고유 ID |
| title | 1 | String | 일정 제목 |
| description | 1 | String | 일정 상세 설명 |
| startDateTime | 1 | String (Date) | 시작 일시 |
| endDateTime | 1 | String (Date) | 종료 일시 |
| location | 1 | String | 장소 |
| isImportant | 1 | Boolean | 중요 일정 여부 |
| category | 1 | String | 카테고리 |
| importantMemo | 1 | String | 중요 일정 메모 |
| createdAt | 1 | String (Date) | 생성 일시 |
| updatedAt | 1 | String (Date) | 수정 일시 |

**Response Example (JSON)**

**result**:
```json
[
  {
    "id": 1,
    "title": "미래 전략 컨퍼런스",
    "description": "2025년 전략 기획 회의",
    "startDateTime": "2025-04-15T01:00:00.000Z",
    "endDateTime": "2025-04-15T05:00:00.000Z",
    "location": "본사 대회의실",
    "isImportant": true,
    "category": "회의",
    "importantMemo": "발표 자료 준비 필수",
    "createdAt": "2025-04-01T08:00:00.000Z",
    "updatedAt": "2025-04-10T09:30:00.000Z"
  }
]
```

**error**:
```json
{
  "message": "다가오는 중요 일정 조회 중 오류가 발생했습니다."
}
```

---

### 3.5 중요 일정 메모 수정
- **메서드**: `PATCH`
- **엔드포인트**: `/:eventId/memo`
- **설명**: 중요 일정에 대한 메모를 수정합니다.

**파라미터 (Path)**
| 파라미터명 | 타입 | 필수여부 | 설명 |
| :--- | :--- | :--- | :--- |
| eventId | Integer | 필수 | 일정 ID |

**파라미터 (Body)**
| 파라미터명 | 타입 | 필수여부 | 설명 |
| :--- | :--- | :--- | :--- |
| memo | String | 필수 | 메모 내용 |

**응답 (Response)**
| 응답 항목 (Response Element) | Depth | 값 구분 (Classification) | 설명 (Description) |
| :--- | :--- | :--- | :--- |
| id | 0 | Integer | 일정 고유 ID |
| title | 0 | String | 일정 제목 |
| description | 0 | String | 일정 상세 설명 |
| startDateTime | 0 | String (Date) | 시작 일시 |
| endDateTime | 0 | String (Date) | 종료 일시 |
| location | 0 | String | 장소 |
| isImportant | 0 | Boolean | 중요 일정 여부 |
| category | 0 | String | 카테고리 |
| importantMemo | 0 | String | 중요 일정 메모 |
| createdAt | 0 | String (Date) | 생성 일시 |
| updatedAt | 0 | String (Date) | 수정 일시 |

**Response Example (JSON)**

**result**:
```json
{
  "id": 1,
  "title": "미래 전략 컨퍼런스",
  "description": "2025년 전략 기획 회의",
  "startDateTime": "2025-04-15T01:00:00.000Z",
  "endDateTime": "2025-04-15T05:00:00.000Z",
  "location": "본사 대회의실",
  "isImportant": true,
  "category": "회의",
  "importantMemo": "발표 자료 지참",
  "createdAt": "2025-04-01T08:00:00.000Z",
  "updatedAt": "2025-04-10T10:30:00.000Z"
}
```

**error**:
```json
{
  "message": "memo 는 문자열이어야 합니다."
}
```

---

## 4. 검색 API (Search API)
**기본 URL:** `/search`

### 4.1 키워드 검색
- **메서드**: `GET`
- **엔드포인트**: `/keyword`
- **설명**: 키워드를 포함하는 일정을 검색합니다.

**파라미터 (Query)**
| 파라미터명 | 타입 | 필수여부 | 설명 |
| :--- | :--- | :--- | :--- |
| keyword | String | 필수 | 검색할 키워드 |

**응답 (Response)**
| 응답 항목 (Response Element) | Depth | 값 구분 (Classification) | 설명 (Description) |
| :--- | :--- | :--- | :--- |
| - | 0 | Array | 일정 객체 배열 |
| id | 1 | Integer | 일정 고유 ID |
| title | 1 | String | 일정 제목 |
| description | 1 | String | 일정 상세 설명 |
| startDateTime | 1 | String (Date) | 시작 일시 |
| endDateTime | 1 | String (Date) | 종료 일시 |
| location | 1 | String | 장소 |
| isImportant | 1 | Boolean | 중요 일정 여부 |
| category | 1 | String | 카테고리 |
| importantMemo | 1 | String | 중요 일정 메모 |
| createdAt | 1 | String (Date) | 생성 일시 |
| updatedAt | 1 | String (Date) | 수정 일시 |

**Response Example (JSON)**

**result**:
```json
[
  {
    "id": 1,
    "title": "가족 수련회",
    "description": "전교인 가족 수련회",
    "startDateTime": "2025-05-20T00:00:00.000Z",
    "endDateTime": "2025-05-22T23:59:59.000Z",
    "location": "수양관",
    "isImportant": true,
    "category": "행사",
    "importantMemo": "참가 신청 필수",
    "createdAt": "2025-04-01T09:00:00.000Z",
    "updatedAt": "2025-04-01T09:00:00.000Z"
  }
]
```

**error**:
```json
{
  "message": "keyword 파라미터가 필요합니다."
}
```

---

### 4.2 제목 검색
- **메서드**: `GET`
- **엔드포인트**: `/name`
- **설명**: 제목이 일치하거나 포함되는 일정을 검색합니다.

**파라미터 (Query)**
| 파라미터명 | 타입 | 필수여부 | 설명 |
| :--- | :--- | :--- | :--- |
| title | String | 필수 | 검색할 제목 |

**응답 (Response)**
| 응답 항목 (Response Element) | Depth | 값 구분 (Classification) | 설명 (Description) |
| :--- | :--- | :--- | :--- |
| - | 0 | Array | 일정 객체 배열 |
| id | 1 | Integer | 일정 고유 ID |
| title | 1 | String | 일정 제목 |
| description | 1 | String | 일정 상세 설명 |
| startDateTime | 1 | String (Date) | 시작 일시 |
| endDateTime | 1 | String (Date) | 종료 일시 |
| location | 1 | String | 장소 |
| isImportant | 1 | Boolean | 중요 일정 여부 |
| category | 1 | String | 카테고리 |
| importantMemo | 1 | String | 중요 일정 메모 |
| createdAt | 1 | String (Date) | 생성 일시 |
| updatedAt | 1 | String (Date) | 수정 일시 |

**Response Example (JSON)**

**result**:
```json
[
  {
    "id": 2,
    "title": "성가대 연습",
    "description": "저녁 연습",
    "startDateTime": "2025-03-05T10:00:00.000Z",
    "endDateTime": "2025-03-05T12:00:00.000Z",
    "location": "음악실",
    "isImportant": false,
    "category": "연습",
    "importantMemo": null,
    "createdAt": "2025-03-01T08:30:00.000Z",
    "updatedAt": "2025-03-01T08:30:00.000Z"
  }
]
```

**error**:
```json
{
  "message": "title 파라미터가 필요합니다."
}
```

---

### 4.3 날짜 검색
- **메서드**: `GET`
- **엔드포인트**: `/date`
- **설명**: 특정 날짜의 일정을 검색합니다.

**파라미터 (Query)**
| 파라미터명 | 타입 | 필수여부 | 설명 |
| :--- | :--- | :--- | :--- |
| date | String/Date | 필수 | 검색할 날짜 |

**응답 (Response)**
| 응답 항목 (Response Element) | Depth | 값 구분 (Classification) | 설명 (Description) |
| :--- | :--- | :--- | :--- |
| - | 0 | Array | 일정 객체 배열 |
| id | 1 | Integer | 일정 고유 ID |
| title | 1 | String | 일정 제목 |
| description | 1 | String | 일정 상세 설명 |
| startDateTime | 1 | String (Date) | 시작 일시 |
| endDateTime | 1 | String (Date) | 종료 일시 |
| location | 1 | String | 장소 |
| isImportant | 1 | Boolean | 중요 일정 여부 |
| category | 1 | String | 카테고리 |
| importantMemo | 1 | String | 중요 일정 메모 |
| createdAt | 1 | String (Date) | 생성 일시 |
| updatedAt | 1 | String (Date) | 수정 일시 |

**Response Example (JSON)**

**result**:
```json
[
  {
    "id": 2,
    "title": "성가대 연습",
    "description": "저녁 연습",
    "startDateTime": "2025-05-03T19:00:00.000Z",
    "endDateTime": "2025-05-03T21:00:00.000Z",
    "location": "음악실",
    "isImportant": false,
    "category": "연습",
    "importantMemo": null,
    "createdAt": "2025-05-01T08:30:00.000Z",
    "updatedAt": "2025-05-01T08:30:00.000Z"
  }
]
```

**error**:
```json
{
  "message": "date 파라미터가 필요합니다."
}
```

---

### 4.4 기간 검색
- **메서드**: `GET`
- **엔드포인트**: `/period`
- **설명**: 특정 기간 내의 일정을 검색합니다.

**파라미터 (Query)**
| 파라미터명 | 타입 | 필수여부 | 설명 |
| :--- | :--- | :--- | :--- |
| startDate | Date | 필수 | 검색 시작일 |
| endDate | Date | 필수 | 검색 종료일 |

**응답 (Response)**
| 응답 항목 (Response Element) | Depth | 값 구분 (Classification) | 설명 (Description) |
| :--- | :--- | :--- | :--- |
| - | 0 | Array | 일정 객체 배열 |
| id | 1 | Integer | 일정 고유 ID |
| title | 1 | String | 일정 제목 |
| description | 1 | String | 일정 상세 설명 |
| startDateTime | 1 | String (Date) | 시작 일시 |
| endDateTime | 1 | String (Date) | 종료 일시 |
| location | 1 | String | 장소 |
| isImportant | 1 | Boolean | 중요 일정 여부 |
| category | 1 | String | 카테고리 |
| importantMemo | 1 | String | 중요 일정 메모 |
| createdAt | 1 | String (Date) | 생성 일시 |
| updatedAt | 1 | String (Date) | 수정 일시 |

**Response Example (JSON)**

**result**:
```json
[
  {
    "id": 2,
    "title": "성가대 연습",
    "description": "저녁 연습",
    "startDateTime": "2025-05-03T19:00:00.000Z",
    "endDateTime": "2025-05-03T21:00:00.000Z",
    "location": "음악실",
    "isImportant": false,
    "category": "연습",
    "importantMemo": null,
    "createdAt": "2025-05-01T08:30:00.000Z",
    "updatedAt": "2025-05-01T08:30:00.000Z"
  },
  {
    "id": 3,
    "title": "운영위원회 회의",
    "description": "월례 운영위원회",
    "startDateTime": "2025-05-10T06:00:00.000Z",
    "endDateTime": "2025-05-10T08:00:00.000Z",
    "location": "교육관 2층",
    "isImportant": true,
    "category": "회의",
    "importantMemo": "안건 사전 검토",
    "createdAt": "2025-04-25T09:00:00.000Z",
    "updatedAt": "2025-04-25T09:00:00.000Z"
  },
  {
    "id": 4,
    "title": "성경 공부",
    "description": "신약 성경 스터디",
    "startDateTime": "2025-05-15T11:00:00.000Z",
    "endDateTime": "2025-05-15T13:00:00.000Z",
    "location": "소그룹실",
    "isImportant": false,
    "category": "교육",
    "importantMemo": null,
    "createdAt": "2025-05-01T10:00:00.000Z",
    "updatedAt": "2025-05-01T10:00:00.000Z"
  }
]
```

**error**:
```json
{
  "message": "startDate와 endDate 파라미터가 필요합니다."
}
```

### 4.5 최근 일정 조회
- **메서드**: `GET`
- **엔드포인트**: `/recent`
- **설명**: 최근에 생성된 일정을 조회합니다.

**파라미터 (Query)**
| 파라미터명 | 타입 | 필수여부 | 설명 |
| :--- | :--- | :--- | :--- |
| limit | Number | 선택 | 조회할 개수 (기본값: 5) |

**응답 (Response)**
| 응답 항목 (Response Element) | Depth | 값 구분 (Classification) | 설명 (Description) |
| :--- | :--- | :--- | :--- |
| - | 0 | Array | 일정 객체 배열 |
| id | 1 | Integer | 일정 고유 ID |
| title | 1 | String | 일정 제목 |
| description | 1 | String | 일정 상세 설명 |
| startDateTime | 1 | String (Date) | 시작 일시 |
| endDateTime | 1 | String (Date) | 종료 일시 |
| location | 1 | String | 장소 |
| isImportant | 1 | Boolean | 중요 일정 여부 |
| category | 1 | String | 카테고리 |
| importantMemo | 1 | String | 중요 일정 메모 |
| createdAt | 1 | String (Date) | 생성 일시 |
| updatedAt | 1 | String (Date) | 수정 일시 |

**Response Example (JSON)**

**result**:
```json
[
  {
    "id": 10,
    "title": "신규 프로젝트 착수",
    "description": "Q2 신규 프로젝트 시작",
    "startDateTime": "2025-04-01T01:00:00.000Z",
    "endDateTime": "2025-04-01T03:00:00.000Z",
    "location": "회의실 A",
    "isImportant": true,
    "category": "업무",
    "importantMemo": "팀원 전원 참석",
    "createdAt": "2025-03-28T15:00:00.000Z",
    "updatedAt": "2025-03-28T15:00:00.000Z"
  },
  {
    "id": 9,
    "title": "월간 보고",
    "description": "3월 실적 보고",
    "startDateTime": "2025-03-31T07:00:00.000Z",
    "endDateTime": "2025-03-31T09:00:00.000Z",
    "location": "임원실",
    "isImportant": false,
    "category": "보고",
    "importantMemo": null,
    "createdAt": "2025-03-27T10:00:00.000Z",
    "updatedAt": "2025-03-27T10:00:00.000Z"
  },
  {
    "id": 8,
    "title": "팀 빌딩",
    "description": "팀 친목 활동",
    "startDateTime": "2025-03-29T08:00:00.000Z",
    "endDateTime": "2025-03-29T17:00:00.000Z",
    "location": "야외",
    "isImportant": false,
    "category": "행사",
    "importantMemo": null,
    "createdAt": "2025-03-26T14:00:00.000Z",
    "updatedAt": "2025-03-26T14:00:00.000Z"
  }
]
```

**error**:
```json
{
  "message": "최근 일정 조회 중 오류가 발생했습니다."
}
```
