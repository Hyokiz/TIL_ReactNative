# 미니 게임 앱 구축하기

## 화면 컴포넌트 설정하기

- pages 대신 screens 폴더 생성

## 커스텀 버튼 생성하기

- View 안에 Text컴포넌트 넣으면 기능적으로는 작동하는 Button 완성.
- 공식 github에도 이렇게 만든다.

## Android & iOS 용 스타일링하기

- boxShadow가 React Native에는 없다.
- 추가하는 방법으로는 각각

  - Android

    - elevation 프로퍼티 추가
    - iOS에서는 elevation에 해당하는 개념이 없음

  - iOS

    - shadow로 시작하는 네 가지 프로퍼티 추가
    - shadowOffset: width, height 두 가지 필요
    - shadowRadius: 그림자가 얼마나 번지는지
    - shadowOpacity: 그림자 투명도

- 플랫폼에 따라 다르게 네이티브 컴포넌트로 컴파일된다.

## Number Input 요소 스타일링하기

- TextInput안에 maxLength 프로퍼티로 최대 글자 제한 가능.
- 중괄호 안에 숫자를 넣으면 된다.

## TextInput 필드 구성하기

- 키보드 제어하기
- 공식문서에 가보면 둘 다 지원하는 경우와 한 곳만 지원하는 경우가 있다.
- 숫자만 사용하기 위해서는 둘다 지원하는 number-pad로 지정해주면 된다.
- autoCapitalize: 자동으로 대문자로 입력되게 하는 것
- autoCorrect: 자동수정
- autoCapitalize, autoCorrect가 이메일 주소를 입력하는 입력란 필드에 설정되게 되면 UI가 안좋아짐.
- 숫자를 입력할 때는 필요없다.

## 버튼에 시각적 피드백 추가하기

- Touchable 컴포넌트

  - 이전에는 메인 컴포넌트였으나 지금은 사용하지 않음.

- Pressable 컴포넌트

  - 이걸로 사용한다.

- overflow: 컨테이너 내부에 일어나는 효과나 스타일링이 컨테이러를 넘어가는 부분은 잘라서 안보이게 한다.

- iOS 전용 스타일로 설정하기 위해서는 따로 전용 스타일을 설정해야 한다.

- pressable 컴포넌트의 경우 화살표 함수같은 함수를 가진다.

```js
<Pressable
  style={({ pressed }) => pressed ? [styles.pressed, styles.buttonInnerContainer] : styles.buttonInnerContainer}
>
  
</Pressable>
```
- 이런식으로 배열도 전달할 수 있다.

## 버튼 개선하기

- View로 공간을 나누어서 스타일링하기
- button의 밖에 View를 씌우고, flex:1로 모든 공간을 차지하도록 하기

## 컴포넌트 & 앱 전반에 색상 넣기

- App.js에 최상단에 View를 추가하고
- View 의 backgroundColor에 필요한 색상을 추가.
- View는 필요한 부분만 차지하는 것을 기억하고, flex:1 을 주면 전화면에 적용할 수 있다.

## 선형 그라데이션 추가하기

- expo install expo-linear-gradient 설치
- import LinearGradient
- 최상단의 View 대신 LinearGradient 로 변경
- 프로퍼티로 colors 프로퍼티 추가.
- 배열 안에 여러가지 색을 추가하면 됨.

## 배경 이미지 추가하기

- ImageBackground 내장 컴포넌트 사용
- ImageBackground 컴포넌트 또한 컴포넌트들의 조합이다.
- source: 이미지 가져오기
- resizeMode: 이미지를 가져왔을 때 이미지 사이즈 맞추기
- imageStyle: style을 지정해줄 수 있다.

## 게임 로직 시작하기

- 값의 유효성 검사

  - 일단 button의 재사용성을 위해서 onpress의 값을 props로 내려준 후 실행되게 한다.

## 사용자 입력 처리 & 경고 대화창 표시

- 사용자 입력을 제한하고 경고 대화창을 표시한다.
- 경고창 표시의 경우 내장 컴포넌트인 Alert를 사용한다.
- Alert의 인자로는 title, message, 경고창의 버튼 설정으로 가능하다.

  - 버튼 설정으로는 text, style, onPress를 사용

- 내장되어 있는 Native Alert API를 사용하는 것이다.

## 프로그램 내에서 화면 전환하기

- react에서 하던 식으로 삼항 연산자를 이용한다.
- 변수에 Component를 넣어두고
- number 가 정해지면 변수의 component를 바꿔준다.
- jsx 코드에는 {변수}로 작성하게 되면 바뀌게 된다.

## 게임 화면 작업 시작하기

- 기기의 모서리, 상단 화면에서 노치와의 간격을 설정할 때 유용한 컴포넌트

## SafeAreaView를 통해 기기 화면 제한 고려하기

- 실행중인 장치를 자동으로 감지하는 컴포넌트?

  - SafeAreaView

## 제목 컴포넌트 생성하기

