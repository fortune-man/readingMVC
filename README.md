![post-thumbnail](https://media.vlpt.us/images/eddy_song/post/5330abd1-ba4e-4ab1-b532-927d1492796c/trygve-reenskaug.webp)

## 어딜가도 MVC

Model, View, Controller. 줄여서 MVC.

아마 소프트웨어 개발을 통틀어 가장 유명한 패턴이 아닐까.

데스크탑 앱, 웹 앱, 모바일 앱... 플랫폼을 가릴 것 없이 앱을 만드는 수많은 프레임워크들이 기본적으로 MVC 구조를 사용한다. 어떤 개발 직군을 택하든 보통 MVC는 기본이다.

초보 개발자라면, 그래서 자연스럽게 MVC에 대해 자주 들을 수밖에 없다. 아마 이 글을 누를 독자라면 '모델(M)이란? 컨트롤러(C)란?' 이런 설명은 한번씩 들어봤을 거다.

하지만 그냥 '남들이 쓰니까' 배우는 건 좀 그렇다. 🤔

MVC도 절대적인 규범은 아니며, 결국 어떤 목적을 달성하기 위한 수단이다.

그렇다면 그 뒤에 있는 '왜?'를 따져볼 필요가 있다. 그게 길게 보면 더 도움이 된다.

![img](https://www.memecreator.org/static/images/memes/4193677.jpg)

> 도대체 왜 우리는 MVC를 써야할까?

> 왜 MVC는 수많은 애플리케이션의 디폴트일까?

> MVC가 해결하는 문제는 정확히 무엇일까?

오늘 이 질문들로 시작해 MVC를 공부해본 내용을 정리해본다.

## MVC를 처음 만든 사람, 트라이브 린스케이지

1979년, 제록스 팔로 알토 연구소.

(맞다. [객체 지향의 아버지 앨런 케이](https://velog.io/@eddy_song/alan-kay-OOP)가 활약하고 있던 바로 그 연구소다. 아니 공부하다보면 어이가 없는게... IT 기술의 유래를 거슬러 올라가다보면 다 저 연구소에서 시작된다. 70년대에 저 연구소는 도대체 뭐하는 곳이었던 걸까?!)

한 노르웨이 컴퓨터과학자가 제록스 연구소에 새로운 방문 연구원으로 오게 되었다. 그의 이름은 **트라이브 린스케이지(Trygve Reenskaug).**

(이름 발음 맞나 찾아봤는데 발음을 들어도 어떻게 쓰는지 모를만큼 발음이 어렵다. 그냥 트라이브로 쓰도록 하겠다...)

![img](https://miro.medium.com/max/240/1*naCrARAXsyZ4ZyOWu89Dfw.jpeg)

당시 제록스 팔로 알토 연구소에서는 지금 우리가 누리고 있는 IT 컴퓨팅 기술의 수많은 원형들을 개발하고 있었다.

트라이브는 그 중 '**다이나북(DynaBook)**' 팀에서 일하게 되었다.

![img](https://blogthinkbig.com/wp-content/uploads/sites/4/2014/08/dynabook.jpg?fit=864%2C605)
(출처: blogthinkbig.com)

다이나북은 '최초의 태블릿 PC'로, 아이패드의 먼 조상님 급이라고 보면 된다.

다이나북 팀은 사용자들이 쉽게, 범용적으로 사용할 수 있는 컴퓨터를 만들고 싶었다.

다르게 말하면 **그때까지 컴퓨터는 연구자와 전문가의 전유물이었다**는 뜻이다.

(참고로 1977년은 최초로 상업적 성공을 거둔 개인용 컴퓨터, 애플 2가 처음으로 출시된 해다.)

다이나북 팀은 **'전문 지식 여부나 남녀노소에 상관없이** **모두가 직관적으로 사용할 수 있어야 한다**'는 철학을 내세웠다.

프로그래머는 CLI를 쓸 수 있었다. 하지만 일반 사람의 관점에서도 쉽게 적응할 수 있으려면 GUI(그래픽 유저 인터페이스)가 필요했다.

다이나북 팀은 GUI를 만드는 데 심혈을 기울였다. (GUI 또한 제록스 팔로 알토 연구소가 최초로 발명한 분야다.)

지금이야 GUI가 없는 컴퓨터를 상상할 수 없다. 하지만 당시만 해도 GUI는 전혀 일반적이지 않았다.

GUI를 잘 만들어야 일반 사용자들이 쓸 수 있다는 게 당시 제록스 연구원들의 생각이었다.

트라이브는 GUI 개발을 보면서 **한 가지 사실**을 깨닫게 된다.

> 사용자가 세상을 인식하는 방법(멘탈 모델)과, 컴퓨터가 정보를 인식하고 처리하는 방법이 정말 다르네.

> 전혀 성질이 다른 이 두 부분을 잘 분리시켜서 설계하는 게 매우 중요하겠구나..!

## 객체 지향 + GUI? MVC의 등장 배경

[앨런 케이가 창시한 객체 지향 프로그래밍(Object oriented Programming)](https://velog.io/@eddy_song/alan-kay-OOP)은 다음과 같은 고민에서 시작되었다.

> 좋은 코드를 만들기 위해서,
> 어떤 방식으로 코드를 나누고 묶어줘야 할까?
> 어떤 방식으로 코드를 추상화해야할까?

여기에 대한 앨런 케이의 답은 **'객체'라는 단위들이 '메시지'를 주고받는 형태로 소프트웨어를 추상화하자**는 것이었다.

트라이브는 여기서 한 발 더 나아간다.

트라이브가 GUI를 사용하는 애플리케이션을 잘 보니, 'UI 관련된 코드'와 '데이터 저장/처리 코드'는 특성과 하는 일이 뚜렷하게 달랐다. 변경하는 이유나 시점도 무척 달랐다.

트라이브는 **(1) '비즈니스 로직'**과 **(2) '시각적인 UI'** **(3) 둘 사이를 연결해주는 부분**을 코드 안에서 분리하고 역할 부여를 해줘야 한다는 생각을 하게 된다.

![img](https://alchetron.com/cdn/trygve-reenskaug-8a4384bf-6a43-42d2-aa1a-c517662d649-resize-750.jpeg)

> GUI를 사용하는 애플리케이션을 객체 지향적으로 추상화하려고 하니까, 객체들이 맡고 있는 '역할'을 나눠주는 게 무척 중요할 거 같다 이 말이야...

> 그렇다면 역할을 이렇게 나눠보면 어떨까.

> 애플리케이션 데이터를 저장/가공하는 역할을 **Model**.

> 화면에 데이터를 표시하고, 사용자와의 인터랙션을 담당하는 부분을 **View**.

> 둘을 연결하는 역할을 **Controller**.

> 이렇게 나눠서 Model - View - Controller로 분류(추상화)하면 어떻겠나?

![img](https://miro.medium.com/max/700/1*6NUTfvsDJfoBSfp9wuT7FQ.png)
MVC의 초기 아이디어를 나타낸 그림. 사용자의 멘탈 모델과, 컴퓨터의 멘탈 모델을 표시해놓은 게 보인다. (출처: [MVC XEROX PARC 1978-79](https://folk.universitetetioslo.no/trygver/themes/mvc/mvc-index.html))

> “MVC was created as a solution to the general problem of giving users control over their information as seen from multiple perspectives.”
> -Trygve Reenskaug

트라이브의 말을 좀 더 잘 이해하기 위해 간단한 예시를 들어보자. 우리가 메모 앱을 만든다고 해보자.

이 메모 앱 안에는...

사용자에게 메모를 보여주는 객체, 메모 추가 버튼을 담당하는 객체가 있을 것이고, (View)

메모한 내용을 저장하는 객체, 메모를 시간순으로 정렬해주는 객체 등이 있을 것이다. (Model)

이 객체들은 각각 Model이라는 역할과 View라는 역할로 나눠서 하고 있는 일을 명확하게 분리해줄 수 있게 된다.

단순화시켜보자면, MVC가 등장한 이유는 다음과 같다.

> GUI를 가진 소프트웨어를 객체 지향적으로 잘 구조화하기 위해서.

MVC 구조는 직관적이고 유용했다. 객체 지향 프로그래밍과 GUI는 소프트웨어의 표준으로 자리잡았다. 덕분에 MVC는 반세기 이후인 지금까지도 널리널리 퍼져서 쓰이게 되었다.

## MVC의 본질: 관심사의 분리

> MVC의 본질적인 목표가 무엇일까?

이 질문에 쉽게 대답하자면, 'Model과 View를 분리하는 것'이다.

이걸 [전문가](https://martinfowler.com/eaaDev/uiArchs.html)는 어려운 말로 **'관심사의 분리(Separation of Concerns)'**라고 한다.

> "At the heart of MVC, and the idea that was the most influential to later frameworks, is what I call **Separated Presentation.**"

> **"The idea behind Separated Presentation** is to **make a clear division between domain objects** that model our perception of the real world, and **presentation objects** that are the GUI elements we see on the screen."
> -Martin Fowler

🔗 [마틴 파울러가 설명하는 GUI 아키텍쳐의 역사](https://martinfowler.com/eaaDev/uiArchs.html)

🔗 [관심사의 분리(Separation of Concerns)](https://kwangyulseo.com/2015/05/29/관심사의-분리separation-of-concerns/)

다만 '관심사'의 분리라고 하니까 직관적이지가 않은데, 나라면 이렇게 번역했을 거 같다.

### 관심사의 분리 = '분업'

![img](http://eiec.kdi.re.kr/userdata//userdata/click/201402/2127/edit/acbOx0VAl0TId_Il2Hbpu1390522128435.jpg)

관심사의 분리는 분업하고 똑같은 말이다.

자본주의 사회에 살고 있는 사람이라면, 분업이 인간 사회의 기본 원리라는 걸 알고 있을 것이다.

일을 나눠서 해야 효율성이 오른다. 내가 할일만 하면 되니까 신경쓸 것도 줄어든다.

회사가면 주로 '제품 만드는 팀' '제품 파는 팀' '관리하는 팀' 이렇게 나눠져있다. 바꿔 말하면 이것도 인간 조직에 적용한 일종의 MVC 같은 거라고 할 수 있겠지?

### 너나 걱정하세요

'관심사(Concern)'에는 걱정이라는 뜻도 있는데, **걱정의 분리**라고 해도 말은 되는 거 같다.

결국 분업이라는 게, 빵집 주인은 빵을 어떻게 잘 만들고 팔지만 걱정하고, 목장 주인은 소를 어떻게 잘 키우고 팔지만 걱정하면 서로 Win-Win 하게 된다는 뜻이니까.

각자 맡은 걱정만 하라는 거지.

![img](https://media.vlpt.us/images/eddy_song/post/d387b759-983d-487e-b5d4-a89f7729ebbc/mindYours.jpeg)

### 결국은 좋은 코드를 만들기 위한 것

소프트웨어도 마찬가지다.

묶어놓은 코드(모듈)들의 역할을 나누고, 각자 맡은 부분만 신경쓰는 것이 기본 원리다.

그래야만 서로가 서로에게 영향을 받지 않고, 코드의 중복을 줄일 수 있다.

결합도가 낮아지고 중복이 줄어들면 변경을 하기가 쉬워진다.

변경을 하기가 쉬우면?
좋은 코드가 될 가능성이 높다.

여기서 내가 느꼈던 점. MVC를 이해하는 시작점도 결국에는 똑같다.

**객체지향이나, MVC 패턴이나, (나중에 다뤄볼) SOLID 원칙이나... 결국은 다 코드를 바꾸기 쉽고, 읽기 쉽게 만들기 위한 노하우일 뿐**이다.

### MVC 외에도 '관심사의 분리'는 많이 있다.

'관심사의 분리'는 소프트웨어 공학에서 보편적으로 강조하는 고전적인 원칙이다.

MVC를 공부하다가 관심사의 분리 원칙을 알게 되고 나니, 다른 IT기술 사례에서도 그냥 그렇구나 했었던 것들이 결국은 이 관심사의 분리를 따르고 있었구나 싶다.

MVC 외에도 관심사의 분리 사례는 이런 것들이 있다.

**Internet: IP와 TCP**
인터넷에서 IP layer는 데이터를 목표 지점까지 전달한다. TCP layer는 데이터 패킷의 전송을 추적하고 관리한다. IP는 TCP가 하는 일에, TCP는 IP가 하는 일에 신경쓰지 않는다.

**Web: 서버와 클라이언트**
서버는 클라이언트가 요청하는 데이터를 보내준다. 클라이언트는 받아온 정보를 사용자에게 보여준다. 클라이언트는 서버가 하는 일에, 서버는 클라이언트가 하는 일에 신경쓰지 않는다.

## 소프트웨어 패턴과 축구 포메이션의 공통점

어릴 때 동네 축구를 하다보면, 공격수고 수비수고 없었다.
그냥 공이 있으면 우와아아아 하고 달려가서 어떻게든 뺏는 게 축구였다.

하지만 조금만 더 영리해지면, 축구를 더 잘하기 위해서는
각자 역할을 나누고 잘 따라야 한다는 걸 알게 된다.

프로 축구에 오면 그런 역할과 배치들이 전술을 만들어내고, 그런 것을 우리는 '4-4-2 포메이션'이니 4-3-3 포메이션이니 하고 부르게 된다.

~~(풋볼 매니저나 피파를 해봤다면 모를 수가 없겠지??)~~

![img](https://www.techgamingreport.com/wp-content/uploads/2020/11/1606245153_719_Best-Football-Manager-2021-Tactics-and-Formations.jpg)
(출처: techgamingreport)

### 소프트웨어 패턴은 축구의 포메이션이다

내가 MVC 같은 아키텍쳐(패턴)을 배우면서 느낀 건, 축구의 포메이션과 매우 비슷하다는 점이다.

일단 패턴은 코드의 '배치'이고, 포메이션은 선수의 '배치'다.

실제 상황과 동작은 (즉, 구현은) 매우 다를 수 있다. 둘 다 실제를 추상화시키고 이름을 붙여서 사람들이 구조와 배치에 대해서 이해할 수 있도록 만들었다.

![img](https://media.vlpt.us/images/eddy_song/post/579d4018-17d9-4b1f-b227-644e45c69e57/Screen%20Shot%202022-03-12%20at%205.46.22%20PM.png)

그런 점에서 MVC를 이해하는 몇 가지 힌트를 축구 포메이션에서 가져와보자.

### 1. 절대적이지 않다. 명확한 경계가 없다.

> 알겠고, 알겠는데... 그래서
> 4-4-2 포메이션이 좋아요?
> 3-4-3 포메이션이 좋아요?

누군가 이렇게 묻는다면 뭐라고 답할까?

> A: 상황에 따라 다르죠.
> B: ~~(돈 많은 팀이요)~~

A가 정답일 것이다.

사실 두 팀 똑같이 4-4-2 포메이션이라하더라도, 플레이는 전혀 다를 수 있다. 각 선수와 그때 그때 상황에 따라서 공격 방식, 패스의 흐름이 전혀 다를 수 있다.

> 중계자: 앗 저 팀은 4-4-2 포메이션인데 방금 패스 플레이는 4-3-3 이었습니다!

중계자가 저렇게 말을 한다면 아마 우스울 거다.

4-4-2 포메이션이라는 게 명확하게 세워진 규칙이거나, Yes/No로 딱 정해져있는 게 아니다.

사실 별 의미도 없는 구별이다. 결국 중요한 건 골 넣는 것이지 포메이션이 아니다.

소프트웨어도 똑같다. **패턴은 절대적이고 명확한 선이 아니다.** 실제 상황에서는 다양한 모습으로 나타날 수 있다.

그런 의미에서 객체 지향의 패턴, 혹은 아키텍쳐라고 부르는 것들을 배우다 보면 항상 듣게 되는 말이 있다.

> 정답은 없다.

'이런 코드는 MVC인가요 아닌가요?'
이런 것도 상당히 애매하다.

'여기서는 컨트롤러가 이것도 하고 있는데?'
'엇? 너는 모델이 이런 걸 해? 그러면 MVC 아닌데?'

MVC는 워낙 오래된 패턴이기 때문에, 수많은 변형 버전들이 있다. 그게 MVC다 아니다라고 딱 말하긴 어렵다.

'442스러운' 움직임이 있고 'MVC스러운 동작'이 있을 수는 있겠지만.

둘다 절대적인 규칙이라기보다는, 높은 수준에서 이해하기 위한 '지도'에 가깝다.

### 2. 포메이션에 맞게 행동해야 한다.

포메이션에서 정해진 각자 자리에 공격수 - 미드필더 - 수비수를 배치했다고 그 포메이션을 활용하고 있는 건 아니다.

포메이션을 정해놓았는데 공격수가 수비 가담하고,수비수가 공격 가담하면 안 되겠지?

포메이션은 어떠한 수비/공격 전술을 더 잘하기 위해서 만들어진 것이다.

그러니 **실제로 그 포메이션이 의도한 바대로 플레이**를 해줘야 한다!

마찬가지로 애플리케이션을 MVC로 나눠놨다고 해도
MVC스럽게 서로 협력하고 있지 않다면 별 의미가 없다.

그렇다면 'MVC스럽게 협력하고 있다'는 것은 무엇일까?

#### MVC스러운 협력

내가 MVC를 직접 구현해보면서 배웠던 구체적인 원칙들은 다음과 같다.

(사실 이건 내가 배운 iOS UIKit 프레임워크 기준이다. 아마 플랫폼/언어별로 차이가 있을 텐데 다른 프레임워크에선 어떤지 잘 모르겠다. 댓글로 알려주시길!)

- 모델은 뷰에게, 뷰는 모델에게 메시지를 절대 보내지 않는다.
- 컨트롤러는 모델과 뷰를 알아도 되지만 (인스턴스 변수로 직접 가져도 되지만), 모델은 뷰를 모르는 상태에서 데이터를 보낸다. 결합도를 낮춰서 재사용이 가능하고 유연한 구조를 만들기 위해서다.
- 모델 쪽으로 향하는 로직(입력 흐름)과, 뷰 쪽으로 향하는 로직(출력 흐름)은 분리한다.
- 모델에는 주로 HTTP 요청을 보내는 코드, 응답을 파싱하는 코드, DB에 데이터를 저장하는 코드, 데이터 모델을 관리하는 코드, 각종 상수, 자주 사용하는 헬퍼 함수 등이 들어간다.
- 뷰에는 데이터를 보여주고, 사용자가 인터랙션을 할 수 있게 만들어주는 최소한의 코드만 들어간다. 나머지는 컨트롤러에게 위임한다.

### 3. 기본에서 시작해 바뀌면서 진화해나간다.

'공격수-미드필더-수비수' 구조는 축구 포메이션의 기본이다.

하지만 거기서 끝은 아니다. 여기서 팀들이 계속 더 맞는 전략을 고민하면서, 숫자가 줄어들고 늘어나고, 미드필더가 공격형 수비형으로 나뉘고 하면서 다양한 변형을 준다.

**기본 포메이션에서 단점을 개선하고 조금씩 바뀌면서 진화하고, 그 중에 유명하거나 성공한 것에 이름이 붙여지는 느낌**이다.

MVC 패턴도 마찬가지다.

MVC 패턴이 등장한 이후 수많은 버전과 새로운 패턴들이 등장했. 하지만 'Model과 View의 분리'라는 기본은 거의 모든 애플리케이션에서 변하지 않는다.

다만 시간이 지나면서 MVC 패턴은 상황에 따라서 **몇 가지 문제점**을 드러내기도 한다.

일단, 너무 역할 분배가 단순하다.

현대의 소프트웨어들은 예전보다 훨씬 더 복잡한 플레이들을 해야한다.

공격수(V)-미드필더(C)-수비수(M)만 있으니 '잘 맞지 않다'라는 여러 지적들이 나온다.

특히 컨트롤러(C)가 문제로 많이 지목된다.

축구에서 미드필더가 올라운더인 것처럼, 많은 MVC 구조에서 컨트롤러는 **'Model 일하고 View 일 빼고 다하는 애'**가 되는 경우가 많다.

그러다보니까 관심사의 분리(분업) 원칙이 제대로 안 지켜지는 경우도 많다. 앱의 실행 흐름이 너무 복잡해지는 경우가 발생한다.

iOS에서는 MVC 외에도 MVVM, MVP, VIPER, RIBs 등이 유명하다.

이 아키텍처도 결국은 복잡한 앱을 만들어야 하는데 MVC만으로 부족하니까 추가적인 역할을 부여하면서 진화해 나간 버전이다.

(참고 링크: [Advanced iOS Architecture: Solving the 5 Issues of the MVC, MVVM and VIPER patterns](https://matteomanferdini.com/ios-architecture-lotus-mvc-pattern/))

이런 걸 보면 그만큼 기본이 중요하다는 뜻이기도 하다.

M과 V의 분리라는 기본 원칙에서 시작해서, 더 복잡한 것들을 하기 위해 진화했기 때문이다. (다르게 말하면, 별로 안 복잡한 앱은 MVC로 해도 얼마든지 상관없다는 뜻이기도 하다.)

MVC에서 더 나아간 대안적인 패턴들에 대해서는 나중에 또 글로 정리해보도록 하자.

## 요약 정리

- MVC는 1979년에 제록스 팔로알토 연구소에 있던 트라이브 린스케이지라는 사람이 만들었다.
- '일반 사용자들이 쓸 수 있도록 만들자(GUI)'와 '변경하기 쉬운 코드를 만들자(객체 지향)'의 아이디어 사이에서 등장한 패턴이다.
- MVC는 오늘날 언어/플랫폼을 막론하고 모든 애플리케이션에서 기본적으로 사용된다.

- MVC의 핵심은 '관심사의 분리'다. 비즈니스 로직(Model)과 UI 로직(View)를 분리한다.
- 분업이 효율화를 만들듯이, 관심사의 분리는 유연한 소프트웨어를 만든다.
- 소프트웨어 패턴은 축구 포메이션과 공통점이 많다.
  1. 둘다 절대적이거나 명확한 경계선이 있는 건 아니다.
  2. 구조 자체가 끝이 아니라, 그에 맞게 플레이하는 것도 중요하다.
  3. 기본에서 시작해서 개선하고 바뀌면서 진화해나간다.
