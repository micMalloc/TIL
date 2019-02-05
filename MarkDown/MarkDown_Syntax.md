# MarkDown
:octocat: Github의 MarkDown 문법 공부

## 개요
* 제목강조
* 텍스트 기울림과 굵음체 (Italic 및 Bold)
* 취소선 효과
* 하이퍼링크 효과
* 인용구 효과
* 코드블럭
<br>

## 제목강조
### 사용밥법
```
html header 와 유사하며 #으로써 강조할 수 있다.
# 의 개수에 따라 크기가 달라진다.
# ~ # 제목 (반드시 마지막 # 띄고 텍스트를 넣어줘야한다.)

<예시>
# MarkDown
## MarkDown
### MarkDown
#### MarkDown
```
### 실행결과
# MarkDown
## MarkDown
### MarkDown
#### MarkDown
<br>

## 텍스트 기울림과 굵음체
텍스트 Italic 및 Bold 효과
### 사용밥법
```

텍스트 Italic : *텍스트*
텍스트  Bold  : **텍스트**
   동시적용    : **_텍스트_**
   
```
### 실행결과
* 텍스트 Italic : *텍스트* <br>
* 텍스트  Bold  : **텍스트** <br>
*    동시적용    : **_텍스트_**
<br>

## 취소선 효과
### 사용방법
```
~~텍스트~~ (텍스트와 ~ 사이에 여백이 있으면 안된다.)
```
### 실행결과
~~텍스트~~
<br>

## 하이퍼링크
### 사용방법
```
[텍스트](링크 URL)
<예시>
[micMalloc](https://github.com/micMalloc)
```
### 실행결과
[micMalloc](https://github.com/micMalloc)
<br>

## 인용구
### 사용방법
```
> 인용텍스트
```
### 실행결과
> 인용텍스트
<br>

## 블럭 사용
다양한 기호가 사용된 문장 사용시 용이하게 쓰인다.
### 사용방법
![사용방법이미지](https://github.com/denlyou/study_markdown_github/blob/master/images/text02.gif?raw=true)
```
문장 중간에서도 사용가능
<예시문장> 안녕하세요, 저는 `이희수` 입니다.
```
### 실행결과
```
#include<stdio.h>
int main(){
   printf("hello world");
}
```
### 프로그래밍 구문 강조
첫 번째 기호 옆에 c를 추가하여 프로그래밍 키워드 강조 효과

```c
#include<stdio.h>
int main(){
   printf("hello world");
}
```
<br>

## 이미지 활용
이미지 주소를 통한 활용과 깃헙 기본 제공 이미지 사용 방법

### 사용방법
```
<외부 이미지 사용>
![텍스트](이미지 주소/ 링크)

<기본 제공 이미지 사용>
:이미지이름:
``` 
기본 제공 이미지 참고 사이트
http://www.emoji-cheat-sheet.com/
<br>
