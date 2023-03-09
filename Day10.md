# 호환 가능한 사용자 인터페이스 구축하기

- 기기에 따라서 화면이 다를 수 있다.
- 이것을 호환이 되게 하면 좋을 것 같다.

## 동적 너비 설정하기

- maxWidth 설정해주기
- 일반 너비, 최대 너비 설정해주면 동적으로 설정가능

## Dimensions API

- 작게 만들 수 있음
- JavaScript 객체로써 styles를 포함한 곳에서 정보 추출을 위해 사용할 수 있다.

- 기기의 너비와 높이를 추출할 수 있음.

```js
const deviceWidth = Dimensions.get("window").width;
```

- get으로 가져올 수 있다.

## Dimensions API 를 통해 이미지 크기 조정하기

- 똑같이 Dimensions를 통해 width 를 가져온 후 조건을 달아주면 된다.

## 화면 방향에 관한 문제 이해하기

- app.json 에 방향(orientation)이 세로(portrait)로 잠겨 있기 때문.
- 방향을 고정하지 않으려면 세로(portrait) 대신 기본값(default)으로 설정해주면 된다.

## 화면 방향에 따라 크기를 동적으로 설정하기

- Dimension API 사용
- 시작할 때 한번만 실행 되기 때문에, 컴포넌트 함수 외부의 코드는 재실행 되지 않음.
- 사용중 방향 전환을 가능하게 하고싶다면 Dimensions API를 사용하지 않아야 함.
- 반응형 코드를 작성하도록 해야 함

  - 컴포넌트 안에 있으면 실행될 때마다 바뀌기 때문에 가능

- useWindowDimensions

  - dimensions를 가져와서 동적으로 변경할 수 있다.

## KeyboardAvoidingView를 통해 화면 컨텐츠 관리하기

- KeyboardAvoidingView는 입력란을 포함하는 다른 콘텐츠를 감싸는데 사용하는 컴포넌트
- 키보드가 열릴 때마다 입력 요소 및 다른 요소가 화면 위로 올라가 키보드가 열려도 액세스 할 수 있음
- 감싸줄 경우 화면이 보이지 않음 -> 화면 범위를 flex:1로 늘려줘야 함
- behavior 프로퍼티를 이용하여 동작할 수 있도록 해야함.
- behavior="position"을 해줘도 안됨 -> ScrollView로 감싸줘야 함
- 동적 리스트가 없기 때문에 FlatList가 아닌 ScrollView로 감싸기

## 가로 모드 UI 개선하기

- 가로 모드로 게임을 진행할 경우 안드로이드에서 작동하지 않음.
- 너비는 넓지만 높이는 낮을 때 설정
- 변수에 jsx 코드를 할당하고
- 변수에 조건을 걸어서 ui를 다르게 해준다.

## useWindowDimensions를 이용한 추가 개선

- gameover 화면에 useWindow