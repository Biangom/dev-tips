# 상황별 git 명령어 정리
- 가장 최근의 브랜치로 커밋하고 싶을 때
  - git reset HEAD
- 가장 최근의 브랜치로 이동 후 unstaged, staged된 파일 다 삭제하고 싶을 때
  - git reset HEAD
  - git checkout .   (git checkout [파일이름] 하면 그 파일 변경사항 없어짐)
- 다른 commit 불러오기 (cherry-pick)
  - git cherry-pick [커밋 ID]

staged = index에 등록
unstage = index에 등록되어있지 않음.
