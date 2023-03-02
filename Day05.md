# 핵심 컴포넌트 & 컴포넌트 스타일링 살펴보기

## 핵심 컴포넌트

- Text, View 는 RN에서 가장 중요한 내장 컴포넌트.
- div, h2태그 등을 사용하지 못함.

## 컴포넌트 스타일링

1. 인라인 스타일링
2. StyleSheet Object로 작성

# 핵심 컴포넌트로 작업하기

- View는 중첩하여 작성할 수 있다.
- Button은 self-closing으로.
- Button의 title 프로퍼티 안에 title을 입력해야 함.

# React App 스타일링하기

- border은 존재하지 않음.
- borderWidth, borderColor 등으로 사용

# 레이아웃, Flex box 살펴보기

- TextInput 존재.
- 글자가 너무 위에 붙을 경우 -> padding으로 조절

# React Native & Flex box

## Flex box

- CSS 프로퍼티의 집합인 핵심 접근 방식이자 핵심 개념
- 외관을 조정하는데 사용
- RN에서 구현된 플렉스 박스는 RN 프로퍼티로 설정할 수 있음

  - CSS 플렉스 박스와 유사

- 결국 플렉스 박스는 몇 개의 스타일 프로퍼티로 컨테이너 내부에 요소를 배치하는 것
- 특정 요소가 차지하는 공간 제어 가능

# Flex box 집중탐구

- container에서 설정한 높이는 모든 요소에 적용된다.
- 플렉스박스에 있는 모든 View는 부모 요소의 높이를 취하지만, 너비는 옇향을 받지 않는다.
- 교차축을 따라 늘여서 배치된다.

  - 기본 설정은 stretch 로 되어있기 때문.

- 자식 컴포넌트에 flex 프로퍼티를 추가하고 flex: 1과 같이 설정

  - flex: 1으로 설정하면 모든 너비를 차지함.
  - 다른 자식에도 같이 추가하면 동일하게 배분된다.
  - flex: 1, flex: 2이면 2배 차지
  - flex: 3, flex: 2이면 5분의3, 5분의2씩 차지

# 레이아웃 개선하기

- 메인 컨테이너에서 전체 높이를 100%으로 설정하고 싶으면

  - height 프로퍼티를 사용하지 말고
  - flex: 1을 사용한다.

# 이벤트 처리하기

- 이벤트 리스너를 추가해서 이벤트 핸들러 함수에 연결하고 다른 React 앱과 마찬가지로 useState훅을 사용해 컴포넌트에서 상태 관리
- 차이점은 웹을 대상으로 하는 React 앱과 비교하면 RN은 ReactDOM 대신 다른 플랫폼 사용
- 하지만 이벤트 처리, 상태 관리 등은 React와 같은 방식으로 작동

1. 버튼 클릭
2. 입력한 값 

- TextInput의 onChangeText 프로퍼티 안에 괄호를 추가하면 코드를 파싱하고 평가하는 즉시 함수가 실행된다.
- Button 컴포넌트 내에서는 onClick 대신 onPress 를 사용.
- react 의 useState를 사용 가능하다.

# 강의 목표 리스트 관리하기

```js
function addGoalHandler() {
  setCourseGoals([...courseGoals, enteredGoalText]);
}
```
- 위의 방법처럼 spread 연산자를 사용한 방법: 새로운 상태가 이전 상태에 따라 달라지는 경우 상태를 업데이트 하는 최선의 방법이 아니다.

```js
const addGoalHandler = () => {
    setCourseGoals(currentCourseGoals => [...currentCourseGoals, enteredGoalText]);
  };
```
- 새 상태가 이전 상태에 의존한다면 업데이트 하는 더 좋은 방법은 상태 업데이트 함수에 함수를 전달하는 것.
- 새 상태를 얻도록 React에서 자동으로 호출하는 함수
- 인자는 React 내에서 자동으로 받아올 수 있음.

# IOS & Android 스타일링의 차이점

- borderRadius 를 설정하면 Android는 잘 적용되나 ios에서는 잘 적용되지 않음.
- 플랫폼마다 다르게 적용해야 할 필요가 있다.
- 모든 플랫폼에서 다 적용하게 만들기 위해서는 코드를 살짝 조정해야 한다.

  - IOS에 적용되지 않은 이유는 Text 컴포넌트에 직접 적용했기 때문이다.
  - React Native는 Text 컴포넌트를 해당하는 네이티브 위젯, 즉 네이티브 UI 요소로 전환하는데 Android 에서는 전환된 후 둥근 모서리로 나타나지만, iOS에서는 기본 네이티브 텍스트 출력 요소가 둥근 모서리를 지원하지 않음
  - Text 를 View 로 감싸서 해결할 수 있음.

- 웹용 CSS 와 달리 스타일은 연속적으로 적용되지 않음.

  - 독립적인 요소이기 때문.

# ScrollView를 통해 컨텐츠를 스크롤 할 수 있도록 만들기

- 브라우저와 비교했을 때

  - 브라우저는 기본적으로 스크롤바가 생긴다.
  - 하지만 React Native는 명시해줘야 한다.

- 사용하고자 하는 View를 ScrollView로 교체

  - View를 추가하여 View 안에 ScrollView가 들어가게 함.
  - property를 살펴보기

    - 튀어오르는 설정 가능
    - iOS 전용 프로퍼티, Android 전용 프로퍼티, 둘 다 사용 가능한 것도 있음

- 플랫폼에 따라 다른 부분이 있음

