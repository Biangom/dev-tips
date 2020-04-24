##### 약속

-   HEAD는 현재 커밋ID를 가리킴
-   HEAD^ 현재보다 한단계 전 커밋ID
-   ORIG\_HEAD

##### 복구

-   git add 한거 다시 취소하기 (staged 파일을 unstaged 로 만들기)  
    `git reset HEAD [파일이름]`
    
-   git reset으로 커밋 이동 후 다시 원하는 커밋으로 복구하고 싶을 때
    
    `git reflog` 입력 후 원하는 커밋 아이디를 찾는다.  
    `git reset [해당 커밋 ID]`
    
-   가장 최근의 branch로 커밋하고 싶을 때  
    `git reset HEAD`
    
-   현재 수정내용 그대로 두고 해당 커밋 아이디로 갈 때.  
    상황. working tree(작업 공간)은 그대로 두고 커밋 ID만 이동시켜서 현재 변경사항을 과거 커밋ID에 적용 시키고 싶을 때  
    상황. 작업 내용을 보존하고 해당 커밋으로 이동하고 싶을 때  
    상황. 해당 커밋 ID로 다 돌리는데 index에 있던 내용(add했던 파일들, staged한 내용)도 unstaged로 만들어버리고 싶을 때.  
    `git reset [커밋ID]` 사실 --mixed 옵션이 생략된 것.
    
-   현재 working tree 수정내용을 그대로 두는데 add 했던 파일들 상태도 살리고 싶을 때 (index tree에 있는 내용들, staged한 내용들)  
    `git reset --soft [커밋ID]`
    
-   현재 working tree의 수정내용, add한 내용들을 다 무시하고 (다버리고) 해당 커밋상태로 돌아가고 싶을 때  
    `git reset --hard [커밋ID]`
    

##### 삭제

-   가장 최근의 branch로 이동 후 unstaged, staged된 내용 다 삭제하고 싶을 때 (untracked파일, 새로 생성된파일들은 삭제 못함)
    
    `git reset HEAD`
    
    `git checkout .`(git checkout \[파일이름\] 하면 그 파일 변경사항만 없어짐)
    

##### 적용

-   다른 commit 불러와서 현재 branch에 적용시키기 (cherry-pick)
    
    `git cherry-pick [커밋 ID]`
    
-   이전 커밋 내용을 취소하고, 다시 커밋하고 싶을 때.  
    `git reset --soft HEAD^`  
    수정다한 뒤  
    `git commit -a -c ORIG_HEAD`
    
-   수정사항을 현재 커밋에 적용 시키고 싶을 때  
    `git commit --amend`
    

##### 검색

-   현재 폴더의 소스 전체에서 해당 키워드 내용 들어있는지 검색  
    `git grep [검색하고싶은 내용]`
    
-   해당 파일을 라인 by 라인으로 어떤 변경사항이 있었는지 커밋ID로 볼 수 있게함  
    `git blame [해당 파일명 (경로까지)]`
    
-   현재커밋과 이전커밋의 변경된 파일만 보기 [새로운커밋]을 생략하면 HEAD와 비교 (내용X)    
    `git diff --name-status [나중커밋] [새로운커밋]`
    
-   현재커밋과 이전커밋의 변경된 파일 추출하기     
    `git archive -o test.zip HEAD $(git diff --name-only HEAD^)`
    
참고  
[https://git-scm.com/book/ko/v2/Git%EC%9D%98-%EB%82%B4%EB%B6%80-Git-Refs](https://git-scm.com/book/ko/v2/Git%EC%9D%98-%EB%82%B4%EB%B6%80-Git-Refs)

https://lovemewithoutall.github.io/it/git-diff-name-status/


staged = index에 등록
unstage = index에 등록되어있지 않음.
