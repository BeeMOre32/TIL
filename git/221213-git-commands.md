# About git Commands

버젼 관리 시스템인 git 은 여러가지 명령어들이 있는데 간단하게 알아보았다.

`$ git add example.txt`

example.txt 를 스테이징해서 넣는 커맨드 이다. 여기서 스테이징은 간단하게 말하면 commit 을 하기 전에 임시로 저장된 공간이라고 생각하면 쉽다. 아래와 같은 사진을 참조하면 아주 쉬운 개념임을 알 수 있다.

![git-staging](https://res.cloudinary.com/practicaldev/image/fetch/s--D7nJOADN--/c_imagga_scale,f_auto,fl_progressive,h_900,q_auto,w_1600/https://cl.ly/569e7f0bbfaf/download/Image%25202018-08-29%2520at%25208.26.35%2520PM.png)

`$ git commit`

커밋을 진행하는 커맨드다. 깃은 커밋을 단위로 버젼별로 추적을 하기 떄문에 커밋은 깃에게 있어 가장 핵심정인 정보이다. 항상 커밋을 하기 전에 생각을 하고 커밋을 진행하자... 제발...

생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기생각하고커밋하기

`$ git push origin {branchName}`

여태까지 작성한 commit을 github나 다른 깃 저장소에 올리는 것을 "push"라고 하는 게 그것을 수행해주는 명령어이다. 항상 모든 commit을 작성하면 push를 해야하는 것은 아니며, 개발자의 진짜 최후의 마지노선이라고 생각하면 편하다. a.k.a 보고서*최종*진짜최종*final_ReallyFinalVer*더이상의수정은없다진짜최종임.hwp

## 위의 세가지의 명령어는 개발자들이 자주 사용하고 흔희 사용하는 명령어였다. 위의 세가지만 알면 괜찮지만 아래의 목롣들은 혹시 나중에 유용하게 사용 할 수 있는 명령어들이다.

`$ git status`

현재의 깃 상태를 알려주는 명령어이다. 지금 무슨 파일이 무슨 상태인지 자세히 알려주는 명령어이다. 자신이 무엇을 add했고 commit했는지 헷갈린다면 `$ git status` 를 사용해보자

`$ git log`

현재 깃이 어떤 커밋을 한지 단번에 알 수 있는 커멘드다. 보통은 보기가 어렵기 떄문에 lg를 사용하거나 별도의 IDE를 통해서 보는 것이 더 편하다.

`$ git revert {commitId}`

특정 커밋을 취소 하거나 해당 버젼으로 돌리고 싶을 때 사용하는 명령어이다. 실수를 했다면 해당 버젼을 다시 되돌릴 수 있는 명령어이다. 하지만 쓸일이 별로 없어야 할 명령어다..

`git reset example.txt`

혹시 실수로 지금 올라가면 안되는 파일을 올렸을 경우에 취소 할 수 있는 명령어이다. 원하는 파일 앞에 HEAD를 붙여야했었지만 업데이트가 되면서 해당 방식을 사용해도 괜찮다.<sup>[1](#footnote_1)</sup>

___
<a name="footnote_1">1</a>: [https://stackoverflow.com/questions/348170/how-do-i-undo-git-add-before-commit](https://stackoverflow.com/questions/348170/how-do-i-undo-git-add-before-commit)