---
layout: post
title: Github Page 시작하기 & Hydejack 테마 적용
description: >
  Github Page 처음 생성부터 Jekyll의 Hydejack Theme 적용하기 까지
sitemap: false
---

- Table of Contents
{:toc .large-only}

## Github Repository 생성

![Full-width image](/assets/img/githubpage/001.png){:.lead width="800" height="100"}

Github Page가 될 Repository를 생성합니다. 이때, Repository의 이름은 `Username.github.io` 로 입력해야 합니다.

![Full-width image](/assets/img/githubpage/002.png){:.lead width="800" height="100"}

따라서 저는 remind2dev.github.io 로 Repository를 생성했습니다.   
공개 범위는 Public으로 설정해야 깃허브 페이지로 사용할 수 있습니다.   

깃허브 페이지는 생성했지만 보여줄것이 아무것도 없기 때문에 https://usename.github.io 로 접속해도 아무것도 나타나지 않습니다. 이제부터 Jekyll의 Hydejack 테마를 적용하여 화면이 나타나게 해보겠습니다.
 
## 테마 고르기

Github Page는 공식적으로 Jekyll을 지원합니다.   
따라서 꼭 Hydejack 테마를 사용할 필요는 없지만, 이 포스트는 해당 테마를 기준으로 작성하였기 때문에 적용 방법이 달라질 수 있습니다.

