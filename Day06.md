# FlatList를 통해 리스트 최적화하기

- ScrollView 는 모든 자식 항목들을 렌더링
- 보이지 않는 것 까지 렌더링 하기 때문에 성능에 문제가 생길 수도 있음.
- ScrollView -> FlatList로 대체

## FlatList

- FlatList는 수동으로 데이터를 매핑하지 않아도 됨.
- 필수 프로퍼티

  - data

    - 목록에서 출력할 데이터를 지정하는 역할
    - map 대신 사용
    - 셀프 클로징 컴포넌트로 바꿔야 함.

  - renderItem

    - 자동으로 개별 함수를 매개변수로 받음
    - 함수를 호출할때마다 함수 전달
    - 새 항목을 렌더링 할 때 함수를 매번 호출(스크롤 시)
    ```jsx
    <FlatList
      data={courseGoals}
      renderItem={(itemData) => {
        // itemData.index 제공
        return (
          <View key={goal} style={styles.goalItem}>
            <Text style={styles.goalText}>{itemData.item}</Text>
          </View>
        )
      }}
    >
    ```
    - 이런 식으로 변경
    - item프로퍼티가 실제 데이터 항목을 하나씩 가짐

- 키를 추가하는 두 가지 방법

  1. 데이터의 값을 문자열 같은 원시 값에서 key 프로퍼티를 포함하는 객체로 변경 

  ```js
  function addGoalHandler() {
    setCourseGoals((currentCourseGoals) => {
      ...currentCourseGoals,
      { text: enteredGoalText, key: Math.random().toString() },
    })
  }
  ```

  2. ..

  - key 프로퍼티가 없는 경우

    - API에서 가져오거나
    - 변경하고 싶지 않을 경우

  - 입력 데이터에 key 프로퍼티 설정
  - FlatList 컴포넌트에 새 프로퍼티를 추가해준다.

    ```jsx
    <FlatList
      data={courseGoals}
      renderItem={(itemData) => {
        // itemData.index 제공
        return (
          <View key={goal} style={styles.goalItem}>
            <Text style={styles.goalText}>{itemData.item}</Text>
          </View>
        )
      }}
      keyExtractor={(item, index) => {
        return item.id
      }}
    >
    ```
  - keyExtractor는 함수를 값으로 취한다.

    - 인라인 화살표 함수를 넣을 수 있다.
    - item, index를 자동으로 수신
    - 모든 항목에서 키를 가져오려고 호출하는 함수
