# Event Service 모듈화


## 🏗️ 모듈 구조

```
src/services/
├── event.service.js          ← 모든 모듈을 통합하는 메인 파일
└── modules/
    ├── dateRange.js          ← 날짜 범위 필터 유틸리티
    ├── crud.js               ← CRUD 작업 (생성, 조회, 수정, 삭제)
    ├── calendar.js           ← 캘린더 조회 (월, 주, 일, 기간)
    ├── important.js          ← 중요 일정 관리
    └── search.js             ← 검색 기능 (키워드, 제목, 날짜, 기간, 최근)
```

---

## 📦 각 모듈의 역할

### 1️⃣ **dateRange.js** (유틸리티)
```javascript
buildDateRangeWhere(start, end)
```
- **역할**: 시작일과 종료일 사이의 이벤트 필터 조건 생성
- **사용처**: calendar, crud, search 모듈에서 공통으로 사용
- **반환**: Sequelize의 Op 조건 객체

---

### 2️⃣ **crud.js** (CRUD 작업)
```javascript
createEvent(payload)           // 일정 생성
getEvents(filters)             // 일정 목록 조회 (필터 포함)
getEventById(id)               // 단일 일정 조회
updateEvent(id, payload)       // 일정 수정
deleteEvent(id)                // 일정 삭제
```

**특징**:
- 기본적인 CRUD 작업 담당
- dateRange 유틸 활용
- 5개 함수 포함

---

### 3️⃣ **calendar.js** (시간 단위 조회)
```javascript
getEventsByMonth(year, month)       // 월별 일정
getEventsByWeek(year, month, week)  // 주별 일정
getEventsByDay(dateStr)             // 일별 일정
getEventsForToday()                 // 오늘 일정
getEventsByRange(startDate, endDate) // 기간별 일정
```

**특징**:
- 다양한 시간 단위의 일정 조회
- dateRange 유틸 활용
- 5개 함수 포함

---

### 4️⃣ **important.js** (중요 일정 관리)
```javascript
markEventAsImportant(eventId)           // 중요 표시
unmarkEventAsImportant(eventId)         // 중요 해제
getImportantEvents()                    // 중요 일정 조회
getUpcomingImportantEvents()            // 다가오는 중요 일정
updateImportantMemo(eventId, memo)      // 메모 수정
```

**특징**:
- 중요 일정의 관리와 조회
- 메모 기능 포함
- 5개 함수 포함

---

### 5️⃣ **search.js** (검색 기능)
```javascript
searchEventsByKeyword(keyword)     // 키워드 검색
searchEventsByTitle(title)         // 제목 검색
searchEventsByDate(dateStr)        // 날짜 검색
searchEventsByPeriod(startDate, endDate) // 기간 검색
getRecentEvents(limit)             // 최근 일정 조회
```

**특징**:
- 다양한 조건의 검색
- calendar 모듈 활용 (searchEventsByDate, searchEventsByPeriod)
- 5개 함수 포함

---

## 🔄 흐름도

### 컨트롤러에서의 사용

```
컨트롤러
  ↓
require('../services/event.service')
  ↓
event.service.js (모든 모듈 통합)
  ↓ (spread operator로 병합)
┌─────────────────────────────────┐
│ dateRange (유틸)                │
│ crud (5개 함수)                 │
│ calendar (5개 함수)             │
│ important (5개 함수)            │
│ search (5개 함수)               │
└─────────────────────────────────┘
  ↓
실제 함수 호출
```

---



## 📊 함수 분포

| 모듈 | 함수 개수 | 기능 |
|------|---------|------|
| dateRange | 1 | 유틸리티 |
| crud | 5 | CRUD 작업 |
| calendar | 5 | 시간 단위 조회 |
| important | 5 | 중요 일정 관리 |
| search | 5 | 검색 기능 |
| **합계** | **21** | **모든 기능** |

---
