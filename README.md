# git_guidebook

- 목차

     0. 깃허브 사용법

    1. GitFlow
    2. Rebase Rule
    3. Commit Message
    4. 참조 

    [https://www.notion.so/Github-ad0da218b4a74e62bce9b06d9fb1d875](https://www.notion.so/Github-ad0da218b4a74e62bce9b06d9fb1d875)

    [https://rogerdudler.github.io/git-guide/index.ko.html](https://rogerdudler.github.io/git-guide/index.ko.html)

# 0. 깃허브 사용법

# STEP1. git 설치

- [https://gitforwindows.org/](https://gitforwindows.org/)
- git bash를 실행시켜라
- git 원격 주소와 연결시킬 폴더를 생성하고
- git init                                 명령어로 해당 폴더를 git 연동 폴더로
- git clone 사용자명@호스트:/원격/저장소/경로    명령어로 해당 폴더를 git과 연동시킵니다.

팁 : git —help명령어로 명령어 힌트를 전달받을 수 있습니다.

# STEP2. git 업로드의 과정

- push 과정에 대해서 서술합니다. 연동한 원격 저장소로 내 로컬 저장소의 파일을 업로드하는 과정입니다.

현재 로컬 작업폴더 > **git add** > commit적기 > **push** > branch > **pull request** > master

>>>>>작업폴더>>>>stage>>head(log)>>>>>>>>>>>> 작업 파일이 올라가는 순서 단계입니다.

![1](https://user-images.githubusercontent.com/41600359/149460713-3878784c-9e2d-4129-a447-cbc3cdcc36b0.PNG)

---

---

git bash에서 해야할 작업은 3단계 까지 입니다. 

총 4단계가 필요한데, 

1. add 
2. commit
3. push branch
4. pull request  < 4단계는 github 사이트 가서 버튼 누르는 거라 step2에서는 생략합니다.

## 2-1. add, status

![2](https://user-images.githubusercontent.com/41600359/149460769-cf8c32a5-8196-4781-b683-c07fc6e1bcc0.PNG)
- git 연동폴더에 수정 업데이트된 파일이 발생했다면
- git status                   명령어로 (빨간글씨) 변경상황 확인이 가능합니다.
- git add 파일명          명령어로 stage라는 임시 메모리에  현재 상황을 올려 둡니다. (사이트 업로드 아직 안됨)
- git reset HEAD~1     명령어로 add 실행 취소 할 수 있다.
- git reset                    명령어로 전체취소

![3](https://user-images.githubusercontent.com/41600359/149460785-167aa69d-7c9a-4fa8-ac0e-fc9d55078992.PNG)
- 빨간 글씨는 메모리에 올리는 걸 실패했다는 뜻이다
- 초록 글씨만 올라간다.

## 2-2. branch

- 허나 바로 원격저장소의 master(main) 폴더에 업로드 하면 안된다. 수정하기 어려워지기 때문 완전 무결할 때만 master로 가야한다. 지금처럼 개발 상태는 branch로 보내주어야한다.

![4](https://user-images.githubusercontent.com/41600359/149460788-7c9d9ac4-9085-4f3c-bd52-362c5dc6ef48.PNG)
- git branch                       명령어는 현재 가지치기 상태를 보여준다.
- git branch 브랜치명       명령어는 원격저장소에 직접 브랜치를 생성해준다.
- git checkout 브랜치명    명령어로 브랜치를 이동해서 작업할 수 있다.

![5](https://user-images.githubusercontent.com/41600359/149460789-da6c7fc1-1d93-40d9-8fea-77a9744e2d10.PNG)
# STEP3. commit push

## 3-1. commit

- git commit -m "commit message"       명령어로 커밋 명령어를 작성할 수 있다.

## 3-2. push

- git push origin 브랜치명                    명령어로 드디어 올린다.

 

# 1. GitFlow

- Master Branch는 최종 확정된 버전만 있습니다. = 릴리즈 버전
- PR 요청 시 Part 장 혹은 전체 리뷰를 거쳐 함

![6](https://user-images.githubusercontent.com/41600359/149460783-85209c20-b470-41ea-a86a-9c4190aabc45.PNG)

i) Part 장만 PR하는 경우

- Function 개발이 끝났고, 해당 branch를 Part로 요청할 때
- Hotfix 와 같이 긴급한 사안의 경우

ii) 전체리뷰를 진행하는 경우

- Part개발이 끝나고, Staging으로 PR요청 시 전체 개발팀에게 리뷰진행
- Staging에서 version을 올리려 master로 PR을 요청 시 개발팀 전체미팅

# 2. Rebase Rule

1. Function → Part
    - Squash and Merge 방식 사용
2. Part → Staging
    - Rebase and Merge 방식 사용
3. Staging → Master
    - Rebase and Merge 방식 사용
4. Hotfix → Master
    - Merge || Squash and Merge 방식중 택 1

ref. [https://meetup.toast.com/posts/122](https://meetup.toast.com/posts/122)

---

# 3. Commit Message

영어를 기본으로 합니다!

1. 제목과 본문사이엔 1 blank line
2. Max_length = 50
3. 제목의 첫글자는 대문자로, 그리고 제목의 마지막에 `.` 금지!
4. 제목은 명령조로
5. 본문에서 line 별 max_length는 72
6. 본문에 표현해야 할 점은 `무엇을`, `왜` 에 집중
