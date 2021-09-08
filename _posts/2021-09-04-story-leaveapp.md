---
layout: post
title: "비개발자가 사내 휴가 앱을 만들어봤습니다"
author: "JJ"
---

올해 5월 개발을 완료하고 작성했던 글인데 게으른 탓에 이제야 정리해 올린다.


<br/>

## <a name="first"></a>1. Intro
개발자 될 것도 아닌데 개발해서 뭐하나? 비즈니스 공부를 하는게 생산적이지 않을까?

2017년 어느날 Hello  World를 처음 친 뒤 가끔 혼자 책, 영상을 보며 공부를 했고, Google Sheet에서 사용 할 몇 줄의 코드를 짜왔다. 그 과정에서 스스로 한번씩 하던 질문이다.

휴가 앱을 만들면서 알게 됐다. 나는 개발이 재밌어서 하는구나!


<br/>

## <a name="second"></a>2. 처음엔 별 생각 없었다

1. 신청자가 캘린더에 휴가 등록
2. 담당자가 슬랙 알림 or 캘린더 확인
3. 수동으로 휴가 관리 시트에 옮겨적기

여느 작은 스타트업이 그렇듯 우리 회사도 별도의 휴가 관리 시스템이 없었다. 그래서 위와 같이 휴가를 관리했다. 이 방식은 담당자가 매번 신경을 써야 했다. 사람이 늘어날수록 써야 하는 시간도 늘어나고 실수할 가능성도 높아지는 구조였다. 도움을 주고 싶었다. 구글 설문지와 간단한 시트 자동화를 통해 지금보다 좋아질 것이라 막연히 생각했다. 그래서 해보겠다고 했다.

<br/>

<img src="https://i.imgur.com/lEfE6l9.png" style="max-height: 400px; width:auto;">
_쉬울 줄 알았다.._


<br/>

## <a name="third"></a>3. 일이 커졌다

설문지로 신청하는 방식은 담당자는 편해질 수 있지만, 신청자는 캘린더보다 불편했다. 어드민, 구성원 모두가 만족하는 성과관리 서비스 [Lemonbase](https://lemonbase.com/?utm_source=jjblog&utm_medium=referral&utm_campaign=leavingapp){:target="_blank"}을 만드는 일원으로서 용납할 수 없었다.


<br/>

## <a name="fourth"></a>4. 제대로 만들어 보기로 했다

[Google Webapp](https://developers.google.com/apps-script/guides/web){:target="_blank"}을 이용해 만들기로 했다. Google Sheet을 DB로 이용하며 프론트앤드를 구현해주는 기술이다. 이걸 선택한 이유는 아래와 같은 장점이 있기 때문이다. 성능이 떨어진다는 단점이 있지만 사내 프로그램이라 문제없을 것이라 생각했다.

1. 이전에 사용해봤음
2. 서버가 필요 없음
3. 어드민 페이지 필요 없음 (Sheet 직접 수정 가능)
4. Sheet 기본 함수를 같이 사용할 수 있음


<br/>

## <a name="fifth"></a>5. 기획을 시작했다

휴가가 만만히 볼 녀석이 아니었다.

반차와 중간에 낀 휴일이 가장 먼저 이슈가 됐다. 연속된 휴가도 하루씩 신청하도록 하면 가장 쉽게 해결되지만, (다시 한번 말한다) 어드민, 구성원 모두가 만족하는 서비스를 만드는 사람으로서 용납이 안 됐다.

결국 시작일과 종료일을 선택하고 반차, 휴일이 있는 경우는 사용자가 체크하도록 기획했다. 하루씩 사용하는 사람이 가장 많기 때문에 시작일만 입력하면 나머지 정보는 하루에 맞춰 자동 입력되도록 했다. 이를 통해 하루짜리 휴가를 쓰는 사람은 시작일만 선택하면 휴가를 신청할 수 있고, 연속으로 쓸 사람만 종료일을 조절하도록 했다.

<br/>

<img src="https://i.imgur.com/1A6Ld3X.png" style="max-height: 500px; width:auto;">
_사용자를 배려한 기획서_


<br/>

## <a name="sixth"></a>6. 뭔 놈의 문제가 이렇게 많은지

구현하다 보니 디테일하게 기획하고 변경할 게 계속 생겼다. 종료일이 시작일보다 큰데 신청되고, 이상한 이름으로도 신청되고, 시간처럼 보였는데 텍스트라 계산 안 되고.. 타임존(왜 10시간이 적게 나오느냐고!!).. 하나하나 해결했다.

<br/>

<img src="https://i.imgur.com/KDgmwPo.png" style="max-height: 500px; width:auto;">
_해결했지만 왜 됐는지 모른다._


<br/>

## <a name="seventh"></a>7. 완성이다..!?

어느 정도 완성됐을 때 일부 동료에게 먼저 공유를 했다. 긍정적 피드백들 중 한 동료의 피드백. "취소할 수 있는 기능도 있으면 좋겠군요?"

있으면 좋다는 건 알고 있었다. 자주 쓰는 기능도 아닐 것 같고.. MVP니까.. 빨리 출시해야 하니까.. 라고 말하고 싶었지만 계속 마음에 걸렸다. (사실 힘들어서 안했다..) 피드백도 있었으니 까짓것 좀 더 해보기로 했다.

<br/>

<img src="https://imgur.com/yxm9OkY.png" style="max-height: 400px; width:auto;">
_Jamie 고맙습니다._


<br/>

## <a name="eighth"></a>8. 끝났다
취소 기능도 엄청나게 많은 이슈가 있었다. 소중한 주말 2일을 꼬박 썼다. 만들고 보니 취소까진 만들어야 했던 것 같다. 완결된 느낌이 들었다.

동료들에게도 소개했다.

<br/>

<img src="https://imgur.com/VQDhUhJ.png" style="max-height: 200px; width:auto;">
_팀 이동 제안을 받았다._


<br/>

## <a name="ninth"></a>9. 재밌었다

막히는 부분이 생겼을 때 몰입하고 풀어가는 과정에서 재미를 많이 느꼈다. 당시에는 답답해 죽을 것 같지만 풀었을 때 그 쾌감이란. 이게 개발의 매력이고 나와 잘 맞는다는 걸 알았다. 잘 사용하는 동료들을 보는 것도 매우 즐거운 경험이었다.

개발자가 되기 위해서가 아니라 문제를 해결하고 가치를 만드는 재미를 느끼기 위해 앞으로도 종종 이런 프로젝트를 해야겠다.

\+ 3개월 지난 지금도 문제없이 작동하고 잘 사용하고 있다.

<br/>

<div class="video-container">
<iframe width="840" height="472.5" src="https://www.youtube.com/embed/ETS6k5kMdo8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>