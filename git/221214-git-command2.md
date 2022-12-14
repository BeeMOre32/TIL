# Git Command 2

오늘은 또 다른 깃과 관련한 다른 커맨드들을 배웠다. 어떤 것을 배웠고 또 어떻게 사용하는지에 대해서 적어보았다.

## About Git Command 2

`$ git branch {branchName}`

git이 모든 프로그래머들에게 가장 많이 사용되면서 깃의 알파이자 오메가인 브랜치를 생성할 수 있게 도와준다. 브랜치에 관련해서는 바로 [이 링크]()를 통해 별도로 적었다.

`$ git switch {branchName}`

사용자가 원하는 브랜치로 이동 할 수 있게 도와주는 명령어이다. 하지만 항상 명심해야할 점이 있다. 내가 다른 브랜치를 이동 하기 전 마지막으로 했던 작업을 Add만 하고 커밋을 하지 않았을 시 다른 브랜치로 이동되면서 Add된 내용이 저장돼지 않고 날라가게 된다...
파일에 변경 사항이 생기고 또 내가 다른 브랜치로 옮겨야 하는 상황이 온다면 무슨 일이 있어도 반드시 커밋을 해주고 넘어가자.

`$ git merge {branchName}`

해당하는 브랜치의 내용을 합치는 명령어다. 합칠때 주의 사항이 있는데 예를 들어 A라는 브랜치와 B라는 브랜치가 있고 A에 B를 합치고 싶다면 A로 브랜치를 반드시 이동하고 합쳐야 한다. 항상 이를 유의하자.

### Merge Conflict에 대해서..

한국어로 하자면 병합충돌 이라는 내용이다. 브랜치를 여기저기 옮겨다니면서 같은 파일의 같은 줄의 내용을 다르게 만든다면 필연적으로 생기는 오류이다. 이유는 간단하다 아래의 코드를 보면 한번에 이해 할 수 있다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Title</title>
  </head>
  <body>
    <span>This is main branch</span>
  </body>
</html>
```

위의 코드는 main 브랜치의 예제 코드이다. 여기서 A라는 브랜치를 만들고 나서 main 브랜치에 있는 아래와 같이 코드를 변경하고 커밋을 진행하고, A로 움직여서 main 브랜치에서 수정한 코드 밑에 적혀있는 코드와 같이 수정했다고 가정해보자.

```html
<!DOCTYPE html>
<!-- 언어를 한국어로 설정 -->
<html lang="ko-KR">
  <head>
    <meta charset="UTF-8" />
    <title>Title</title>
  </head>
  <body>
    <span>This is edited main branch</span>
  </body>
</html>
```

위의 코드는 수정된 main 브랜치의 파일 코드이다.

```html
<!DOCTYPE html>
<!-- 언어를 일본어로 설정 -->
<html lang="ja-JP">
  <head>
    <meta charset="UTF-8" />
    <meta name="title" content="This is test html files" />
    <title>Title</title>
  </head>
  <body>
    <span>This is edited A branch</span>
  </body>
</html>
```

위의 코드는 수정된 A 브랜치의 파일 코드이다.

이렇게 된 상태에서 `$ git merge A` 를 실행하게 된다면 비로소 Merge Conflict 오류를 뿜어 낼 것 이다. 이를 해결하는 방법은 의외로 간단하다. 충돌 된 부분을 수정하여 파일을 작동하게만 만들면 된다.

```html
<!-- main 브랜치에서 충돌되는 내용 -->
<html lang="ko-KR">
  <!-- main 브랜치에서 충돌되는 내용 -->
  <html lang="ja-JP"></html>
</html>
```

즉 위의 있는 코드들이 다른 내용으로 작성되었으니 이를 수정하여 중복을 제거를 해달라는 내용의 오류이다. 여기에서는 이렇게 수정 하면 제대로 병합이 진행 될 것 이다.

```html
<!DOCTYPE html>
<!--중복 되는 내용을 하나로 수정-->
<html lang="ko-KR">
  <head>
    <meta charset="UTF-8" />
    <meta name="title" content="This is test html files" />
    <title>Title</title>
  </head>
  <body>
    <span>This is edited main branch</span>
  </body>
</html>
```

협업을 하다보면 특히 처음으로 협업을 진행 하다보면 항상 생기는 병합충돌오류이기 때문에, 오류가 떴다고 너무 두려워하지 말고 어디 부분은 살려야 하고 또 어떤 부분은 날려서 병합을 시켜 통일성 있게 만들어 주자.
그리고 항상 이런 것을 조율할때는 간단한 문제라면 상관이 없겠지만 항상 팀원들과 상의하여 잘 조율해 나가야한다.

`$ git rm A.txt B.txt `

로컬에서 이름을 변경을 하게 되면 git에서는 이름을 변경하게 됐다는 사실을 인지 하지 못해서 새로운 파일이 들어 온 것으로 착각하게 된다. 이를 방지 하기 위한 명령어이다.
위의 명령어를 사용해서 A.txt 를 B.txt 로 변경시 git 에서도 이름을 변경 되었음을 인지 시켜주고 자동으로 해당하는 파일의 이름을 바꿔주는 아주 신통방통한 명령어 라고 할 수 있다.

`& git commit --amend`

가장 최근의 한 커밋의 내용을 바꿔줄 수 있는 심플한 내용의 명령어이다. 만약 실수로 오타를 냈거나 커밋의 내용을 잘못 수기 했다면 위의 명령어를 통해 바로 바꿀 수 있다.

`$ git commit reset --hard`

개발자가 건들여서는 안되는 금단의 커맨드 top3 중 하나, 내용은 간단하다 해당하는 커밋을 아예 존재 하지 않았던 것 처럼 아예 밀어버리는 커맨드다. 단순하지만 무식하게 아예 말끔히 지워버린 다는 이유로 개발자가 건들여서는 안되는 금단의 커맨드다.
특히 옵션으로 --hard 를 넣게 된다면 강제로 모든 내용을 지우게 될 것 이며, 모든 레포를 날려버릴 수도 있는 금단의 커맨드 이기 때문에 제발 커밋은 reset 할 생각도 하지말자. 같은 팀원들에게 엄청난 실례다.

`$ git revert --no-commit {HEAD~n}`

커밋을 되돌릴수 있는 커맨드다. 현실적으로 위의 커맨드를 사용하는 것이 바람직하다. reset 은 아예 파일을 지워버리기 때문에 어떤 파일이 문제가 생겼고 또 어떤 파일을 지워하는지 팀원들이 인지를 하지 못한다.
하지만 revert를 하게 된다면 reset과는 다르게 되돌린 이력을 남기기 때문에 commit 메세지를 통해서 팀원들을 _합리적_ 으로 설득을 할 수 있는 이유와 사과를 할 수 있기 때문에 팀원간의 소통과 화목을 원한다면 제발... 함부로 commit 날리지 말자.
