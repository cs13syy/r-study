# R 마크다운 한글 파일 만들기
기존의 R 마크다운 파일에서 한글을 입력하고 word나 pdf로 knit하면 파일이 만들어지지 않거나 깨져서 출력된다. R 마크다운으로 한글 파일을 만들기 위해서는 몇 가지 설치가 필요하다. 아래 순서를 따라해보고 안 되는 경우 구글링을 통해 오류를 해결해나가면서 설치해보자.

## 1. TeX Live 설치
- (1) 다음의 링크를 클릭하여 TexLive 설치 페이지로 이동하자 syntax: [TeX Live](https://tug.org/texlive/acquire-netinstall.html)
- (2) 해당 페이지 넷째 줄에 "install-tl.zip"를 클릭하여 파일을 다운 받는다
- (3) 다운 받은 압축 파일을 풀어준다
- (4) "install-tl-advanced" 파일에 커서를 대고 오른쪽 버튼을 클릭하여 "관리자 권한으로 실행"으로 파일을 열어준다 
- (5) 검은색 cmd 창이 뜨면 대기하다가, 창이 뜨면 하단의 "Install TeX Live" 버튼을 클릭하여 설치를 시작한다
- (6) 설치를 시작하면 창이 하나 뜨는데, 설치 시간은 대략 1시간 정도(혹은 그 이상) 걸린다
- (7) 설치가 완료되면 하단에 "Finish"라는 버튼이 뜨는데, 해당 버튼을 클릭한다

### tips : 파일을 열 때, 가능한 "관리자 권한으로 실행"해야 오류가 나지 않는다

## 2. TeX Live 한글 적용
- (1) "TeX Live command-line"을 실행한다
다음의 문구를 순서대로 하나씩 입력하고 enter 버튼을 클릭한다 (입력->클릭->입력->클릭...)

tlmgr repository add http://ftp.ktug.org/KTUG/texlive/tlnet ktug
tlmgr pinning add ktug *
tlmgr install ktugbin
tlmgr install texworks-config 
tlmgr install nanumttf hcr-lvt
