#GitHub 시작하기

##기본 용어
**Branch** : 작업자들은 메인 프로젝트의 브랜치를 따와서(branch off), 자신이 변경하고 싶은 자신만의 버전을 만든다. 작업을 끝낸 후, 프로젝트의 메인 디렉토리인 "master"에 브랜치를 다시 "Merge"한다.


##주요 명령어
**git init**: 깃 저장소를 초기화한다. 저장소나 디렉토리 안에서 이 명령을 실행하기 전까지는 그냥 일반 폴더이다. 이것을 입력한 후에야 추가적인 깃 명령어들을 줄 수 있다.

**git config**: “configure”의 준말, 처음에 깃을 설정할 때 가장 유용하다.

**git help**: 명령어를 잊어버렸다? 커맨드 라인에 이걸 타이핑하면 21개의 가장 많이 사용하는 깃 명령어들이 나타난다. 좀 더 자세하게 “git help init”이나 다른 용어를 타이핑하여 특정 깃 명령어를 사용하고 설정하는 법을 이해할 수도 있다.

**git status**: 저장소 상태를 체크. 어떤 화일이 저장소 안에 있는지, 커밋이 필요한 변경사항이 있는지, 현재 저장소의 어떤 브랜치에서 작업하고 있는지 등을 볼 수 있다.

**git add**: 이 명령이 저장소에 새 화일들을 추가하진 않는다. 대신, 깃이 새 화일들을 지켜보게 한다. 화일을 추가하면, 깃의 저장소 “스냅샷”에 포함된다.

**git commit**: 깃의 가장 중요한 명령어. 어떤 변경사항이라도 만든 후, 저장소의 “스냅샷”을 찍기 위해 이것을 입력한다. 보통 “git commit -m “Message hear.” 형식으로 사용한다. -m은 명령어의 그 다음 부분을 메시지로 읽어야 한다는 것을 말한다.

**git branch**: 여러 협업자와 작업하고 자신만의 변경을 원한다? 이 명령어는 새로운 브랜치를 만들고, 자신만의 변경사항과 화일 추가 등의 커밋 타임라인을 만든다. 당신의 제목이 명령어 다음에 온다. 새 브랜치를 “cats”로 부르고 싶으면, git branch cats를 타이핑한다.

**git checkout**: 글자 그대로, 현재 위치하고 있지 않은 저장소를 “체크아웃”할 수 있다. 이것은 체크하길 원하는 저장소로 옮겨가게 해주는 탐색 명령이다. master 브랜치를 들여다 보고 싶으면, git checkout master를 사용할 수 있고, git checkout cats로 또 다른 브랜치를 들여다 볼 수 있다.

**git merge**: 브랜치에서 작업을 끝내고, 모든 협업자가 볼 수 있는 master 브랜치로 병합할 수 있다. git merge cats는 “cats” 브랜치에서 만든 모든 변경사항을 master로 추가한다.

**git push**: 로컬 컴퓨터에서 작업하고 당신의 커밋을 깃허브에서 온라인으로도 볼 수 있기를 원한다면, 이 명령어로 깃허브에 변경사항을 “push”한다.

**git pull**: 로컬 컴퓨터에서 작업할 때, 작업하고 있는 저장소의 최신 버전을 원하면, 이 명령어로 깃허브로부터 변경사항을 다운로드한다(“pull”).


##Repository 연결
리모트 저장소가 있는지 확인하거나 저장소 이름 확인
대부분 origin을 사용하는데, 원하는 이름으로도 가능
`$ git remote`

#####Repository 연결하기
```
# git remote add origin <repo 주소>
$ git remote add origin https://github.com/hygeim/nktest.git
```

#####하나의 로컬저장소에 Repository 여러 개 연결하기
등록 시, Repository의 이름을 다르게 해준다. 그리고 push할 때 Repository의 이름을 구분하여 버전 관리를 해준다.
```
$ git remote add second https://github.com/hygeim/something.git
$ git push origin master
$ git push second master
```


#####Repository 연결 확인하기
`-v` 옵션을 통해 연결한 repository의 상태 체크를 할 수 있다.
```
$ git remote -v
origin https://~~.git (fetch)
origin https://~~.git (push)
```
*fetch*는 파일을 불러오는 저장소, *push*는 파일을 저장하는 저장소를 의미한다.



- - -
출처: https://juliahwang.kr/gitstudy/2017/10/04/%EB%A6%AC%EB%AA%A8%ED%8A%B8%EC%A0%80%EC%9E%A5%EC%86%8C.html
https://nolboo.kim/blog/2013/10/06/github-for-beginner/
