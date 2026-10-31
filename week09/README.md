# week09 - 박스오피스 1위 영화 조회

## 무엇을 하는 코드인가
영화진흥위원회(KOBIS) 오픈 API를 이용해, 날짜(예: `20260824`)를 넣으면 그날 박스오피스 1위 영화 제목을 알려줍니다.

## 설치
```
pip install -r requirements.txt
```
그리고 `week09` 폴더에 `secret.py`를 만들어 KOBIS API 키를 넣습니다. (이 파일은 git에 올라가지 않습니다)
```python
API_KEY = "발급받은_키"
```

## 실행
```
cd week09
python main.py
```
