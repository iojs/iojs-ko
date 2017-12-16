---
layout: page
title: 번역 참여 가이드
---

# 번역 대상

* [Node.js](https://nodejs.org/)와 관련된 모든 문서가 번역 대상입니다.
* 기본적으로 [공식 Node.js의 글](https://nodejs.org/en/blog/)을 번역합니다.
* 번역했으면 하는 문서는 [이슈](https://github.com/nodejs/nodejs-ko/issues)로 등록합니다.
  * 이슈의 제목을 원문의 제목으로 하고 본문에 링크를 입력합니다.
  * 번역 이슈에는 [translation](https://github.com/nodejs/nodejs-ko/labels/translation) 레이블을 붙입니다.

# 번역에 참여하는 방법

* [이슈](https://github.com/nodejs/nodejs-ko/issues) 중에서 [translation 레이블이 붙은 이슈](https://github.com/nodejs/nodejs-ko/labels/translation)가 번역할 문서입니다.
* 댓글로 번역하겠다는 의사를 밝힙니다.
* 이슈를 할당하면 번역의 진행을 위해서 1주일 안에 번역 작업을 합니다. 1주일이 지나면 다른 사람에게 이슈가 넘어갈 수 있습니다.

# 번역 방법

1. [nodejs-ko](https://github.com/nodejs/nodejs-ko) 프로젝트를 포크합니다.
1. 로컬에 클론해 `npm install`으로 관련 라이브러리를 설치합니다.
1. 풀 리퀘스트를 보내기 위한 브랜치를 새로 생성합니다.
1. 번역 작업을 위한 파일을 생성합니다.
  * 디렉터리 관례
    * 모든 글은 `source/_posts/` 디렉터리를 사용합니다.
  * 파일명
    * 원문이 올라온 날짜와 제목을 대시(`-`)로 이어 붙여서 파일명을 정합니다.(예시: `2015-01-27-state-of-io-js.md`)
    * 주간 뉴스의 경우에는 원문의 날짜와 weekly를 대시(`-`)로 이어 붙여서 파일명을 정합니다.(예시: `2015-02-13-weekly.md`)
  * 자동 파일 생성
    * 관례대로 파일을 자동으로 생성하려면 다음 명령어를 실행합니다.

      ```bash
      $ npm run scaffold URL [DATE]
      ```

    * 다음과 같이 사용합니다.

      ```bash
      $ npm run scaffold https://raw.githubusercontent.com/nodejs/nodejs.org/master/locale/en/blog/release/v6.3.0.md 2016-07-22
      ```

    * 주간뉴스는 날짜를 생략할 수 있습니다.

      ```bash
      $ npm run scaffold https://raw.githubusercontent.com/nodejs/nodejs.org/master/locale/en/blog/weekly-updates/weekly-update.2016-07-22.md
      ```

    * 이 명령어를 실행하면 관례에 맞는 파일이 자동으로 생성됩니다.
  * 번역문서
    * 파일 상단에는 YAML 형식으로 글의 메타정보를 작성합니다.

      ```yaml
      ---
      category: articles
      title: 번역 글의 제목
      author: 원 저자명
      ref: 원문의 글 제목
      refurl: 원문 링크
      translator: github_id
      ---
      ```

    * 번역자의 이름은 문자열이나 key-value로 작성합니다.

      ```yaml
      translator: github_id
      # or
      translator:
        github_id: Real Name
      ---
      ```

    * 번역자가 여러 명인 경우에는 `translator`에 여러 줄을 추가하면 됩니다.

      ```yaml
      translator:
      - github_id1
      - github_id2
      # or
      translator:
        github_id1: Real Name1
        github_id2: Real Name2
      ---
      ```

    * 이곳에 작성한 메타정보는 각 글의 상단에 표시됩니다.
    * 문서는 [마크다운](https://help.github.com/articles/github-flavored-markdown/) 형식으로 작성합니다.
    * 이후 문서를 관리하기 위해 원문을 주석(`<!-- -->`)으로 추가하고 번역한 내용을 다음과 같이 작성합니다.

      ```md
      <!--
      # io.js 1.6 release
      This week we had a two io.js releases [v1.6.1](https://iojs.org/dist/v1.6.1/) and  [v1.6.0](https://iojs.org/dist/v1.6.0/), complete changelog can be found [on GitHub](https://github.com/nodejs/io.js/blob/v1.x/CHANGELOG.md).
      -->

      # io.js 1.6 릴리스
      이번 주에는 [v1.6.1](https://iojs.org/dist/v1.6.1/)과 [v1.6.0](https://iojs.org/dist/v1.6.0/) 두 번의 릴리스가 있었습니다. [GitHub](https://github.com/nodejs/io.js/blob/v1.x/CHANGELOG.md)에서 전체 변경사항을 볼 수 있습니다.
      ```

1. `npm start`를 실행하면 [로컬](http://localhost:4000/nodejs-ko/)에서 마크다운 문법 등이 깨진 곳이 없는지 확인해 볼 수 있습니다.
1. 번역이 완료되면 해당 브랜치를 이용해서 풀 리퀘스트를 보냅니다.
  * 커밋 메시지나 풀 리퀘스트에 번역한 문서의 이슈번호를 추가합니다.
1. 풀 리퀘스트는 리뷰 과정을 거치게 되고 이 과정에서 오타, 번역 문체 등을 다듬습니다.
1. 2명 이상이 GitHub의 리뷰 기능을 사용해 승인하면 바로 머지할 수 있습니다.
   다른 수정을 기다려야 하거나 이슈가 있는 경우가 아니라면 2명 이상이 승인한 경우 누구나
   머지할 수 있습니다. 일반적으로 두 번째 리뷰 승인자가 머지합니다.
1. 풀 리퀘스트가 머지되면 CI가 자동으로 [블로그](https://nodejs.github.io/nodejs-ko/)에
   발행합니다.

# 그 외 참고할 사항

1. 특별히 어색하지 않다면 기울임꼴, 굵은 글씨 등 서식은 원문과 똑같이 사용합니다.
1. 사람, 기관, 지역 이름은 가능한 영어 그대로 남겨둡니다.
1. 본문에 링크된 글에 대한 한국어 문서가 존재한다면 한국어 문서의 링크를 우선으로 사용합니다.
1. 적어도 풀 리퀘스트를 만들기 전에는 [한국어 맞춤법 검사기](http://speller.cs.pusan.ac.kr/)를 사용해 맞춤법을 확인해주세요.

# 자주 나오는 리뷰 사항

* Node의 버전 이름은 다음과 같이 번역합니다.
  * `Current`-> `현재 버전`
  * `Stable`-> `안정 버전`
  * `LTS`-> `LTS`
  * `Maintenance`-> `유지보수 버전`
* `Node v6.0.0 (Current)` 같은 경우 `Node v6.0.0(현재 버전)`으로 번역합니다. 버전 번호와 괄호 사이에 공백을 제거합니다.
* 괄호 뒤에 조사가 오면 괄호는 앞 단어에 붙여 씁니다. 또한, 조사는 괄호를 제외하고 읽었을 때 자연스럽도록 적습니다. 예시: `사물인터넷 (IoT)과` 대신 `사물인터넷(IoT)과`라고 번역합니다.
* `릴리즈`가 아니라 `릴리스`로 표기합니다.
* URL은 `< >`로 감싸줍니다. 예시: `<https://nodejs.github.io/nodejs-ko/>`
* 마크다운의 헤딩을 의미하는 `#`, `##`, `###` 등의 윗줄에는 빈 줄을 추가합니다. 빈 줄이 없으면 스타일이 적용되지 않습니다.

  ```md
  -->
  ### Node v6.0.0(현재 버전) 릴리스
  ```

  위 내용은 다음과 같이 빈 줄을 추가합니다.

  ```md
  -->

  ### Node v6.0.0(현재 버전) 릴리스
  ```

* 목록을 나열하는 경우 영어 문장에 들어가는 `and`, `&`는 번역하지 않습니다. 예시: `A, B, C, and D`, `A, B, C, & D`는 `A, B, C 그리고 D`로 번역하지 않고 `A, B, C, D`로 번역합니다.
* 영어 뒤에 조사가 올 때도 읽었을 때 되도록 읽기 자연스러운 방향으로 적습니다. 예시: `vm.createContext과`가 아니라 `vm.createContext와`라고 번역합니다.
* `Core Technical Committee`는 `코어 기술 위원회`라고 번역합니다.
* Node.js 공식 블로그의 특성상 비슷한 시기에 나온 글에는 중복되는 내용이 있는 경우가 많습니다. 특히 보안 업데이트 공지나 새 버전 릴리스의 경우 그렇습니다. 비슷한 문서의 다른 번역문을 참고하면 번역에 도움이 됩니다.
* `메소드`가 아니라 `메서드`로 표기합니다. <http://www.insightbook.co.kr/9688>

# 멤버 구분

## nodejs-ko Collaborators
* [nodejs-ko 저장소](https://github.com/nodejs/nodejs-ko)에 Collaboratios로 등록된 사용자를 말하며 nodejs 조직이나 [nodejs-ko 팀](https://github.com/orgs/nodejs/teams/nodejs-ko)에는 등록되지 않습니다.
* [nodejs-ko 저장소](https://github.com/nodejs/nodejs-ko)에 올라오는 이슈를 관리할 수 있고 번역문의 리뷰, 머지 권한을 가집니다.

## nodejs-ko Maintainers
* 메인테이너는 [nodejs-ko 팀](https://github.com/orgs/nodejs/teams/nodejs-ko)에 등록된 멤버를 의미합니다.
* 메인테이너는 nodejs-ko 문서 번역, 번역문의 리뷰, 저장소 관리는 물론 Node.js 소속 다른 프로젝트에서 발생 또는 요청하는 한국어 관련 이슈에도 참여합니다.
  * 다른 프로젝트에서 nodejs-ko 의 의견을 듣기 위해서 멘션을 하는 경우가 있습니다.
* nodejs-ko 저장소 외에 [nodejs.org](https://github.com/nodejs/nodejs.org)의 한국어 번역과 검수에도 참여하고 있습니다.
* nodejs-ko 저장소 관리를 위해 번역문이 아닌 간단한 맞춤법 오류, 서식 오류, 오타, 저장소 설정 등은 풀 리퀘스트를 거치지 않고 바로 수정할 수 있습니다.
* 빠른 반영을 위해 간단한 오류 등은 다른 사람이 등록한 풀 리퀘스트를 직접 수정할 수 있습니다.
* nodejs-ko의 메인테이너는 6개월마다 갱신하며 갱신 시점을 기준으로 최근 1년간 nodejs-ko 저장소에 기여한 사람을 메인테이너로 등록합니다.
  * 메인테이너 명단은 Node.js 릴리스 주기에 맞춰서 매년 4월, 10월에 갱신합니다.
  * [Graph](https://github.com/nodejs/nodejs-ko/graphs/contributors)를 기준으로 최근 1년간 커밋이 10개 이상인 사람을 메인테이너로 등록합니다.(풀 리퀘스트는 Squash로 머지합니다.)
  * 현재는 nodejs-ko 팀 관리 권한 이슈로 nodejs 코어멤버들과 논의하는 중입니다. [관련 이슈](https://github.com/nodejs/nodejs-ko/issues/425) 참고.
