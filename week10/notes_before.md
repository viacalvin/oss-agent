# week09/tools.py 함수 정리

## 개요

`tools.py`는 영화진흥위원회(KOBIS) 오픈 API로 박스오피스 정보를 가져오는 도구 모음이다.

- 사용 라이브러리: `requests`
- API 키: `secret.py`의 `API_KEY`에서 가져온다
- 요청 주소(`BASE_URL`): KOBIS 일별 박스오피스 조회 API (`searchDailyBoxOfficeList.json`)

## 함수 목록

### `get_boxoffice_rank_1(date)`

지정한 날짜의 일별 박스오피스 **1위 영화 제목**을 돌려준다.

| 구분 | 내용 |
|------|------|
| 받는 것 | `date` (문자열): 8자리 날짜. 예: `"20260824"` |
| 돌려주는 것 | (문자열) 1위 영화 제목. 예: `"오디세이"` |

**동작 순서**

1. `key`(API 키)와 `targetDt`(날짜)를 요청 파라미터로 만든다.
2. `requests.get`으로 `BASE_URL`에 요청을 보낸다. 제한 시간은 10초다.
3. 응답 JSON에서 `boxOfficeResult` → `dailyBoxOfficeList`(순위 목록)를 꺼낸다.
4. 목록의 첫 번째 항목(`movies[0]`)에서 영화 제목 `movieNm`을 돌려준다.

**참고 (현재 코드의 한계)**

- 1위만 돌려주며, 다른 순위나 관객 수 같은 정보는 다루지 않는다.
- 오류 처리가 없다. 날짜 형식이 틀렸거나 결과 목록이 비어 있거나 네트워크 오류가 나면 예외(`KeyError`, `IndexError`, `requests` 예외 등)가 그대로 발생한다.
