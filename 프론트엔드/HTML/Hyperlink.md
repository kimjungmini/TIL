https://poiemaweb.com/html5-tag-link를 공부하고 정리한 문서 입니다.

# 하이퍼 링크

기존 문서나 텍스트의 선형성, 고정성의 제약에서 벗어나사용자가 원하는 순서대로 원하는 정보를 취득 할 수 있는 기능 즉 한 텍스트에서 다른 텍스트로 건너뛰어 읽을 수 있는 기능을 **하이퍼 링크**라 한다.

HTML link는hyperlink를 의미하며 a tag가 그 역할을 담당한다

```html
<a href="http://www.google.com">Visit google.com</a>
```

## href 속성

---

href 속성은 이동하고자 하는 파일의 위치(경로)를 값으로 받는다. 경로란 파일 시스템 상에서 특정 파일의 위치를 의마한다.

### Directory

디렉토리는 파일과 다른 디렉토리를 갖는 파일시스템 내의 존재물로서 폴더라고 불린다.

**루트 디렉토리**: 파일 시스템 계층 구조 상 최상위 디렉토리

**홈 디렉토리**: 시스템 사용자에게 각각 할당된 개별 디렉토리

**작업 디렉토리**: 작업 중인 파일이 위치한 디렉토리

**부모 디렉토리**: 작업 디렉토리의 부모 디렉토리

### 파일 경로

---

#### **절대경로**

현재 작업 디렉토리와 관계 없이 특정 파일의 절대적인 위치를 가리킨다. 루트 디렉토리를 기준으로 파일위치를 나타낸다

- http://www.mysite.com/index.html
- /Users/kimjungmin/Desktop/myfile.txt
- C:\users\kimjungmin\Desktop/myfile.txt
- /index.html

#### **상대경로**

현재 작업 디렉토리를 기준으로 특정 파일의 상대적인 위치를 가르킨다.

- ./index.html
- ../dist/index.js
- ../../dist/index.js
- index.html
- html/index.html

href 속성에 사용가능한 값은 다음과 같다.

| Value               | Description                                              |
| ------------------- | -------------------------------------------------------- |
| 절대 URL            | 웹사이트 URL                                             |
| 상대 URL            | 자신의 위치를 기준으로한 대상의 URL                      |
| fragment identifier | 페이지 내부에 특정 id를 가지는 요소에 링크 (href='#top') |
| 메일                | mailto:                                                  |
| script              | href="javascript:alert('hello')"                         |

```html
<!DOCTYPE html>
<html>
  <body>
    <a href="http://www.google.com">URL</a><br />
    <a href="html/my.html">Local File</a><br />
    <a href="file/my.pdf" download>Download file</a><br />
    <a href="#">fragment identifier</a><br />
    <a href="http://www.google.com">URL</a><br />
    <a href="mailto:aphopis@naver.com?Subject=Hello again">Send Mail</a><br />
    <a href="javascript:alert('Hello');">Javascript</a>
  </body>
</html>
```

## target 속성

target 속성은 링크를 클릭했을 때 윈도우를 어떻게 오픈할 지를 지정한다.

| Value   | Description                                                    |
| ------- | -------------------------------------------------------------- |
| \_self  | 링크를 클릭했을 때 문서를 현재 윈도우에서 오픈한다(default)    |
| \_blank | 링크를 클릭했을 때 연결문서를 새로운 윈도우나 탭에서 오픈한다. |

```html
<!DOCTYPE html>
<html>
  <body>
    <a href="http://www.google.com" target="_blank">URL</a><br />
  </body>
</html>
```