아래의 사이트들을 방문하여 원하는 테마를 골라 적용합니다.
> - [jekyllthemes.io](https://jekyllthemes.io/free)   
- [jekyllrc](http://themes.jekyllrc.org/)   
- [jekyll-themes](https://jekyll-themes.com/free/)
 
## Hydejack 테마로 선택

![Full-width image](/assets/img/blog/blog-layout.jpg){:.lead width="800" height="100"}

제가 선택한 Hydejack 테마는 여러 장점이 있지만 그 중 두가지를 꼽자면 다음과 같습니다.
- Code Block 지원
![Full-width image](/assets/img/githubpage/002-1.png){:.lead width="800" height="100"}
- Katex Kramdown (수학 공식 표시) 지원
![Full-width image](/assets/img/githubpage/002-2.png){:.lead width="800" height="100"}


## 테마 적용하기

원하는 테마를 골랐다면 Gitgub Repository를 방문하여 설치방법을 따라 적용하면 됩니다.   
Hydejack 설치 및 적용방법을 알아보겠습니다.

테마를 적용하기에 앞서 깃허브와 루비가 설치되어있어야 합니다.   
깃허브와 루비 설치방법은 링크로 대체 하겠습니다.
> - [Github 다운로드](https://git-scm.com/download/)   
- [Github 설치방법 참고](https://taewow.tistory.com/13)   
- [Ruby Installer 다운로드](https://rubyinstaller.org/)   
- [Ruby 설치방법 참고](https://junstar92.tistory.com/5)

**Github와 Ruby 설치**가 완료 되었다면 본격적으로 테마를 적용해보겠습니다.

- [Hydejack-starter-kit](https://github.com/hydecorp/hydejack-starter-kit)에 접속하여 ZIP으로 다운로드

![Full-width image](/assets/img/githubpage/003.png){:.lead width="800" height="100"}
ZIP으로 다운로드 받아 적용해도 되지만 Fork로 나의 Repository로 복사해와서 작업해도 좋습니다.

- 다운로드 받은 파일 압축해제

![Full-width image](/assets/img/githubpage/004.png){:.lead width="800" height="100"}

- Github Page Repository Clone

![Full-width image](/assets/img/githubpage/005.png){:.lead width="800" height="100"}

깃허브 페이지 레포지토리로 사용될 폴더에서 git clone 명령어를 사용해 Repository를 Clone합니다.   

> git clone RepositoryURL   
`ex)`   
git clone https://github.com/remind2dev/remind2dev.github.io.git

- 압축해제한 Hydejack-starter-kit 폴더의 **항목 전체**를 복사해 깃허브 레포지토리에 붙혀넣기

![Full-width image](/assets/img/githubpage/006.png){:.lead width="800" height="100"}

- Command 실행

키보드의 [Window키 + R]을 눌러 나타난 화면에 cmd 를 입력하고 확인을 눌러 Command 창을 실행시키고,   
깃허브 페이지 폴더로 이동해 아래 커맨드를 순서대로 실행합니다.

> `// bundler 설치`   
gem install bundler   
`// Hydejack bundle install`   
bundle install


위의 설치가 완료되고 `bundle exec jekyll serve` 명령어를 입력해 서버를 실행시키면,   
`http://localhost:4000` 또는 `http://127.0.0.1:4000` 에 접속하여 화면을 확인할 수 있습니다.

- 적용 내용 Git Push 하기

Git Bash 에서 아래 커맨드를 순서대로 입력해 Push를 진행합니다.

> git add .   
git commit –m “change theme hydejack“   
git push origin main

Push가 완료되고나면 오래걸려도 10분 이내에는 적용이 완료되어 `https://username.github.io`에 접속하여 반영 내용을 확인할 수 있습니다.

## 적용 오류 수정

아닌분들도 계시겠지만 저는 Hydejack 테마를 적용하면서 오류가 발생했습니다.

![Full-width image](/assets/img/githubpage/007.png){:.lead width="800" height="100"}

캡처화면과 같이 오류가 발생하여 Details를 눌러 확인해보니

![Full-width image](/assets/img/githubpage/008.png){:.lead width="800" height="100"}

github-pages 225 | Error: The jekyll-theme-hydejack theme could not be found
테마를 찾을 수 없다고 합니다.. 어떻게 해결해야 할까요 ?

**_config.yml** 파일을 수정해주면 해결할 수 있습니다.
_config.yml 파일을 열고 스크롤을 내리다보면 아래 코드 두줄을 발견할 수 있습니다.

~~~yml
theme: jekyll-theme-hydejack   
# remote_theme: hydecorp/hydejack@v9
~~~

해당 코드를 하래와같이 전부 주석 해제하고 Push하면 제대로 적용됩니다.

~~~yml
theme: jekyll-theme-hydejack   
remote_theme: hydecorp/hydejack@v9
~~~

적용....된다고 하던데 저는 오류가 없어지지 않았습니다ㅠㅠ......   
그래서 마구잡이로 바꿔보던 도중 아래와 같이 theme를 주석하고 적용시켜 보았더니

~~~yml
# theme: jekyll-theme-hydejack   
remote_theme: hydecorp/hydejack@v9
~~~

**짜쟌!!!!** 드디어... 드디어 적용되었습니다 ㅠㅠㅠ 이제 포스트를 작성할 수 있어요...

![Full-width image](/assets/img/githubpage/009.png){:.lead width="800" height="100"}

_config.yml의 theme를 주석하고나니 로컬에서 `bundle exec jekyll serve`를 실행하면 아래와 같이 경로에 파일이 존재하지 않는다며 `http://localhost:4000`에 접속해도 화면이 나타나지 않지만, `# theme: jekyll-theme-hydejack`의 주석을 해제하고 다시 실행하면 잘 나옵니다.

![Full-width image](/assets/img/githubpage/010.png){:.lead width="800" height="100"}

로컬에서 포스트를 작성하며 확인할때는 주석을 풀고, Github에 적용할때는 주석을 하고...   
살짝 번거롭긴 하지만 잘 적용되서 뿌듯하네요.

깃허브 페이지를 꾸미고 세팅하는 방법들도 추가적으로 올리도록 하겠습니다.
긴 글 읽어주셔서 감사합니다.


## 참고 사이트
- [juxgsiroo님의 블로그](https://velog.io/@juxgsiroo/github-page-pt2)
- [SuperMemi's Study](https://supermemi.tistory.com/146)
