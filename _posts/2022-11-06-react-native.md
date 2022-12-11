---
title: React-Native와 Expo를 이용하여 프로젝트 생성 및 실행
layout: post
post-image: "https://cdn.inflearn.com/public/course-325874-cover/f38ca683-df16-488c-8114-9259c7919265"
description: React-Native와 Expo를 이용해 인생네컷을 찍을 수 있는 프로젝트를 개발하는 과정을 정리하였다.
tags:
- react-native
- expo
--- 


# 개발환경
1. VS Code
2. React-Native
3. Expo


# 1. Expo Cli를 이용한 프로젝트 생성
cmd창(윈도우+R -> cmd)을 열고 난 후 프로젝트를 생성하고자 하는 위치로 이동한 후 아래의 코드를 순차적으로 작성하여 프로젝트를 생성한다.

```cmd
npm insall -g expo cli	//expo cli 설치

npm init testProject	//해당 위치에 프로젝트(testProject) 생성
```
testProject 대신에 만들고자 하는 프로젝트 이름을 입력하면 된다.
그러면 프로젝트가 생성된 것을 확인할 수 있다.

![](https://velog.velcdn.com/images/2020108249/post/2ebd397e-4377-4a4a-9012-ef3b34558bae/image.png)
위와 같은 에러가 발생한 경우 아래의 코드로 프로젝트를 생성하면 된다.
```cmd
expo init testProject

//위의 코드가 되지 않는 경우(local CLI에서는 지원되지 않는다는 에러가 뜬다)
npx create-expo-app [프로젝트명]
```

# 2. 프로젝트 실행
### 프로젝트 실행
```cmd
npm start	//프로젝트 실행
```
### Expo Go 설치 및 QR코드를 이용한 실행
위의 명령어를 cmd 창에서나 VSCode의 cmd 창에서 작성하면 QR코드가 생성된다. IOS인 경우에는 해당 QR코드를 카메라로 찍어 확인하고, Android인 경우에는 'Expo Go'라는 어플을 실행하여 로그인을 한 후 QR코드를 찍으면 확인이 가능하다. 물론 IOS인 경우에도 'Expo Go'라는 어플을 다운받고 로그인을 수행하여야 한다.

### QR코드 이용시 Error 해결
해당 코드로 실행하였을 때 파란화면이 뜨면서 "Something went wrong"이라는 오류가 발생하였다.<br> 이를 해결하기 위해 많은 시도를 해보았지만 다음과 같은 코드로 실행함으로써 오류를 해결할 수 있었다.
```cmd
expo start --tunnel
```
### 웹에서 프로젝트 실행
위의 방식은 스마트폰에서 확인을 하기 위해 사용하는 방식이다.
웹에서 프로젝트를 실행하기 위해서는 새로운 패키지를 설치해주어야한다.
```cmd
npx expo install react-native@0.69.6

npx expo install react-native-web@~0.18.7 react-dom@18.0.0 @expo/webpack-config@^0.17.0
```
위의 두 코드를 입력하여 패키지를 설치한 후 아래의 화면이 나온 상태에서 "w"를 누르면 웹에서 프로젝트가 실행이 된다. <br>
![](https://velog.velcdn.com/images/2020108249/post/ed8a1a14-4473-4bae-b2ac-05f8387c5a7f/image.png)
# 3. 코드 수정하여 프로젝트 구현
VS Code에 들어가서 생성한 프로젝트를 열면 'App.js' 파일이 보이는데 이게 가장 처음에 나오는 화면이다. 이 화면을 시작으로 본인이 원하는 화면들을 구성할 수 있다.<br>
구성하는 방법들을 찾아보기 위해서는 React-Native를 이용하면 쉽게 할 수 있다. 관련 내용들이 잘 정리되어 있는 링크를 아래에 첨부하였으니 참고하면 좋을 것 같다.<br>
<https://jeffgukang.github.io/react-native-tutorial/docs/basic-tutorial/basic-features(todolist)/01-getting-started/getting-started-kr.html>
