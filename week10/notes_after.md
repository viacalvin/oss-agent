작성: Claude Code / 확인: 박지환

# week09/tools.py 함수 정리

## 개요

- 영화진흥위원회(KOBIS) 오픈 API로 박스오피스 정보를 가져오는 도구 모음임
- 사용 라이브러리: `requests`
- API 키: `secret.py`의 `API_KEY`를 가져와 씀
- 요청 주소(`BASE_URL`): KOBIS 일별 박스오피스 조회 API (`searchDailyBoxOfficeList.json`)
- 들어 있는 함수: `get_boxoffice_rank_1` 1개임

## 함수 목록

### `get_boxoffice_rank_1(date)`

- 역할: 지정한 날짜의 일별 박스오피스 **1위 영화 제목**을 돌려줌
- 받는 것: `date` (문자열) — 8자리 날짜. 예: `"20260824"`
- 돌려주는 것: (문자열) 1위 영화 제목. 예: `"오디세이"`

**동작 순서**

1. `key`(API 키)와 `targetDt`(날짜)로 요청 파라미터를 만듦
2. `requests.get`으로 `BASE_URL`에 요청을 보냄 (제한 시간 10초)
3. 응답 JSON에서 `boxOfficeResult` → `dailyBoxOfficeList`(순위 목록)를 꺼냄
4. 목록의 첫 번째 항목(`movies[0]`)의 영화 제목 `movieNm`을 돌려줌

**참고 (현재 코드의 한계)**

- 1위 제목만 돌려줌. 다른 순위나 관객 수 등은 다루지 않음
- 오류 처리가 없음. 날짜 형식 오류, 빈 결과 목록, 네트워크 오류 시 예외(`KeyError`, `IndexError`, `requests` 예외 등)가 그대로 발생함

## 요약

- tools.py는 KOBIS API로 박스오피스 정보를 가져오는 도구 모음임
- 함수는 `get_boxoffice_rank_1(date)` 1개이며, 8자리 날짜를 받아 그날 1위 영화 제목을 돌려줌
- 오류 처리가 없어 잘못된 입력이나 네트워크 오류 시 예외가 그대로 발생함
