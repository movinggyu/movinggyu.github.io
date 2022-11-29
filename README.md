## 빌드과정

### 깃부터 시작
1. 깃허브에서 <githubid>.github.io 으로 퍼블릭 리포지토리 생성
2. `git clone <repository link>` 으로 퍼블릭 리포지토리 클론
3. `git branch -M main` 으로 현재 가지를 main으로 변경
4. `git status` 로 상태 확인하면서 일단 대기

### 지킬 설치
1. `sudo apt install ruby-full build-essential zlib1g-dev` 로 필요한 패키지 설치
2. 아래 코드로 Gem들을 설치할 때 권한오류를 피하기
```
mkdir .gems
export GEM_HOME="$HOME/.gems"
export PATH="$HOME/.gems/bin:$PATH"
```
3. `gem install jekyll bundler` 로 Jekyll과 Bundler 설치
4. 추가) `jekyill new . -f` 로 기본 Jekyll blog 만들 수 있대요!

### 테마 설치
1. 원하는 테마 설치 후 압축파일을 클론한 깃에 붙여넣기 겹치는것은 덮어씌우기
2. 테마에 필요한 패키지를 `bundle install`을 통해 설치
3. `jekyll serve`를 통해 지킬 블로그 실행
4. 여기서 나는 Lanyon 테마를 사용함.
5. _config.yml에서 기본적으로 작성된 부분을 내 필요에 맞게 수정

### 댓글 추가
1. [Disqus사이트](https://disqus.com)에 접속해 가입
2. 가입 과정중 사이트 정보 입력할 때 Website Name 기억
3. Jekyll Platform 선택, Website URL에 깃블로그 주소 입력
4. _config.yml에 아래 코드 입력
```
comment:
  provider: "disqus"
  disqus:
    shortname: "<기억해둔 Website Name 입력>"
```
5. _layouts/post.html에 아래 코드 입력
```
{% if page.comments %}
<div id="disqus_thread"></div>
<script>
    /**
     *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT 
     *  THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR 
     *  PLATFORM OR CMS.
     *  
     *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: 
     *  https://disqus.com/admin/universalcode/#configuration-variables
     */
    let PAGE_URL = "{{site.url}}{{page.url}}"
    let PAGE_IDENTIFIER = "{{page.url}}"
    var disqus_config = function () {
        // Replace PAGE_URL with your page's canonical URL variable
        this.page.url = PAGE_URL;  
        
        // Replace PAGE_IDENTIFIER with your page's unique identifier variable
        this.page.identifier = PAGE_IDENTIFIER; 
    };
    
    (function() {  // REQUIRED CONFIGURATION VARIABLE: EDIT THE SHORTNAME BELOW
        var d = document, s = d.createElement('script');
        
        // IMPORTANT: Replace EXAMPLE with your forum shortname!
        s.src = 'https://lee-super.disqus.com/embed.js'; // 이부분에 Website Name 입력해야함!
        
        s.setAttribute('data-timestamp', +new Date());
        (d.head || d.body).appendChild(s);
    })();
</script>
<noscript>
    Please enable JavaScript to view the 
    <a href="https://disqus.com/?ref_noscript" rel="nofollow">
        comments powered by Disqus.
    </a>
</noscript>
{% endif %}
```
6. 포스트 작성할때 comments: True 지정해줌

### 파비콘 설정
1. `/assets`폴더 내에 `favicon.ico`파일을 넣어줌
2. `_includes`폴더 내에 `head.html`의 위쪽에 아래 코드 삽입
`<link rel="icon" type="image/png" href="/assets/favicon.ico">`

### 구글애널리틱스
요 내용은 블로그 내에 포스팅으로 작성함.

