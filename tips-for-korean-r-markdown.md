# R 마크다운 한글 파일 만들기
기존의 R 마크다운 파일에서 한글을 입력하고 word나 pdf로 knit하면 파일이 만들어지지 않거나 깨져서 출력된다. R 마크다운으로 한글 파일을 만들기 위해서는 몇 가지 설치가 필요하다. 아래 순서를 따라해보고 안 되는 경우 구글링을 통해 오류를 해결해나가면서 설치해보자.
***
## 1. TeX Live 설치
- (1) 다음의 링크를 클릭하여 TexLive 설치 페이지로 이동하자 [TeX Live](https://tug.org/texlive/acquire-netinstall.html)
- (2) 해당 페이지 넷째 줄에 "install-tl.zip"를 클릭하여 파일을 다운 받는다
- (3) 다운 받은 압축 파일을 풀어준다
- (4) "install-tl-advanced" 파일에 커서를 대고 오른쪽 버튼을 클릭하여 "관리자 권한으로 실행"으로 파일을 열어준다 
- (5) 검은색 cmd 창이 뜨면 대기하다가, 창이 뜨면 하단의 "Install TeX Live" 버튼을 클릭하여 설치를 시작한다
- (6) 설치를 시작하면 창이 하나 뜨는데, 설치 시간은 대략 1시간 정도(혹은 그 이상) 걸린다
- (7) 설치가 완료되면 하단에 "Finish"라는 버튼이 뜨는데, 해당 버튼을 클릭한다

### * tips : 파일을 열 때, 가능한 "관리자 권한으로 실행"해야 오류가 나지 않는다
***
## 2. TeX Live 한글 적용
- (1) "TeX Live command-line"을 실행한다
- (2) 다음의 문구를 순서대로 하나씩 입력하고 enter 버튼을 클릭한다 (입력->클릭->입력->클릭...)
tlmgr repository add http://ftp.ktug.org/KTUG/texlive/tlnet ktug
tlmgr pinning add ktug *
tlmgr install ktugbin
tlmgr install texworks-config 
tlmgr install nanumttf hcr-lvt
- (3) "TeXworks editor"를 실행하고, 실행 창 초록 버튼 옆 항목을 "XeLaTex"로 선택한다
- (4) 입력창에 다음과 같이 입력하고, 초록 버튼을 클릭한다
* 오타가 있을 시 "Undefined control sequence"라고 오류 메시지가 뜨니 정확히 입력하자
\documentclass{article}
\usepackage{kotex}
\begin{document}
Hello World 안녕하세요
\end{document}
- (5) 이상이 없으면 pdf 파일로 변환되어 한글이 출력되는 것을 확인할 수 있다
***
## 3. r markdown 실행
- (1) r studio를 실행한다
- (2) 상단의 File -> New File -> R Markdown을 클릭한다
- (3) Title과 Author를 입력하고 OK 버튼을 클릭한다
- (4) 5번째 줄 output 항목에 다음과 같이 입력한다
output:
  pdf_document :
	  latex_engine : xelatex
  html_notebook : default
  html_document : default
mainfont : NanumGothic
- (5) 입력창에 한글 문구를 입력한다 (아무 문구나 상관없다)
- (6) Knit 옆 ▼ 표시를 클릭, Knit to PDF를 선택한다
- (7) 이상이 없으면 한글이 출력된 PDF를 저장, 확인할 수 있다
***
