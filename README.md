# _*Learn to Redux*_

Ship Identification Project를 넘겨받고 결코 작지 않은 이 소스들을 감당하면서 Global한 State 관리의 필요성을 뼈저리게 느끼게 되었다. 이전부터 Redux를 공부하자고 다짐했지만 미루고 미루면서 이제야 시작하게 되었다.

Redux를 정리해보자

<br>

## _Concept_

React에서 State 관리를 하다보면 한 Component 내에서 상태관리를 주로 하게 된다.

그러나 Redux를 사용하게 되면 Component 외부에서 State 관리를 하기 때문에

State를 Store에서 가져와 관리할 수 있게 된다.

상태에 변화가 필요하다면 Store에  Dispatch를 이용해 Action을 전달하게 되고, 

Action의 객체를 참조하여 변화를 일으킨다.

Store가 Action을 받게 되면 Reducer가 State를 어떻게 변화시킬지 결정한다.

Action을 처리하게 되면 새로운 State가 Store에 저장이 되고, Store를 참조하고 있는 컴포넌트에 변화된 State값을 즉시 전달한다. 

<br>

## _Action_

특정 State 값에 변화가 필요하다면 Action을 보내야 한다. 

이것은 객체 형식으로 작성되며, ```type``` 필드를 필수적으로 가지게 된다.

State 변화 시 이 객체를 참조하여 변화를 일으킨다.

아래는 Action 함수의 생성 예제이다.

<br>

addSubscriber
``` 
const addSubscriber = () => {
    return {
        type: ADD_SUBSCRIBER
    }
}
```

addViewCount
```
const addViewCount = () => {
    return {
        type: ADD_VIEWCOUNT
    }
}
```

<br>


## _Reducer_

Reducer는 State 값을 변화시키는 역할이 있고, 변화하는 로직이 들어있다.

Reducer는 두 가지의 파라미터를 전달받는다. ```(state, action)```

<br>

subscriberReducer

```
const subscriberReducer = (state = subscriberState, action) => {
    switch(action.type) {
        case ADD_SUBSCRIBER:
            return {
                ...state,
                subscribers: state.subscribers + 1
            }
        default: return state;
    }
}
```
viewReducer

```
const viewReducer = (state = viewState, action) => {
    switch(action.type) {
        case ADD_VIEWCOUNT:
            return {
                ...state,
                viewCount: state.viewCount + 1
            }
        default: return state
    }
}
```

```action.type```의 값에 따라 어떤 값을 handling 할 지 결정한다. 

Reducer는 현재의 State와 전달 받은 Action을 참고하여 새로운 state를 반환한다.

<br>

## _Store_

Store에는 모든 State값이 내장되어 있다.

<br>

## _Dispatch_

Action을 Store에 전달하게 하는 행위이다.

<br>

## _Subscribe_

Component에서 특정 State값이 필요하면 Store를 Subscribe한다.

즉, Store의 State값이 변경되면 특정 함수를 실행시킨다.


