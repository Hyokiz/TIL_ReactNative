# 컴포넌트를 작은 컴포넌트로 쪼개기

- React와 동일

# Goal Input 컴포넌트로 작업하기

- React와 같은 방식으로 props로 함수를 내리고 만들기

# Pressable 컴포넌트로 누르는 이벤트 처리하기

- 아이템을 터치할 수 있게 하려면 React Native에서 인식시켜줘야 함.
- 특정한 컴포넌트로 감싸줘야 함.
- Pressable

  - Touchable도 있으나, 옛날 버전에서 쓰였다.

- onPress에 추가하고 싶은 내용을 추가하면 된다.

# 아이템을 삭제할 수 있게 만들기 & ID 사용하기

- filter 사용

  - filter은 true만 반환

- 삭제할 수 있는 방법에는 두가지가 있다.

  1. addGoalHandler와 같은 방법

  - 함수를 정의하고
  - 함수를 수동으로 호출해서 매개변수를 전송한다.

  2. bind()메서드 사용

  - 기본적으로 나중에 실행할 함수를 미리 조정할 수 있게 함
  - 첫 인자 : 곧 실행될 함수의 this 키워드
  - 두번째 인자 : 호출될 함수에서 수신하는 첫 매개변수 -> props.id로 설정

# Android 물결 효과 추가하기 & iOS 대안

- Android

  - Pressable 안에서 android_ripple안에 color를 추가해주면 금방 만들 수 있음.
  - 물결을 View 안에 만들고 싶으면 View 안에 Pressable 넣기
  - 패딩을 Text에 넣으면 됨.

- iOS

  - iOS의 경우 Pressable 컴포넌트의 style 프로퍼티를 넣는다.
  ```js
  <Pressable 
    android_ripple={{ color: "#210644" }} 
    onPress={onDeleteHandler}
    style={({ pressed }) => pressed && styles.pressedItem}
  >
  ```
  - 이후에 밑에 styles에 원하는 css 적용.
  - 누를때마다 true 를 반환하기 때문에 가능.

# 모달 화면 추가하기

- 내장된 모달 컴포넌트 사용
- useState로 true, false값 만들고
- React처럼 {isvisible && } 이런식으로 하지 않음.
- Modal에 visible 프로퍼티가 포함되어 있으므로 그것으로 관리
- 또한 animationType가 기본 프로퍼티로 내장되어 있음

```js
<Modal visible={props.visible}animationType="slide">
```

# 모달 오버레이 스타일링하기

- Button을 커스텀 하지 않는 이상 Button의 스타일을 변경하기는 쉽지 않다.
- View를 div 처럼 사용하여 button을 감싼 후, view를 변경한다.

# 모달 열기 & 닫기

- App 의 컴포넌트 가시성 상태 변경
- setModalIsVisible로 false로 변경 후 props로 내려준다.

# 이미지로 작업하기 & 색상 변경하기

- React의 Img태그 처럼
- React Native는 Image 컴포넌트를 사용 가능하다.
- source={require()} 안에 경로를 넣어주고
- style로 style 또한 지정 가능

# 앱 최종 마무리

- 모든 화면을 같은 색으로 하고 싶으면
- app.json안에 "backgroundColor": "색상코드"로 추가.
- 어둡게 하면 상태표시줄이 보기 힘들어짐.
- 이때 App.js에 import StatusBar를 해준다.
- StautsBar 컴포넌트의 스타일을 light로 바꿔주면 잘보임

```js
<>
  <StatusBar
    style="light"
  />
  <여기서부터 코드 시작>
</>
```

# 모듈 요약

- 간단한 애플리케이션 구축