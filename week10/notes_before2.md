# week09/tools.py 함수 설명

## 파일 개요

`tools.py`는 영화진흥위원회(KOBIS) 오픈 API를 호출해 박스오피스 정보를 가져오는 도구 모음이다.

- `requests` 라이브러리로 HTTP 요청을 보낸다.
- API 키는 `secret.py`에 정의된 `API_KEY`를 불러와 쓴다.
- `BASE_URL`은 KOBIS의 일별 박스오피스 조회 주소(`searchDailyBoxOfficeList.json`)다.

현재 파일에 정의된 함수는 **1개**다.

## `get_boxoffice_rank_1(date)`

주어진 날짜의 일별 박스오피스 **1위 영화 제목**을 알려준다.

| 항목 | 설명 |
|------|------|
| 매개변수 | `date` (문자열): 8자리 날짜, 예: `"20260824"` |
| 반환값 | (문자열) 1위 영화 제목, 예: `"오디세이"` |

### 동작 방식

1. 요청 파라미터로 `key`(API 키)와 `targetDt`(조회 날짜)를 만든다.
2. `requests.get(BASE_URL, params=params, timeout=10)`으로 API를 호출한다. 응답을 최대 10초까지 기다린다.
3. 응답을 JSON으로 바꾼 뒤 `data['boxOfficeResult']['dailyBoxOfficeList']`에서 순위 목록을 꺼낸다.
4. 목록의 첫 번째 영화(`movies[0]`)의 제목(`movieNm`)을 반환한다.

### 사용 예

```python
from tools import get_boxoffice_rank_1

print(get_boxoffice_rank_1("20260824"))  # 예: 오디세이
```

### 참고할 점

- 1위 영화의 제목만 돌려준다. 2위 이하 순위나 관객 수, 개봉일 같은 정보는 가져오지 않는다.
- 예외 처리가 없다. 네트워크 오류, 잘못된 API 키나 날짜 형식, 빈 결과 목록이면 `requests` 예외, `KeyError`, `IndexError` 같은 오류가 그대로 발생한다.
