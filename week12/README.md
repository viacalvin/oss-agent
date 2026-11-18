# boxoffice — KOBIS 박스오피스 조회 스킬

## 하는 일
특정 날짜의 박스오피스 1위 영화나 그 영화의 관객 수를 물어보면 영화진흥회(KOBIS) 일별 박스오피스를 조회하여 답한다

## 들어 있는 파일
- .claude/skills/boxoffice/SKILL.md
- .claude/skills/boxoffice/scripts/boxoffice.py
- .claude/skills/boxoffice/LICENSE

## 필요한 것
tools.py, secret.py 파일과 python3, requests 패키지가 필요하다

## 설치
week12/.claude/skills/boxoffice에 두고 week12 밑에는 tools.py가 있어야 한다. 또 처음 스크립트를 실행할 때 권한 허용을 해야한다

## 바깥으로 요청하는 곳
(https://www.kobis.or.kr)

## 키
"자기 키를 secret.py 에 넣을 것"

## 권한
allowed-tools는 없고 스킬을 부를 때 스킬을 사용해도 되는지 한번 물어봄

## 라이선스
MIT-LICENSE이고 파일위치는 week12/.claude/skills/boxoffice/LICENSE.txt 이다
