# React Native 내부 살펴보기

## React + React Native App

```js
const App = props => {
  return (
    <View>
      <Text>Hello there!</Text>
    </View>
  )
}
```
- View와 Text는 RN의 특별한 컴포넌트로 RN가 컴파일 함.
- 사용한 JSX 요소는 각 플랫폼의 네이티브 요소로 컴파일됨

## What about the logic?

- UI 요소와 다르게 로직은 컴파일 되지 않음.
- 구축한 네이티브 앱 안에서 RN이 호스트한 대로 JS 스레드에서 실행
- 즉, RN은 간단한 JS 프로세스를 구축하고 있는 네이티브 앱의 일부로 만들어 자동으로 이 프로세스를 관리해 네이티브 플랫폼과 상호작용 할 수 있도록 함
- 따라서 JS 코드는 네이티브 앱 안에서 그대로 실행하면서 네이티브 앱의 RN을 통해 Android나 IOS 플랫폼과 상호작용

